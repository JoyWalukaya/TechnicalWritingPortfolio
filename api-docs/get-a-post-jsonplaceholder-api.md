# Get a Post

Retrieve a single post by its ID from the JSONPlaceholder API. JSONPlaceholder is a free, public REST API used for testing and learning, and it needs no authentication.

## Endpoint

```
GET https://jsonplaceholder.typicode.com/posts/{id}
```

## Base URL

```
https://jsonplaceholder.typicode.com
```

## Path parameters

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `id` | integer | Yes | The unique ID of the post to retrieve. Valid values are 1 to 100. |

## Authentication

None. This is an open API.

## Example request

Using `curl`:

```bash
curl https://jsonplaceholder.typicode.com/posts/1
```

## Example response

A successful request returns status `200 OK` and a JSON object:

```json
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit suscipit recusandae consequuntur expedita et cum reprehenderit molestiae"
}
```

## Response fields

| Field | Type | Description |
| --- | --- | --- |
| `userId` | integer | The ID of the user who created the post. |
| `id` | integer | The unique ID of the post. |
| `title` | string | The title of the post. |
| `body` | string | The main text content of the post. |

## Status codes

| Code | Meaning |
| --- | --- |
| `200 OK` | The post was found and returned. |
| `404 Not Found` | No post exists for the given ID. The response body is an empty object `{}`. |

## Notes

- JSONPlaceholder contains 100 posts, so IDs outside the range 1 to 100 return `404`.
- The data is read only for practical purposes. You can send `POST`, `PUT` and `DELETE` requests and the API will respond as if they succeeded, but no changes are saved on the server.

## Related endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| `GET` | `/posts` | Retrieve all posts. |
| `GET` | `/posts/{id}/comments` | Retrieve the comments for a specific post. |
| `GET` | `/users/{id}` | Retrieve a single user. |
