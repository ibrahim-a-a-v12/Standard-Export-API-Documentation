
# 📦 Standard Export API Documentation

This API allows users to export their data in different formats (JSON, XML, CSV) with customizable filters.

---

## 🛣️ Endpoint

```
GET https://export.autodealersdigital.com/api/export/standard
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
| `types`         | array    | ❌ No    | List of type IDs to filter by. See list of available types below. |
| `published`     | boolean  | ❌ No    | Filter by published status. Use `1` for published, `0` for unpublished. |
| `sold`          | boolean  | ❌ No    | Filter by sold status. Use `1` for sold, `0` for unsold. |
| `conditions`    | array    | ❌ No    | Filter by item condition. See list of available conditions below. |
| `token`         | string   | ✅ Yes   | Your API token for authentication and rate limiting. |

---

## 🚗 Vehicle Types

| ID  | Label               |
|-----|---------------------|
| 1   | Cars & Trucks       |
| 2   | Commercial Trucks   |
| 3   | Motorcycles         |
| 4   | Power Boats         |
| 5   | RVs & Campers       |
| 6   | Sail Boats          |
| 7   | Trailers            |
| 8   | ATV/Golf-Cart       |
| 9   | Vans                |

---

## 📦 Conditions

| ID     | Label                        |
|--------|------------------------------|
| 47603  | Certified Pre-Owned          |
| 10425  | New                          |
| 10426  | Used                         |
| 10427  | Traded                       |
| 10428  | Consignment                  |
| 10429  | Demo                         |
| 10430  | Used w/ New Conversion       |

---

## 🧪 Example Request

```
GET https://export.autodealersdigital.com/api/export/standard?format=xml&published=1&token=YOUR_UNIQUE_TOKEN
```

Optional with more filters:

```
GET https://export.autodealersdigital.com/api/export/standard?format=json&types[]=1&types[]=2&conditions[]=10425&published=1&token=YOUR_UNIQUE_TOKEN
```
