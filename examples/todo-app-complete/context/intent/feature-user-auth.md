# Intent: Feature - User Authentication

## What

Implement user authentication system allowing users to:
- Sign up with email and password
- Log in with email and password
- Log out
- Maintain authenticated session

## Why

**User Need**: Users need secure access to their personal todos. Without authentication, todos would be shared or accessible by anyone.

**Technical Need**: Foundation for user-specific data isolation and future features (sharing, permissions).

## Success Criteria

- [ ] User can sign up with email/password
- [ ] User can log in with email/password
- [ ] User can log out
- [ ] Session persists across page refreshes
- [ ] Protected routes redirect unauthenticated users
- [ ] Password is hashed (never stored in plain text)
- [ ] JWT tokens used for authentication

## Technical Approach

- **Backend**: JWT-based authentication
- **Frontend**: Store JWT in httpOnly cookies (or localStorage for demo)
- **Database**: User table with email, hashed password, timestamps

## Related

- [Project Intent](project-intent.md)
- [Decision: Authentication Approach](../decisions/002-auth-approach.md)
- [Decision: Database Schema](../decisions/003-database-schema.md)

## Status

- **Created**: 2024-01-15
- **Phase**: Intent → Build
- **Completed**: 2024-01-18

