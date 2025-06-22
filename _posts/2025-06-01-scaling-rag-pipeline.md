---
layout: post
title: Lessons from Scaling a Naive RAG Pipeline..
description: ...I'm sure there are more to come
date: 2025-06-01
tags: [growth, technical, programming, project, AWS]

# display_tags: ['life', 'career', 'technical', 'programming', 'project', 'AWS', 'growth']


comments: true
published: false

---

In my spare time, I've been building a simple [RAG (Retrieval-Augmented Generation) pipeline](https://brandonyongys.github.io/blog/2025/naive-rag-pipeline/) - and I finally got a functional chatbot running! At first, it seemed promising. It handled queries about a specific credit card fairly well (though, admittedly, I only used one document in the initial test). I felt like I had achieved something significant and thought I was ready to scale this for production.

So I pushed it further by bulk-loading more documents into the pipeline.

Oh boy, was I wrong about being production-ready.

<hr>

### Issue #1: Bedrock API Throttling & Timeouts
The first problem arose when I started calling Bedrock to perform tasks like summarizing chunks of text and generating embedding vectors from the summaries. I had already accounted for API throttling and built in retry logic - but I didn't expect almost all of my requests to get throttled repeatedly.

This caused my AWS Lambda functions to timeout, which meant chunks weren't getting summarized or embedded properly.

To address this, I implemented a FIFO queue with Amazon SQS. This setup allowed me to control the number of concurrent Lambda consumers calling Bedrock. Now, when a message (i.e., a file) isn't fully processed - read, chunked, summarized, embedded, and indexed in OpenSearch - it goes back into the queue for reprocessing. This flow control drastically improved reliability and allowed me to bulk-upload documents without needing to manually manage availability or retry logic.

<hr>

### Issue #2: Poor Retrieval & Reranking Results
The second major issue came during retrieval and reranking. Many of my queries received responses like:
```
I apologize, but I don't have specific information about [X]. The provided context does not contain details about [X].
```

This was incredibly frustrating. I had assumed the LLM was "smart enough" to generate responses based on the context - but the issue wasn't with the model's generation. It was with retrieval.

Since my test queries were about a specific credit card, most relevant chunks were indeed being retrieved. However, my implementation was naive: I embedded and indexed the chunks without any metadata.

#### Optimization Opportunities
1. Metadata: By including metadata (e.g., card name, category), I could restrict retrieval to more relevant subsets of the index rather than searching the entire vector space.

1. Smarter Chunking: Instead of naively splitting by token count, I could chunk by semantically related sections. This would make summaries more coherent and embeddings more meaningful, improving kNN search accuracy.

<hr>

These are just some of the growing pains I've encountered scaling this from a toy project into something more robust - all while working full-time. Still lots to fix and learn, but I'm confident the effort will pay off.






