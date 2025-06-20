# eCommerce Scraping API

<p align="center">
    <a href="https://dashboard.smartproxy.com/register?page=ecommerce-scraping-api%2Fpricing&utm_source=socialorganic&utm_medium=social&utm_campaign=github_ecommerce_scraper">
        <img src="https://i.imgur.com/v707ui6.png" alt="Smartproxy eCommerce Scraping API">
    </a>
</p>

<p align="center">
    <a href="https://discord.gg/sCr34yVDVB">
        <img src="https://dcbadge.vercel.app/api/server/gvJhWJPaB4" alt="Discord">
    </a>
    <img src="https://img.shields.io/badge/API-v2-blue" alt="API Version">
    <img src="https://img.shields.io/badge/License-MIT-green" alt="License">
</p>

## 🚀 Overview

The **eCommerce Scraping API** by Smartproxy enables developers to extract comprehensive product data from major eCommerce platforms including Amazon and Wayfair. Our API provides structured, reliable data extraction with high success rates and built-in parsing capabilities.

### ✨ Key Features

- **Multi-platform Support**: Amazon, Wayfair, and generic eCommerce sites
- **Comprehensive Data**: Products, reviews, pricing, Q&A, and search results
- **AI-Powered Parsing**: Intelligent data extraction for any eCommerce site
- **Global Coverage**: Support for multiple locales and geographical locations
- **High Performance**: Fast response times with reliable uptime
- **Developer Friendly**: RESTful API with extensive documentation and examples

## 📋 Table of Contents

