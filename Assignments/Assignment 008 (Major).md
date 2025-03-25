# Assignment #008 (Major | `HackerNews`)

> Repository Name: `hackernews-server`

Replicate the core features of "Hacker News" platform.

It has the following entites --

1. `User`
2. `Post`
3. `Like`
4. `Comment`

Create the following routes (along with their controllers, types, etc) as well as create middlewares as appropriate.

### Authentication

1. `GET` `/auth/sign-in` -- Signs up a user (leverages JWT)
2. `GET` `/auth/log-in` -- Logs in a user (leverages JWT)

### Users

1. `GET` `/users/me` -- Returns the current user's details (based on JWT token).
2. `GET` `/users` -- Returns all the users in alphabetical order of their names (paginated).

### Posts

1. `GET` `/posts` -- Returns all posts in reverse chronological order (paginated).
2. `GET` `/posts/me` -- Returns all posts in reverse chronological order of the current user (referenced by attached JWT) (paginated).
3. `POST` `/posts` -- Creates a post (authored by the current user).
4. `DELETE` `/posts/:postId` -- Delete the post (if it belongs the current user) referenced by `postId`.

### Likes

1. `GET` `/likes/on/:postId` -- Returns all the likes in reverse chronological order (paginated) on the post referenced by `postId`.
2. `POST` `/likes/on/:postId` -- Creates a like (authored by the current user) on the post referenced by `postId`.
   > There can only be one like per user per post, creating multiple likes on the same post has no effect once a like has been created.
3. `DELETE` `/likes/on/:postId` -- Deletes the like (if existing and authored by the current user) on the post referenced by `postId`.

### Comments

1. `GET` `/comments/on/:postId` -- Returns all the comments in reverse chronological order (paginated) on the post referenced by `postId`.
2. `POST` `/comments/on/:postId` -- Creates a comment (authored by the current user) on the post referenced by `postId`.
   > There can be multiple comments per user per post.
3. `DELETE` `/comments/:commentId` -- Deletes the comment (if existing and authored by the current user).
4. `PATCH` `/comments/:commentId` -- Updates the comment's text (if existing and authored by the current user).
