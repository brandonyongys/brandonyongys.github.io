---
layout: post
title: Setting Up Lambda Access to Amazon OpenSearch in a Private Subnet
# description: It's Also About Travel (and the Downtime in Between)
date: 2025-05-03
tags: [growth, technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: false

---

I just got back from a long holiday, and as expected, getting back into the groove wasn't easy - my brain was in full vacation mode! Thankfully, I had documented my progress well enough to pick things up quickly.

I'm currently working on building a Retrieval-Augmented Generation (RAG) pipeline, and one key component is a vector database to store all the embeddings. I chose to use Amazon OpenSearch Service, assuming that simply creating a domain in a private subnet would be sufficient. Spoiler alert: it wasn't.

When I tried accessing the OpenSearch domain from my Lambda function, the request failed due to authorization issues. After some digging, I found out I needed to explicitly grant permissions to my Lambda's IAM role. Here's a breakdown of what I did.

# Accessing the OpenSearch Dashboard

Since the domain is hosted in a private subnet, I couldn't access the OpenSearch dashboard directly from my local machine. Fortunately, I had previously set up a bastion EC2 instance for connecting to my RDS database in the same VPC.

Step 1: SSH into the EC2 instance
```
ssh -i your-key.pem ubuntu@<EC2-Public-IP>
```

Step 2: Test connection to OpenSearch
```
curl -k https://vpc-xxx-xxx.es.region.amazonaws.com
```

You should get a response similar to:
```
{
  "name" : "random_alphanumeric",
  "cluster_name" : "accountID:domain_name",
  "cluster_uuid" : "random_alphanumeric",
  "version" : { ... },
  "tagline" : "The OpenSearch Project: https://opensearch.org/"
}
```

Step 3: Port forward the dashboard

Run the following command on your local terminal:
```
ssh -i your-key.pem -L 5601:vpc-xxx-xxx.es.region.amazonaws.com:443 ubuntu@<EC2-Public-IP>
```

Then open your browser and navigate to:
```
https://localhost:5601/_dashboards
```

You should now see the OpenSearch Dashboard login screen.


# Authorizing the Lambda Function

Log in with the admin credentials you set when creating the OpenSearch domain.
1. Navigate to Security > Roles.
1. Create a new role and assign it the necessary permissions.
1. Under Mapped users, add your Lambda function's IAM role ARN as a backend role.

# Verifying Access from Lambda

Here's the Python snippet I used to test the connection:
```
try:
    result = opensearch_client.ping()
    ping_output = {"ping": result}
except Exception as e:
    logger.exception("Ping failed")
    ping_output = {"error": str(e)}

print(f"ping output: {ping_output}")
```

If everything is configured correctly, you should see:
```
ping output: {'ping': True}
```

<hr>
And that's it! Now my Lambda function can securely connect to Amazon OpenSearch within a private subnet. Hopefully this helps someone avoid the same confusion I had!

