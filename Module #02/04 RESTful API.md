# RESTful

> In order to work with RESTful APIs in a convenient way, head over to [postman.com](postman.com) and download Postman.

# Request

Any REST request includes four essential parts:

- HTTP method
- endpoint
- headers
- body (optional)

## HTTP method

An HTTP method describes what is to be done with a resource.
There are five important HTTP methods --

- `GET` <br/>
  Retrieves data from a resource.
- `POST` <br/>
  Creates a new resource.
- `PUT` <br/>
  Completely updates an existing resource.
- `PATCH` <br/>
  Partially updates an existing resource.
- `DELETE` <br/>
  Deletes a resource.

### Resources

- [HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

## Endpoint

The specific address of the resource on the server, typically structured as a path with parameters (e.g., `/users/123`).

> **Query Parameters**
>
> A query parameter is a `key=value` pair appended at the end of the URI path after `?`. Multiple query parameters are combined together using `&`.
>
> e.g. `/users/123?page=10&limit=10`

> **Path Parameters**
>
> A path parameter is a dynamic segment within the URI path itself, used to identify a specific resource or subset of resources.
>
> Unlike query parameters, which are appended after a ?, path parameters are integrated directly into the URL structure.
>
> They are typically used to represent specific identifiers, such as IDs, names, or other unique values.
>
> e.g. `/users/:userId`
>
> `userId` is the path parameter in the above example.

## Headers

Key-value pairs providing additional information like `content-type`, `authentication` details, and other metadata related to the request.

### Resources

- [HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)

## Body

The data sent to the server for operations like creating or updating a resource, formatted in a specified data type like JSON or XML. This piece of the request is optional.

# Response

[HTTP Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---

## Key points about REST requests

- **Statelessness** <br/> Each request is treated independently, meaning the server does not need to store information about previous interactions with the client.
- **Uniform Interface** <br/> The same set of HTTP methods are used to interact with different resources across the API.
- **Resource-Oriented** <br/> The focus is on manipulating data as resources identified by their URIs.

## JavaScript Object Notation (`JSON`)

JSON (JavaScript Object Notation) is a lightweight, text-based data-interchange format. It's easy for humans to read and write, and easy for machines to parse and generate.

- **Lightweight** <br/>
  JSON is designed to be minimal, reducing the overhead of data transmission.
- **Text-based** <br/>
  It uses human-readable text, making it easy to debug and inspect.
- **Language-independent** <br/>
  Although it originated from JavaScript, JSON is supported by virtually all programming languages.
- **Hierarchical** <br/>
  It can represent complex data structures using nested objects and arrays.
- **Widely Used** <br/>
  It's the standard format for data exchange on the web, especially in APIs.

```JSON
{
  "name": "Example",
  "address": { // nesting
    "street": "123 Main St",
    "city": "Anytown"
  },
  "phones": ["555-1234", "555-5678"]
}
```

```TypeScript
const data = {
  name: "Kabir Asani",
  city: "Bengaluru"
  };

const tranportableData = JSON.stringify(data);
const decodedData = JSON.parse(tranportableData);
```

---

# Quick Assignment (Reminders API)

Create an API end-point that looks like as shown below --

- `GET` `/reminders` <br/>
  Retrieves a list of all remainders.
- `GET` `/remainders/:id` <br/>
  Retrieves a specific to-do item by its `id`.
- `POST` `/remainders` <br/>
  Creates a new remainder.
- `PUT` `/remainders/:id` <br/>
  Updates an existing remainder completely.
- `PATCH` `/remainders/:id` <br/>
  Updates an existing remainder partially.
- `DELETE` `/remainders/:id` <br/>
  Deletes a remainder.
