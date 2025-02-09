---
layout: post
title: Connecting My Telegram Bot to an RAG Pipeline on AWS
description: Just the initial setup
date: 2025-02-07
tags: [technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']

comments: true
published: true

---
Lately, it feels like "RAG" is everywhere. It’s not a new concept, but it keeps popping up. At its core, Retrieval-Augmented Generation (RAG) is pretty straightforward:
1. Convert a data source into vector embeddings.
1. Store the embeddings in a vector database.
1. Convert a query into a vector embedding.
1. Retrieve the k most similar embeddings.
1. Feed these retrieved texts, along with the original query and role instructions, to an LLM to generate a natural language response.

In my existing [Telegram bot](https://brandonyongys.github.io/blog/2025/telegram-chatbot/), it currently just responds with a simple message whenever a user sends something. Now, I want to enhance it by integrating an RAG pipeline, allowing users to ask questions and receive relevant responses based on stored knowledge. This post will focus on setting up the basic implementation.

# Choosing AWS Services for RAG
To implement RAG on AWS, I need two additional resources:
1. Amazon Kendra (or another vector database like OpenSearch Service)
1. Amazon Bedrock (or an LLM provider like OpenAI)

Why these services? Simply put, I don't want to manage infrastructure. Let AWS handle that for me.

Now, let’s dive into setting up Amazon Kendra and Bedrock!

# Setting up Amazon Kendra
1. Create a new index in the Amazon Kendra console.
1. Wait for the index to be fully set up (this takes some time).
1. Add an S3 bucket as a data source using the following CLI command:
    ~~~
    --index-id <your-kendra-index-id> \
    --name "data-source-name" \
    --type S3 \
    --configuration '{
        "S3Configuration": {
            "BucketName": "your-S3-bucket-name",
            "InclusionPrefixes": ["folder-name/"]
        }
    }' \
    --role-arn "arn:aws:iam::<your-aws-account-id>:role/service-role/your-service-role" \
    --region <your-kendra-region> \
    --profile <your-aws-account>
    ~~~
    - I initially tried setting this up via the console but ran into issues when specifying the S3 bucket.
    - I had to manually update the IAM role permissions and modify the S3 bucket policy to allow Kendra access.
    - Even after that, syncing failed because Kendra couldn't delete old documents from a previous S3 bucket.
    - Switching to the command line method solved these issues!
1. Sync the data source and ensure it's successfully indexed.
1. Test the index by running queries to verify it returns expected results.
1. Connect Kendra to AWS Lambda using the following function:
    ~~~
    def search_documents_kendra(query, kendra_index_id, pagesize = 5):
        """
        Function:   Given the query, search for relevant piece of text
        """
        response = kendra_client.query(
            IndexId=kendra_index_id,
            QueryText=query,
            PageSize=pagesize
        )

        retrieved_texts = [item["DocumentExcerpt"]["Text"] for item in response["ResultItems"]]
        return retrieved_texts
    ~~~

# Setting up Amazon Bedrock
Amazon Bedrock is much easier to set up compared to Kendra.

1. Get access to a preferred LLM model on Amazon Bedrock.
1. Integrate it into AWS Lambda using the following function:
    ~~~
    def generate_response_with_bedrock(query, retrieved_texts, bedrock_model_id = BEDROCK_MODEL_ID,
                                    max_tokens = 300):
        context = "\n".join(retrieved_texts)
        prompt = f"Context: {context}\n\nUser Query: {query}\n\nAnswer:"

        # Different model has different params. 
        payload = {
                "prompt": prompt,
                "max_tokens": max_tokens
            }

        response = bedrock_client.invoke_model(
            modelId=bedrock_model_id,  # Example: Claude 3 model
            contentType="application/json",
            accept="application/json",
            body=json.dumps(payload)
        )
        
        response_body = json.loads(response["body"].read())
        return response_body["completion"]
    ~~~
    1. Refer to [this guide](https://docs.aws.amazon.com/bedrock/latest/userguide/models-supported.html) for available model IDs.
    2. Check [this documentation](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters.html) for supported model parameters.

# Wrapping up
With that, I now have a basic RAG pipeline connected to my Telegram bot! While this setup isn't optimized yet, it's a solid starting point.

One issue I noticed is that the LLM sometimes pulls information from external sources instead of my documents. The next step will be fine-tuning the setup to ensure the responses are strictly based on my indexed data.

Stay tuned for the next update! 🚀
