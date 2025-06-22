# Microservices Overview - Domain & Responsibilities

## 1. User Service

**Domain**: User management, authentication, and profiles

**Responsibilities**:

- User registration and authentication
- Profile management (bio, avatar, banner) - _integrates with Cloudinary_
- Account settings and privacy controls
- Password management and OAuth integration
- Email verification and password reset

## 2. Tweet Service

**Domain**: Tweet creation and management

**Responsibilities**:

- Tweet creation, editing, deletion
- Media attachment handling - _integrates with Cloudinary_
- Thread management
- Tweet privacy controls and scheduling
- Draft management

## 3. Timeline Service

**Domain**: Feed generation and timeline management

**Responsibilities**:

- Home timeline construction
- Algorithmic and chronological feeds
-
- Timeline caching and optimization
- Real-time feed updates

## 4. Engagement Service

**Domain**: User interactions with tweets

**Responsibilities**:

- Likes, retweets, replies
- Bookmarks and shares
- Engagement analytics and counts
- Interaction history

## 5. Relationship Service

**Domain**: User connections and social graph

**Responsibilities**:

- Follow/unfollow functionality
- Follower/following management
- Blocking and muting
- Social graph queries

## 6. Messaging Service

**Domain**: Direct messaging system

**Responsibilities**:

- Private messaging between users
- Message history
- Message status (sent, delivered, read)
- Media sharing in messages - _integrates with Cloudinary_

## 7. Notification Service

**Domain**: Real-time notifications

**Responsibilities**:

- Push notifications
- In-app notifications
- Email notifications

## 8. Search Service

**Domain**: Search and discovery

**Responsibilities**:

- User search
- Post search with full-text indexing
- Hashtag search and trending
- Search suggestions and history
