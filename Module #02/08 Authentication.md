# JWT Authentication & Authorization

We'll leverage JWT (JSON Web Token) to authenticate our uses.

- JWT is a compact, self-contained way to securely transmit information between parties.
- JWTs are commonly used for authentication and authorization.

**How JWTs work?**

- JWTs are a standard, defined in `RFC 7519`.
- JWTs are made up of three parts: a header, payload, and signature.
- JWTs can be sent through a URL, through a POST parameter, or inside an HTTP header.
- JWTs can be stored in cookies.

**Why use JWTs?**

- JWTs are a popular choice for highly distributed websites because all the data that a server needs is stored client-side.
- JWTs are compact and can be transmitted quickly.
- JWTs can contain information that verifies the identity of a user, and their permissions.

**JWT use cases**

- JWTs are used to represent an identity and its associations, such as an administrator role or group.
- JWTs are used to help servers establish trust between an unknown client and themselves.

![JWT](https://fusionauth.io/img/shared/json-web-token.png)

A signed JWT contains these 3 parts:

- A header: which contains metadata, including information about the key used to sign the JWT.
- A body: which is a JSON object with an arbitrary payload; the keys of this JSON object are commonly called “claims”.
- A signature: which is built by performing a cryptographic operation over the header and the body.
