# Tweet Service ERD - MongoDB Schema

## Document Schema for Tweet Service

This diagram shows the MongoDB document structure for the Tweet Service, which handles tweet creation, management, media attachments, and threading.

```mermaid
`erDiagram
    Tweets {
        ObjectId _id PK
        UUID user_id "External Reference"
        String content "280 chars max"
        Date created_at
        Date updated_at
        UUID reply_to_tweet_id "nullable"
        UUID thread_id "nullable"
        String reply_settings "everyone|followers|mentioned"
        Boolean is_pinned "default false"
        Array media "embedded media objects"
        Object metadata "hashtags, mentions, counts"
    }

    Tweet_Threads {
        ObjectId _id PK
        UUID creator_user_id "External Reference"
        Date created_at
        Array tweet_ids "array of tweet ObjectIds"
    }

    Scheduled_Tweets {
        ObjectId _id PK
        Date scheduled_for
        String status "pending|published|failed"
        Object tweet_data "embedded tweet content"
    }

    Tweet_Drafts {
        ObjectId _id PK
        UUID user_id "External Reference"
        String content
        Array media_urls
        Date created_at
        Date updated_at
    }

    Tweets ||--o{ Tweet_Threads : "belongs to thread"
    Tweets ||--o| Scheduled_Tweets : "can be scheduled"
    Tweets ||--o{ Tweets : "can reply to"`
```

## Collections Explained

### Tweets

Stores individual tweets with embedded media and metadata. Each tweet is a complete document containing all its data.

### Tweet_Threads

Groups related tweets together in conversation threads. Contains an array of tweet IDs that belong to the thread.

### Scheduled_Tweets

Manages tweets scheduled for future publication. Stores the complete tweet data until it's published.

### Tweet_Drafts

Stores unpublished draft tweets that users can save and edit before publishing.
