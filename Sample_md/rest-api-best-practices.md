# REST API Design Best Practices

> A quick reference for building clean, consistent, and developer-friendly APIs.

---

## 1. Use Nouns for Endpoints, Not Verbs

Resources should be nouns. HTTP methods carry the action.

| ✅ Good                  | ❌ Bad                    |
|--------------------------|--------------------------|
| `GET /users`             | `GET /getUsers`          |
| `POST /orders`           | `POST /createOrder`      |
| `DELETE /posts/42`       | `DELETE /deletePost/42`  |

---

## 2. Use HTTP Methods Correctly

| Method   | Purpose                     | Idempotent? |
|----------|-----------------------------|-------------|
| `GET`    | Read a resource             | ✅ Yes       |
| `POST`   | Create a new resource       | ❌ No        |
| `PUT`    | Replace a resource fully    | ✅ Yes       |
| `PATCH`  | Partially update a resource | ✅ Yes       |
| `DELETE` | Remove a resource           | ✅ Yes       |

---

## 3. Use Standard HTTP Status Codes

```
200 OK              – Successful GET, PUT, PATCH
201 Created         – Successful POST
204 No Content      – Successful DELETE
400 Bad Request     – Validation error / malformed input
401 Unauthorized    – Missing or invalid auth
403 Forbidden       – Authenticated but not allowed
404 Not Found       – Resource doesn't exist
409 Conflict        – State conflict (e.g. duplicate entry)
422 Unprocessable   – Semantic validation failure
500 Internal Error  – Something broke server-side
```

---

## 4. Version Your API

Always version from day one to allow non-breaking evolution:

```
/api/v1/users
/api/v2/users
```

---

## 5. Use Consistent Naming Conventions

- **Lowercase** with **hyphens** for URLs: `/user-profiles`
- **snake_case** for JSON fields: `{ "first_name": "Priya" }`
- Plural nouns for collections: `/articles`, `/products`
- Singular for a specific resource: `/articles/7`

---

## 6. Support Filtering, Sorting & Pagination

```
GET /products?category=electronics&sort=price&order=asc
GET /users?page=2&limit=20
```

Return pagination metadata in the response:

```json
{
  "data": [...],
  "meta": {
    "page": 2,
    "limit": 20,
    "total": 154
  }
}
```

---

## 7. Return Meaningful Error Responses

```json
{
  "error": {
    "code": "VALIDATION_FAILED",
    "message": "The 'email' field is required.",
    "field": "email"
  }
}
```

---

## 8. Secure Your API

- Always use **HTTPS**
- Authenticate with **JWT** or **OAuth 2.0**
- Rate-limit endpoints to prevent abuse
- Validate and sanitize all input server-side
- Never expose internal error stack traces to clients

---

## 9. Document Everything

Use **OpenAPI / Swagger** to auto-generate interactive docs. Document:
- Request parameters and body schema
- All possible response codes
- Authentication requirements
- Example requests and responses

---

## Resources

- [RESTful API Design — Best Practices](https://restfulapi.net/)
- [OpenAPI Specification](https://swagger.io/specification/)
- [HTTP Status Codes Reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

---
_Last updated: 2026-05-09_
