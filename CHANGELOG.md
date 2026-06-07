# Changelog

All notable changes to Socipoki are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [Unreleased]

### Planned
- Post delete and description edit
- Email confirmation on signup
- Infinite scroll / pagination
- Follower notifications
- Password reset via email link
- Private accounts
- Multiple image uploads per post
- Post image crop on upload
- Comment likes and deep replies
- Tagging users in posts (`@mention`)
- AI-powered explore recommendations

---

## [0.1.0] — 2024

### Added
- User registration, login, and logout
- Custom user model with avatar upload (auto-resized to 200×200)
- Profile editing: name, username, email, bio, website URL
- Password change
- Follow / unfollow users with follow request + accept flow
- Followers and following listing per profile
- Post creation with image upload (multi-resolution: 1500×, 500×, 250×, original)
- Post permalink via hashed ID
- Post like and save actions
- Liked and saved posts listing per profile
- Nested comments and sub-comment replies
- Hashtag extraction from post descriptions
- Tag detail pages
- Home feed showing posts from followed users
- Explore page with weighted engagement ranking
- Search across users, posts, and tags
- Instagram-style frontend UI (HTML + custom CSS)
- Heroku deployment configuration (Gunicorn + WhiteNoise)
- Avatar fallback to initials when no image uploaded

### Fixed
- Avatar upload redirect URL
- Like count not incrementing correctly
- Follow request button text not updating after acceptance
