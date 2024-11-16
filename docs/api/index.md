# API Documentation

Access KazDATA's data programmatically through our REST API.

## Quick Start

### :material-rocket-launch: Getting Started

```bash
# Example API request
curl -X GET "https://api.kazdata.kz/v1/companies" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### :material-key: Authentication

1. Get API key from dashboard
2. Include in Authorization header
3. Use Bearer token format
4. Manage keys in settings
5. Rotate keys regularly

## API Endpoints

### :material-office-building: Organizations API

```json
GET /v1/companies
{
  "limit": 10,
  "offset": 0,
  "filters": {
    "region": "Almaty",
    "industry": "Manufacturing"
  }
}
```

### :material-swap-horizontal: Trade API

```json
GET /v1/trade/statistics
{
  "period": "2024-01",
  "type": "import",
  "country": "KZ"
}
```

### :material-factory: Production API

```json
GET /v1/production/volume
{
  "industry": "Manufacturing",
  "period": "2024-Q1"
}
```

### :material-gavel: Procurement API

```json
GET /v1/tenders
{
  "status": "active",
  "category": "Construction"
}
```

## Request Format

### :material-code-json: Parameters

Common parameters:

| Parameter | Type | Description |
|-----------|------|-------------|
| limit | integer | Results per page |
| offset | integer | Pagination offset |
| filters | object | Search filters |
| fields | array | Field selection |
| sort | string | Sort order |

### :material-filter: Filters

Filter syntax:

```json
{
  "filters": {
    "field": "value",
    "range": {
      "min": 0,
      "max": 100
    },
    "in": ["value1", "value2"]
  }
}
```

## Response Format

### :material-code-brackets: Structure

Standard response:

```json
{
  "status": "success",
  "data": [...],
  "meta": {
    "total": 100,
    "page": 1,
    "pages": 10
  }
}
```

### :material-alert: Error Handling

Error response:

```json
{
  "status": "error",
  "code": "ERROR_CODE",
  "message": "Error description",
  "details": {...}
}
```

## Rate Limits

### :material-speedometer: Limits

| Plan | Requests/min | Daily Limit |
|------|-------------|-------------|
| Basic | 60 | 10,000 |
| Pro | 300 | 100,000 |
| Enterprise | Custom | Custom |

### :material-clock: Headers

Rate limit headers:

```http
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 59
X-RateLimit-Reset: 1612345678
```

## Code Examples

### :material-language-python: Python

```python
import requests

API_KEY = "your_api_key"
BASE_URL = "https://api.kazdata.kz/v1"

headers = {
    "Authorization": f"Bearer {API_KEY}"
}

response = requests.get(
    f"{BASE_URL}/companies",
    headers=headers,
    params={"limit": 10}
)

data = response.json()
```

### :material-language-javascript: JavaScript

```javascript
const API_KEY = 'your_api_key';
const BASE_URL = 'https://api.kazdata.kz/v1';

async function fetchCompanies() {
  const response = await fetch(`${BASE_URL}/companies`, {
    headers: {
      'Authorization': `Bearer ${API_KEY}`
    }
  });
  
  const data = await response.json();
  return data;
}
```

## Best Practices

### :material-lightbulb: Optimization

1. Use field selection
2. Implement pagination
3. Cache responses
4. Handle rate limits
5. Batch requests

### :material-security: Security

1. Protect API keys
2. Use HTTPS
3. Validate responses
4. Monitor usage
5. Regular updates

## Support

### :material-help: Resources

- [API Status](https://status.kazdata.kz)
- [Support Portal](../support/contact.md)
- [Rate Limits](rate-limits.md)
- [FAQ](../getting-started/faq.md)
- [Updates](../support/updates.md)

### :material-tools: Tools

- API Console
- Test Environment
- Code Libraries
- Sample Projects
- Documentation

!!! tip "API Updates"
    Check our [changelog](changelog.md) for API updates and new features.