- [Quick Start](#-quick-start)
- [Authentication](#-authentication)
- [Supported Platforms](#-supported-platforms)
  - [Amazon](#amazon)
  - [Wayfair](#wayfair)
  - [Generic eCommerce](#generic-ecommerce)
- [API Reference](#-api-reference)
- [Code Examples](#-code-examples)
- [Response Codes](#-response-codes)
- [Support](#-support)

## 🚀 Quick Start

### Prerequisites

- Active eCommerce Scraping API subscription
- Valid API credentials (username/password)

### Basic Request

```bash
curl -X POST https://scraper-api.smartproxy.com/v2/scrape \
  -H "Content-Type: application/json" \
  -u "username:password" \
  -d '{
    "target": "amazon",
    "url": "https://www.amazon.com/dp/B09H74FXNW"
  }'
```

## 🔐 Authentication

Authentication is handled via HTTP Basic Auth using your Smartproxy credentials.

1. Navigate to your [Smartproxy Dashboard](https://dashboard.smartproxy.com)
2. Go to **eCommerce > Authentication**
3. Enter your username and password
4. Generate and test your API request

> **Note**: The dashboard provides example requests with preset values. Customize parameters in your actual implementation.

## 🛍️ Supported Platforms

### Amazon

Extract comprehensive data from Amazon including products, reviews, pricing, and search results.

#### Available Targets

| Target | Description | Parseable | Required Parameter |
|--------|-------------|-----------|-------------------|
| `amazon` | Product page via URL | ✅ | `url` |
| `amazon_product` | Product via ASIN | ✅ | `query` |
| `amazon_pricing` | Pricing information | ✅ | `query` |
| `amazon_reviews` | Product reviews | ✅ | `query` |
| `amazon_questions` | Q&A section | ✅ | `query` |
| `amazon_search` | Search results | ✅ | `query` |
| `amazon_bestsellers` | Bestseller lists | ✅ | `query` |

#### Example Response Structure

<details>
<summary>Click to expand Amazon product response</summary>

```json
{
  "results": [
    {
      "content": {
        "url": "https://www.amazon.com/dp/B09H74FXNW",
        "asin": "B09H74FXNW",
        "title": "Gaming Headset with Microphone...",
        "price": 20.98,
        "currency": "USD",
        "rating": 4.4,
        "reviews_count": 2239,
        "images": ["https://m.media-amazon.com/images/..."],
        "description": "Product description...",
        "bullet_points": "Key features...",
        "category": [...],
        "variations": [...],
        "ads": [...]
      },
      "status_code": 200,
      "created_at": "2022-09-01 11:03:48"
    }
  ]
}
```

</details>

### Wayfair

Access Wayfair product data and search results.

#### Available Targets

| Target | Description | Parseable | Required Parameter |
|--------|-------------|-----------|-------------------|
| `wayfair` | Product page via URL | ❌ | `url` |
| `wayfair_search` | Search results | ❌ | `query` |

### Generic eCommerce

Extract data from any eCommerce website using our AI-powered parser.

#### Target Configuration

| Target | Description | Parseable | Required Parameter |
|--------|-------------|-----------|-------------------|
| `ecommerce` | Any eCommerce site | ✅ (AI) | `url` |

> **Note**: For AI parsing, set `parse: true` and `parser_type: "ecommerce_product"`

## 📖 API Reference

### Base URL
```
https://scraper-api.smartproxy.com/v2/scrape
```

### Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `target` | string | ✅ | Scraping target (see [supported targets](#supported-platforms)) |
| `url` | string | * | Direct URL to scrape |
| `query` | string | * | Search query or product ID |
| `locale` | string | ❌ | Interface language (e.g., `en-US`, `en-GB`) |
| `geo` | string | ❌ | Geographical location |
| `device_type` | string | ❌ | Device type: `desktop`, `mobile`, `tablet` |
| `headless` | string | ❌ | JavaScript rendering: `html`, `png` |
| `parser_type` | string | ❌ | Parser type for eCommerce target |

*Required parameter depends on the target

### Device Types

- `desktop` (default)
- `desktop_chrome`
- `desktop_firefox`
- `mobile`
- `mobile_android`
- `mobile_ios`

## 💻 Code Examples

### Python

```bash
curl https://raw.githubusercontent.com/Smartproxy/eCommerce-Scraping-API/main/python/amazon.py > amazon.py
```

### PHP

```bash
curl https://raw.githubusercontent.com/Smartproxy/eCommerce-Scraping-API/main/php/amazon.php > amazon.php
```

### Node.js

```bash
curl https://raw.githubusercontent.com/Smartproxy/eCommerce-Scraping-API/main/nodejs/amazon.js > amazon.js
```

### Complete Example Collection

| Platform | Python | PHP | Node.js |
|----------|--------|-----|---------|
| Amazon Product | [amazon.py](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/python/amazon.py) | [amazon.php](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/php/amazon.php) | [amazon.js](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/nodejs/amazon.js) |
| Amazon Search | [amazonsearch.py](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/python/amazonsearch.py) | [amazonsearch.php](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/php/amazonsearch.php) | [amazonsearch.js](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/nodejs/amazonsearch.js) |
| Amazon Reviews | [amazonreviews.py](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/python/amazonreviews.py) | [amazonreviews.php](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/php/amazonreviews.php) | [amazonreviews.js](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/nodejs/amazonreviews.js) |
| Wayfair | [wayfair.py](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/python/wayfair.py) | [wayfair.php](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/php/wayfair.php) | [wayfair.js](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/nodejs/wayfair.js) |
| Generic eCommerce | [ecommerce.py](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/python/ecommerce.py) | [ecommerce.php](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/php/ecommerce.php) | [ecommerce.js](https://github.com/Smartproxy/eCommerce-Scraping-API/blob/main/nodejs/ecommerce.js) |

## 📊 Response Codes

### HTTP Status Codes

| Code | Status | Description | Action Required |
|------|--------|-------------|-----------------|
| **200** | ✅ Success | Request completed successfully | Continue processing |
| **204** | ⏳ Processing | Job still in progress | Wait and retry |
| **400** | ❌ Bad Request | Invalid request format | Check request structure |
| **401** | 🔒 Unauthorized | Invalid credentials | Verify authentication |
| **403** | 🚫 Forbidden | Access denied | Check subscription/permissions |
| **404** | 🔍 Not Found | Target not found | Verify URL/parameters |
| **429** | ⚡ Rate Limited | Too many requests | Wait before retrying |
| **500** | 🔧 Server Error | Internal server error | Contact support |
| **524** | ⏰ Timeout | Request timeout | Retry after delay |

### Parser Status Codes

| Code | Status | Description |
|------|--------|-------------|
| **12000** | ✅ Success | Data parsed successfully |
| **12002** | ❌ Parse Failed | Complete parsing failure |
| **12003** | 🚫 Not Supported | Target not supported |
| **12004** | ⚠️ Incomplete | Some fields missing |
| **12005** | ⚠️ Partial | Some fields unparsed |
| **12006** | 🔧 Error | Unexpected error occurred |
| **12007** | ❓ Unknown | Parse status unclear |
| **12008** | ❌ Failed | Failed to parse data |
| **12009** | 🔍 Not Found | Target parameters invalid |

## 🧪 Testing

### Postman Collection

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/23304112-92a123e7-171c-497e-8ca1-57eff04361f3?action=collection%2Ffork&collection-url=entityId%3D23304112-92a123e7-171c-497e-8ca1-57eff04361f3%26entityType%3Dcollection%26workspaceId%3D52705bab-433c-4fbf-afce-ccbfc97430fe)

Import our comprehensive Postman collection to test all API endpoints with pre-configured examples.

## 🆘 Support

### Documentation & Resources

- 📚 [Full API Documentation](https://smartproxy.com/scraping/ecommerce)
- 🎯 [Dashboard](https://dashboard.smartproxy.com)

### Getting Help

1. **Check Documentation**: Review this README and our full documentation
2. **Community Support**: Join our Discord for community help
3. **Technical Issues**: Contact our support team with your task ID
4. **Feature Requests**: Submit via GitHub issues

### Rate Limits & Best Practices

- Monitor your request quota in the dashboard
- Implement exponential backoff for retries
- Cache responses when appropriate
- Use appropriate `device_type` for your use case

## 📄 License

This project is licensed under the [MIT License](./LICENSE).

---
