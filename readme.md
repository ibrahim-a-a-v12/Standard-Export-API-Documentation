
# 📦 Standard Export API Documentation

This API allows users to export their data in different formats (JSON, XML, CSV) with customizable filters.

---

## 🛣️ Endpoint

```
GET /api/export/standard
```

---

## 🔐 Authentication

- Token-based authentication.
- Each user is assigned a **unique token**.
- Pass the token as a **query parameter**:
  ```
  ?token=YOUR_UNIQUE_TOKEN
  ```
- **Rate Limit**: Each token can be used **10 times per day**.

---

## 📥 Query Parameters

| Parameter       | Type     | Required | Description |
|----------------|----------|----------|-------------|
| `user_id`       | integer  | ✅ Yes   | The unique ID of the user requesting the export. |
| `format`        | string   | ✅ Yes   | The export format. Allowed values: `json`, `xml`, `csv`. |
| `types`         | array    | ❌ No    | List of type IDs to filter by. Allowed values: `1` to `9`. |
| `published`     | boolean  | ❌ No    | Filter by published status. Use `1` for published, `0` for unpublished. |
| `sold`          | boolean  | ❌ No    | Filter by sold status. Use `1` for sold, `0` for unsold. |
| `conditions`    | array    | ❌ No    | Filter by item condition. Allowed values: `47603`, `10425`, `10426`, `10427`, `10428`, `10429`, `10430`. |
| `token`         | string   | ✅ Yes   | Your API token for authentication and rate limiting. |

---

## 🧪 Example Request

```
GET http://localhost:82/api/export/standard?user_id=123&format=xml&published=1&token=36Z9QQbUe6Xx9YGk7mvGGOLAKMdYBrMUF2I8eOyESWGcJsr5w6mV
```

Optional with more filters:

```
GET http://localhost:82/api/export/standard?user_id=123&format=json&types[]=1&types[]=2&conditions[]=10425&published=1&token=YOUR_UNIQUE_TOKEN
```
