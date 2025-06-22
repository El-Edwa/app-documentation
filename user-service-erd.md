# User Service ERD

## Entity Relationship Diagram for User Service

This diagram shows the database schema for the User Service, which handles user management, authentication, and profiles.

```mermaid
erDiagram
    Users {
        UUID user_id PK
        VARCHAR email UK "UNIQUE, NOT NULL"
        VARCHAR username UK "UNIQUE, NOT NULL, 15 chars max"
        VARCHAR password_hash "NULL for OAuth users"
        TIMESTAMP created_at
        TIMESTAMP updated_at
        BOOLEAN email_verified "DEFAULT FALSE"
        ENUM account_type "public, private"
        BOOLEAN is_verified "DEFAULT FALSE"
        ENUM status "active, suspended, deleted"
    }

    User_Profiles {
        UUID profile_id PK
        UUID user_id FK
        VARCHAR display_name "50 chars max"
        VARCHAR bio "160 chars max"
        VARCHAR location "100 chars max"
        DATE birth_date
        VARCHAR profile_picture_url "255 chars max"
        VARCHAR banner_image_url "255 chars max"
        VARCHAR website_url "255 chars max"
        TIMESTAMP created_at
        TIMESTAMP updated_at
    }

    OAuth_Providers {
        UUID oauth_id PK
        UUID user_id FK
        ENUM provider "google, github"
        VARCHAR provider_user_id "255 chars max"
        TEXT access_token
        TEXT refresh_token
        TIMESTAMP created_at
        TIMESTAMP updated_at
    }


    Users ||--|| User_Profiles : "has"
    Users ||--o{ OAuth_Providers : "can have multiple"
```

## Table Descriptions

### Users

Core user account information including authentication credentials and account settings.

### User_Profiles

Extended profile information that users can customize, including bio, images, and personal details.

### OAuth_Providers

Stores OAuth authentication tokens and provider-specific user IDs for third-party login integration.

## Key Relationships

- Each User has exactly one Profile (one-to-one)
- Each User can have multiple OAuth Providers (one-to-many)