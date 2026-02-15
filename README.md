# Enally.in Free AI - Complete API Documentation

**The World's First Completely Free Enterprise-Grade AI for Students & Developers**

**API Version:** 2.0.0  
**Updated:** February 15, 2026  
**Base URL:** `https://ai.enally.in/api-backend.php`  
**Status:** ✅ 100% Uptime | ✅ Free Forever | ✅ No Credit Card Required

---

## 📋 Table of Contents

1. [Why Enally AI is Free](#-why-enally-ai-is-free)
2. [Quick Start](#-quick-start)
3. [Authentication](#-authentication)
4. [Endpoint Reference](#-endpoint-reference)
5. [Request Examples](#-request-examples)
6. [Response Examples](#-response-examples)
7. [Error Handling](#-error-handling)
8. [Advanced Usage](#-advanced-usage)
9. [Code Examples](#-code-examples)
10. [Troubleshooting](#-troubleshooting)

---

## 💚 Why Enally AI is Free

**The Problem We're Solving:**  
College students and aspiring developers shouldn't need a premium subscription to build amazing projects. Paying for an API shouldn't cost more than your daily coffee. Enterprise-grade AI should be accessible to everyone, not just those who can afford expensive subscriptions.

**Our Commitment:**
- **100% Free Forever** - No hidden charges, no freemium trap, no surprise payments
- **No Credit Card Required** - Just sign up with email and OTP verification
- **Same Power, Zero Cost** - Enterprise-grade multimodal AI for students and developers
- **For Talent, Not Wallets** - We believe great ideas deserve great tools, regardless of budget

---

## 🚀 Quick Start

### What is Enally AI 2.0?

Enally AI 2.0 is a powerful, completely free enterprise-grade API that provides:
- **Text-based chat completions** with context awareness and custom system prompts
- **Multimodal analysis** supporting images and videos for research and projects
- **Real-time streaming** responses for interactive applications and demos
- **Advanced reasoning** capabilities for complex problems, math, and coding
- **Unlimited students** accessing the same professional-grade features
- **No quotas or hidden fees** - use it for college projects, hackathons, and personal portfolios

### Perfect For:
✅ College project assignments  
✅ Hackathon development  
✅ Portfolio building projects  
✅ Competitive programming  
✅ Research and analysis  
✅ Content creation for student blogs  

### Quick Links
- **🏠 Main Website:** https://ai.enally.in/
- **🔑 Request API Key:** https://ai.enally.in/api
- **🧪 Test API:** https://ai.enally.in/test-api
- **📚 GitHub Repository:** https://github.com/03prashantpk/enally.in-ai
- **📖 Full Documentation:** You're reading it!

### Prerequisites
- A validated email address (OTP verification)
- Your project domain (for whitelisting and security)
- API key (request at https://ai.enally.in/api)
- HTTPS recommended for production deployments

---

## 🔐 Authentication

All API requests require authentication headers to ensure secure access. Our security system validates both your API key and origin domain to prevent unauthorized usage.

### Security Features

✅ **Origin Validation** - Each API key is tied to specific whitelisted domains  
✅ **Rate Limiting** - 30 requests per minute, 500 requests per hour per domain  
✅ **Key-Domain Binding** - API keys only work from their registered domains  
✅ **Automatic CORS** - Proper CORS headers for whitelisted origins only  
✅ **Request Logging** - All requests are logged for security auditing  

### Required Headers

| Header | Value | Description |
|--------|-------|-------------|
| `Content-Type` | `application/json` | The format of the request body. |
| `X-API-Key` | `enally_your_api_key_here` | Your unique API key (starts with `enally_`). |
| `Origin` | `https://your-domain.com` | The domain whitelisted for your API key. |

### Example Headers

```http
Content-Type: application/json
X-API-Key: enally_abc123def456...
Origin: https://your-website.com
```

### Getting Your API Key

1. Visit **https://ai.enally.in/api** to request an API key
2. Fill in your email, name, domain, and project details
3. Verify your email via OTP
4. Your domain will be whitelisted and you'll receive your API key
5. Test your integration at **https://ai.enally.in/test-api**

> **Security Note:** Never expose your API key in client-side JavaScript. Always proxy requests through your backend server. Localhost testing requires configuration - contact us for development access.

---

## 📡 Endpoint Reference

The API provides a single endpoint with multiple actions:

### Base Endpoint

```
POST https://ai.enally.in/api-backend.php
```

### Available Actions

| Action | Description | Auth Required |
|--------|-------------|---------------|
| `chat` | Chat completion (streaming & non-streaming) | ✅ Yes |
| `report_issue` | Report technical issues | ❌ No |
| `status` | Check API health and capabilities | ❌ No |

---

## 💬 Request Examples

### 1. Basic Chat Request (Non-Streaming)

The simplest way to interact with the API.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": "Hello! How are you?"
    }
  ],
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": "Hello! How are you?"
      }
    ],
    "stream": false
  }'
```

**Expected Response:**
```json
{
  "id": "abc123def456ghi789",
  "model": "enally-ai-2.0v",
  "choices": [
    {
      "finish_reason": "stop",
      "message": {
        "content": "Hello! I'm doing well, thank you for asking. How can I help you today?",
        "role": "assistant"
      },
      "index": 0
    }
  ],
  "usage": {
    "completion_tokens": 18,
    "prompt_tokens": 12,
    "total_tokens": 30,
    "completion_tokens_details": {
      "reasoning_tokens": 0
    },
    "prompt_tokens_details": {
      "cached_tokens": 0
    }
  },
  "created": 1771060855,
  "object": "chat.completion",
  "request_id": "a1b2c3d4e5f6g7h8",
  "api_version": "2.0.0"
}
```

---

### 2. Chat with Conversation History

Maintain context by including previous messages.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": "What is the capital of France?"
    },
    {
      "role": "assistant",
      "content": "The capital of France is Paris."
    },
    {
      "role": "user",
      "content": "What's the population?"
    }
  ],
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {"role": "user", "content": "What is the capital of France?"},
      {"role": "assistant", "content": "The capital of France is Paris."},
      {"role": "user", "content": "What'\''s the population?"}
    ],
    "stream": false
  }'
```

---

### 3. Streaming Chat Request

Get real-time responses as they're generated.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": "Tell me a short story about a robot."
    }
  ],
  "stream": true
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -N \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": "Tell me a short story about a robot."
      }
    ],
    "stream": true
  }'
```

**Expected Streaming Response:**
```
data: {"id":"abc123","model":"enally-ai-2.0v","choices":[{"index":0,"delta":{"role":"assistant"}}]}

data: {"id":"abc123","model":"enally-ai-2.0v","choices":[{"index":0,"delta":{"content":"Once"}}]}

data: {"id":"abc123","model":"enally-ai-2.0v","choices":[{"index":0,"delta":{"content":" upon"}}]}

data: {"id":"abc123","model":"enally-ai-2.0v","choices":[{"index":0,"delta":{"content":" a"}}]}

data: {"id":"abc123","model":"enally-ai-2.0v","choices":[{"index":0,"delta":{"content":" time"}}]}

...

data: [DONE]
```

---

### 4. Chat with Reasoning Mode

Enable advanced reasoning for complex problems.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": "A car travels 120 km in 2 hours. What is the average speed?"
    }
  ],
  "enable_reasoning": true,
  "max_reasoning_tokens": 1024,
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": "A car travels 120 km in 2 hours. What is the average speed?"
      }
    ],
    "enable_reasoning": true,
    "max_reasoning_tokens": 1024,
    "stream": false
  }'
```

**Expected Response:**
```json
{
  "id": "d806c9d1d7924ade8de80860be478b24",
  "model": "enally-ai-2.0v",
  "choices": [
    {
      "finish_reason": "stop",
      "message": {
        "content": "60 km/h.",
        "role": "assistant",
        "reasoning": "The problem is to find average speed. Average speed is total distance divided by total time. Distance is 120 km, time is 2 hours. So 120 km / 2 h = 60 km/h."
      },
      "index": 0
    }
  ],
  "usage": {
    "completion_tokens": 70,
    "prompt_tokens": 42,
    "total_tokens": 112,
    "completion_tokens_details": {
      "reasoning_tokens": 62
    },
    "prompt_tokens_details": {
      "cached_tokens": 0
    }
  },
  "created": 1771060931,
  "object": "chat.completion",
  "request_id": "2026021417221057edef7478124e31",
  "api_version": "2.0.0"
}
```

---

### 5. Chat with Custom System Prompt

Customize the AI's behavior and tone.

**Request Body:**
```json
{
  "action": "chat",
  "system_prompt": "You are a helpful coding assistant. Provide concise code examples with explanations.",
  "messages": [
    {
      "role": "user",
      "content": "How do I reverse a string in Python?"
    }
  ],
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "system_prompt": "You are a helpful coding assistant. Provide concise code examples with explanations.",
    "messages": [
      {
        "role": "user",
        "content": "How do I reverse a string in Python?"
      }
    ],
    "stream": false
  }'
```

---

### 6. Chat with Temperature Control

Control the creativity and randomness of responses.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": "Write a creative tagline for a coffee shop."
    }
  ],
  "temperature": 0.9,
  "max_tokens": 50,
  "top_p": 0.95,
  "stream": false
}
```

**Parameters Explanation:**
- `temperature`: `0.0` to `2.0` (0 = deterministic, 2 = very creative)
- `max_tokens`: Maximum tokens in response
- `top_p`: Nucleus sampling (0.1 to 1.0)

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": "Write a creative tagline for a coffee shop."
      }
    ],
    "temperature": 0.9,
    "max_tokens": 50,
    "top_p": 0.95,
    "stream": false
  }'
```

---

### 7. Multimodal Request (Image + Text)

Analyze images with text queries.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "What's in this image?"
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "https://example.com/image.jpg"
          }
        }
      ]
    }
  ],
  "stream": false
}
```

**Alternative: Base64 Encoded Image**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "Describe this image in detail."
        },
        {
          "type": "image_url",
          "image_url": {
            "url": "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAA..."
          }
        }
      ]
    }
  ],
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": [
          {
            "type": "text",
            "text": "What'\''s in this image?"
          },
          {
            "type": "image_url",
            "image_url": {
              "url": "https://example.com/image.jpg"
            }
          }
        ]
      }
    ],
    "stream": false
  }'
```

---

### 8. Multimodal Request (Video + Text)

Analyze video content.

**Request Body:**
```json
{
  "action": "chat",
  "messages": [
    {
      "role": "user",
      "content": [
        {
          "type": "text",
          "text": "Describe the events in this video."
        },
        {
          "type": "video_url",
          "video_url": {
            "url": "https://example.com/video.mp4"
          }
        }
      ]
    }
  ],
  "stream": false
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -d '{
    "action": "chat",
    "messages": [
      {
        "role": "user",
        "content": [
          {
            "type": "text",
            "text": "Describe the events in this video."
          },
          {
            "type": "video_url",
            "video_url": {
              "url": "https://example.com/video.mp4"
            }
          }
        ]
      }
    ],
    "stream": false
  }'
```

---

### 9. Report Issue

Report technical problems or request support.

**Request Body:**
```json
{
  "action": "report_issue",
  "domain": "https://myapp.com",
  "email": "developer@myapp.com",
  "message": "Getting 429 errors even though we haven't exceeded our quota. Please investigate."
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -d '{
    "action": "report_issue",
    "domain": "https://myapp.com",
    "email": "developer@myapp.com",
    "message": "Getting 429 errors even though we haven'\''t exceeded our quota. Please investigate."
  }'
```

**Expected Response:**
```json
{
  "success": true,
  "message": "Issue reported successfully. We will contact you soon.",
  "issue_id": "issue_1771060946_a1b2c3d4",
  "timestamp": "2026-02-14T12:35:46+00:00"
}
```

---

### 10. Get API Status

Check API health and available features.

**Request Body:**
```json
{
  "action": "status"
}
```

**cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -d '{
    "action": "status"
  }'
```

**Expected Response:**
```json
{
  "status": "operational",
  "api_name": "Enally-AI-2.0V",
  "version": "2.0.0",
  "model": "enally-ai-2.0v",
  "timestamp": "2026-02-14T12:35:46+00:00",
  "uptime": 86400,
  "statistics": {
    "total_requests": 1543,
    "total_tokens": 456789,
    "active_domains": 3
  },
  "capabilities": [
    "chat_completion",
    "multimodal_input",
    "streaming_responses",
    "reasoning_mode",
    "issue_reporting"
  ],
  "limits": {
    "max_request_size": "2MB",
    "rate_limit_per_minute": 30,
    "rate_limit_per_hour": 500,
    "default_daily_token_limit": 100000,
    "default_daily_request_limit": 100
  }
}
```

---

## 🔴 Error Handling

### Error Response Format

All errors follow this consistent format:

```json
{
  "error": {
    "message": "Error description",
    "code": 400,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

### Common Errors

#### 1. Invalid API Key (403)

**Cause:** Wrong API key, missing `X-API-Key` header, or API key format is incorrect.

**Response:**
```json
{
  "error": {
    "message": "Access denied: Invalid API key",
    "code": 403,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00",
    "details": "API key must start with 'enally_' and be valid"
  }
}
```

**Solution:** 
- Verify your API key is correct and starts with `enally_`
- Ensure the `X-API-Key` header is included in your request
- Request a new API key at https://ai.enally.in/api if needed

---

#### 2. Origin Not Whitelisted or Key-Origin Mismatch (403)

**Cause:** The origin domain in the `Origin` header doesn't match the domain registered for your API key.

**Response:**
```json
{
  "error": {
    "message": "Access denied: Origin not whitelisted for this API key",
    "code": 403,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00",
    "details": "Each API key is bound to specific whitelisted domains"
  }
}
```

**Solution:** 
- Ensure the `Origin` header matches your registered domain exactly
- API keys only work from their authorized domains
- Contact services@enally.in to update your whitelisted domain
- For testing, use the interactive tester at https://ai.enally.in/test-api

---

#### 3. Rate Limit Exceeded (429)

**Cause:** Exceeded 30 requests per minute or 500 requests per hour limit.

**Response:**
```json
{
  "error": {
    "message": "Rate limit exceeded. Limits: 30/minute, 500/hour",
    "code": 429,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00",
    "retry_after": 12,
    "limits": {
      "per_minute": 30,
      "per_hour": 500
    }
  }
}
```

**Solution:** 
- Implement exponential backoff and request throttling
- Use the `retry_after` value (in seconds) before retrying
- Cache responses when possible to reduce API calls
- Optimize your request patterns and consider batching

---

#### 4. Daily Quota Exceeded (429)

**Cause:** Daily token or request limit reached.

**Response:**
```json
{
  "error": {
    "message": "Daily quota exceeded. Please try again tomorrow.",
    "code": 429,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Wait until the next day or contact support to increase your quota.

---

#### 5. Invalid JSON (400)

**Cause:** Malformed JSON in request body.

**Response:**
```json
{
  "error": {
    "message": "Invalid JSON: Syntax error",
    "code": 400,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Validate your JSON syntax.

---

#### 6. Missing Required Fields (400)

**Cause:** Required parameters are missing.

**Response:**
```json
{
  "error": {
    "message": "Missing required field: messages (must be array)",
    "code": 400,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Ensure all required fields are included.

---

#### 7. Invalid Content Type (400)

**Cause:** Missing or incorrect `Content-Type` header.

**Response:**
```json
{
  "error": {
    "message": "Invalid content type. Expected: application/json",
    "code": 400,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Set `Content-Type: application/json` header.

---

#### 8. Request Too Large (413)

**Cause:** Request body exceeds 2MB limit.

**Response:**
```json
{
  "error": {
    "message": "Request payload too large. Maximum: 2MB",
    "code": 413,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Reduce request size or compress images.

---

#### 9. Method Not Allowed (405)

**Cause:** Using GET instead of POST.

**Response:**
```json
{
  "error": {
    "message": "Method not allowed",
    "code": 405,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Use POST method for all requests.

---

#### 10. Maintenance Mode (503)

**Cause:** API is under maintenance.

**Response:**
```json
{
  "error": {
    "message": "Service temporarily unavailable for maintenance",
    "code": 503,
    "request_id": "a1b2c3d4e5f6g7h8",
    "timestamp": "2026-02-14T12:35:46+00:00"
  }
}
```

**Solution:** Wait and retry after a few minutes.

---

## 🚀 Advanced Usage

### Complete Request with All Options

**Request Body:**
```json
{
  "action": "chat",
  "system_prompt": "You are a helpful, creative assistant.",
  "messages": [
    {
      "role": "user",
      "content": "Write a haiku about coding."
    }
  ],
  "stream": false,
  "enable_reasoning": true,
  "max_reasoning_tokens": 512,
  "temperature": 0.8,
  "max_tokens": 100,
  "top_p": 0.9
}
```

**Full cURL Example:**
```bash
curl -X POST https://ai.enally.in/api-backend.php \
  -H "Content-Type: application/json" \
  -H "X-API-Key: enally_your_api_key_here" \
  -H "Origin: https://your-domain.com" \
  -H "User-Agent: MyApp/1.0" \
  -d '{
    "action": "chat",
    "system_prompt": "You are a helpful, creative assistant.",
    "messages": [
      {
        "role": "user",
        "content": "Write a haiku about coding."
      }
    ],
    "stream": false,
    "enable_reasoning": true,
    "max_reasoning_tokens": 512,
    "temperature": 0.8,
    "max_tokens": 100,
    "top_p": 0.9
  }'
```

---

## 💻 Code Examples

### JavaScript / Fetch

```javascript
async function chatWithEnally() {
  const response = await fetch('https://ai.enally.in/api-backend.php', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-API-Key': 'enally_your_api_key_here',
      'Origin': 'https://your-domain.com'
    },
    body: JSON.stringify({
      action: 'chat',
      messages: [
        { role: 'user', content: 'Hello!' }
      ],
      stream: false
    })
  });

  const data = await response.json();
  
  if (data.error) {
    console.error('Error:', data.error.message);
    return;
  }

  console.log('Response:', data.choices[0].message.content);
  console.log('Tokens used:', data.usage.total_tokens);
}

chatWithEnally();
```

---

### JavaScript / Streaming with EventSource Alternative

```javascript
async function streamChat() {
  const response = await fetch('https://ai.enally.in/api-backend.php', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'X-API-Key': 'enally_your_api_key_here',
      'Origin': 'https://your-domain.com'
    },
    body: JSON.stringify({
      action: 'chat',
      messages: [
        { role: 'user', content: 'Tell me a story.' }
      ],
      stream: true
    })
  });

  const reader = response.body.getReader();
  const decoder = new TextDecoder();

  while (true) {
    const { done, value } = await reader.read();
    if (done) break;

    const chunk = decoder.decode(value);
    const lines = chunk.split('\n');

    for (const line of lines) {
      if (line.startsWith('data: ')) {
        const data = line.substring(6);
        if (data.trim() === '[DONE]') {
          console.log('\nStream completed');
          return;
        }

        try {
          const json = JSON.parse(data);
          const content = json.choices[0]?.delta?.content || '';
          if (content) {
            process.stdout.write(content);
          }
        } catch (e) {
          // Skip invalid JSON
        }
      }
    }
  }
}

streamChat();
```

---

### Python / Requests

```python
import requests

url = "https://ai.enally.in/api-backend.php"

headers = {
    "Content-Type": "application/json",
    "X-API-Key": "enally_your_api_key_here",
    "Origin": "https://your-domain.com"
}

payload = {
    "action": "chat",
    "messages": [
        {"role": "user", "content": "Hello!"}
    ],
    "stream": False
}

response = requests.post(url, json=payload, headers=headers)
data = response.json()

if "error" in data:
    print(f"Error: {data['error']['message']}")
else:
    print(f"Response: {data['choices'][0]['message']['content']}")
    print(f"Tokens used: {data['usage']['total_tokens']}")
```

---

### Python / Streaming

```python
import requests
import json

url = "https://ai.enally.in/api-backend.php"

headers = {
    "Content-Type": "application/json",
    "X-API-Key": "enally_your_api_key_here",
    "Origin": "https://your-domain.com"
}

payload = {
    "action": "chat",
    "messages": [
        {"role": "user", "content": "Tell me a story."}
    ],
    "stream": True
}

response = requests.post(url, json=payload, headers=headers, stream=True)

for line in response.iter_lines():
    if line:
        line = line.decode('utf-8')
        if line.startswith('data: '):
            data_str = line[6:]
            if data_str.strip() == '[DONE]':
                print("\nStream completed")
                break
            try:
                data = json.loads(data_str)
                content = data['choices'][0]['delta'].get('content', '')
                if content:
                    print(content, end='', flush=True)
            except json.JSONDecodeError:
                pass
```

---

### Python / With Image Analysis

```python
import requests
import base64

# Load and encode image
with open("image.jpg", "rb") as image_file:
    base64_image = base64.b64encode(image_file.read()).decode('utf-8')

url = "https://ai.enally.in/api-backend.php"

headers = {
    "Content-Type": "application/json",
    "X-API-Key": "enally_your_api_key_here",
    "Origin": "https://your-domain.com"
}

payload = {
    "action": "chat",
    "messages": [
        {
            "role": "user",
            "content": [
                {
                    "type": "text",
                    "text": "What's in this image?"
                },
                {
                    "type": "image_url",
                    "image_url": {
                        "url": f"data:image/jpeg;base64,{base64_image}"
                    }
                }
            ]
        }
    ],
    "stream": False
}

response = requests.post(url, json=payload, headers=headers)
data = response.json()

if "error" in data:
    print(f"Error: {data['error']['message']}")
else:
    print(f"Response: {data['choices'][0]['message']['content']}")
```

---

### Node.js / Express Backend Proxy

```javascript
const express = require('express');
const fetch = require('node-fetch');

const app = express();
app.use(express.json());

const ENALLY_API_KEY = process.env.ENALLY_API_KEY;
const ENALLY_ORIGIN = process.env.ENALLY_ORIGIN;

app.post('/api/chat', async (req, res) => {
  try {
    const response = await fetch('https://ai.enally.in/api-backend.php', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'X-API-Key': ENALLY_API_KEY,
        'Origin': ENALLY_ORIGIN
      },
      body: JSON.stringify({
        action: 'chat',
        messages: req.body.messages,
        stream: false
      })
    });

    const data = await response.json();
    res.json(data);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.listen(3000, () => {
  console.log('Proxy server running on port 3000');
});
```

---

### PHP / cURL

```php
<?php

$url = "https://ai.enally.in/api-backend.php";
$apiKey = "enally_your_api_key_here";
$origin = "https://your-domain.com";

$data = [
    "action" => "chat",
    "messages" => [
        ["role" => "user", "content" => "Hello!"]
    ],
    "stream" => false
];

$ch = curl_init($url);

curl_setopt_array($ch, [
    CURLOPT_POST => true,
    CURLOPT_POSTFIELDS => json_encode($data),
    CURLOPT_HTTPHEADER => [
        "Content-Type: application/json",
        "X-API-Key: {$apiKey}",
        "Origin: {$origin}"
    ],
    CURLOPT_RETURNTRANSFER => true
]);

$response = curl_exec($ch);
$httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);

if (curl_errno($ch)) {
    echo "Error: " . curl_error($ch);
} else {
    $data = json_decode($response, true);
    if (isset($data['error'])) {
        echo "API Error: " . $data['error']['message'];
    } else {
        echo "Response: " . $data['choices'][0]['message']['content'] . "\n";
        echo "Tokens used: " . $data['usage']['total_tokens'];
    }
}

curl_close($ch);
?>
```

---

## 🔧 Troubleshooting

### Issue: Getting 403 Errors

**Possible Causes:**
1. API key is incorrect or missing
2. Domain not whitelisted
3. Origin header missing or incorrect

**Solutions:**
1. Verify your API key is correct
2. Contact services@enally.in to whitelist your domain
3. Ensure `Origin` header matches your whitelisted domain exactly (including protocol)

---

### Issue: Getting 429 Rate Limit Errors

**Possible Causes:**
1. Too many requests per minute (>30)
2. Too many requests per hour (>500)
3. Daily quota exceeded

**Solutions:**
1. Implement request throttling in your application
2. Use exponential backoff for retries
3. Contact support to increase your quota

**Example Retry Logic:**
```javascript
async function chatWithRetry(payload, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      const response = await fetch('https://ai.enally.in/api-backend.php', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'X-API-Key': 'your_api_key',
          'Origin': 'https://your-domain.com'
        },
        body: JSON.stringify(payload)
      });

      if (response.status === 429) {
        const waitTime = Math.pow(2, i) * 1000; // Exponential backoff
        console.log(`Rate limited. Waiting ${waitTime}ms...`);
        await new Promise(resolve => setTimeout(resolve, waitTime));
        continue;
      }

      return await response.json();
    } catch (error) {
      if (i === maxRetries - 1) throw error;
    }
  }
}
```

---

### Issue: Streaming Not Working

**Possible Causes:**
1. Web server buffering enabled
2. Not using streaming-compatible HTTP client
3. Firewall blocking SSE connections

**Solutions:**
1. Disable buffering in your web server (nginx: `X-Accel-Buffering: no`)
2. Use a streaming-compatible client (cURL with `-N`, or fetch with ReadableStream)
3. Check firewall settings for long-lived connections

---

### Issue: Large Images Causing Errors

**Possible Causes:**
1. Request size exceeds 2MB limit
2. Image not properly encoded
3. Network timeout

**Solutions:**
1. Compress images before sending
2. Use image URLs instead of base64 when possible
3. Increase timeout settings in your HTTP client

**Image Compression Example (Python):**
```python
from PIL import Image
import io
import base64

def compress_image(image_path, max_size_kb=500):
    img = Image.open(image_path)
    
    # Resize if too large
    if img.size[0] > 1024 or img.size[1] > 1024:
        img.thumbnail((1024, 1024), Image.LANCZOS)
    
    # Compress
    buffer = io.BytesIO()
    img.save(buffer, format="JPEG", quality=85, optimize=True)
    
    return base64.b64encode(buffer.getvalue()).decode('utf-8')
```

---

### Issue: CORS Errors in Browser

**Cause:** Trying to call API directly from frontend JavaScript.

**Solution:** **Never call the API directly from the browser.** Always proxy requests through your backend server for security.

**Correct Architecture:**
```
Browser → Your Backend → Enally AI API
```

---

## 📈 Best Practices

### 1. Security

- **Never expose API keys in frontend code**
- **Always use HTTPS** in production
- **Implement rate limiting** in your application
- **Rotate API keys** regularly
- **Monitor usage** for suspicious activity

### 2. Performance

- **Cache responses** when appropriate
- **Use streaming** for long responses
- **Implement connection pooling** for multiple requests
- **Compress images** before sending
- **Use CDN URLs** for media when possible

### 3. Error Handling

- **Always check for errors** in API responses
- **Implement retry logic** with exponential backoff
- **Log errors** with request IDs for debugging
- **Handle rate limits** gracefully
- **Set appropriate timeouts** for your use case

### 4. Cost Optimization

- **Set `max_tokens`** to limit response length
- **Use lower `temperature`** for consistent responses
- **Cache common queries** to reduce API calls
- **Monitor token usage** regularly
- **Optimize prompts** to be concise

---

## 🎯 Quick Reference

### Rate Limits

| Limit Type | Default Value |
|-----------|--------------|
| Requests per minute | 30 |
| Requests per hour | 500 |
| Daily tokens | 100,000 |
| Daily requests | 100 |
| Max request size | 2MB |

### Supported Media Types

| Type | Format | Method |
|------|--------|--------|
| Text | Plain text | Direct in `content` |
| Image | JPG, PNG, GIF | URL or Base64 |
| Video | MP4, WebM | URL |

### Parameter Ranges

| Parameter | Range | Default |
|-----------|-------|---------|
| `temperature` | 0.0 - 2.0 | 1.0 |
| `top_p` | 0.0 - 1.0 | 1.0 |
| `max_tokens` | 1 - 8192 | 8192 |
| `max_reasoning_tokens` | 1 - 8192 | 1024 |

---

## 📞 Support

### Contact Information

- **Email:** services@enally.in or prashantmanwan@gmail.com
- **Website:** https://enally.in
- **Live Chat:** Available at https://enally.in/app.php
- **Documentation:** https://enally.in/readme.md
- **Developer:** Prashant Kumar (Founder & Full-Stack Developer)

### What We Support

- API integration help for students and developers
- Domain whitelisting for your projects
- Quota increases for project needs
- Technical troubleshooting
- Feature requests and suggestions
- Project-specific guidance

### Support Standards

We're committed to supporting students and developers:
- Response time: Within 24 hours for all inquiries
- Free support: No premium support tiers
- Community focus: We believe in helping each other learn
- Transparent communication: Clear answers, no corporate jargon

### What to Include in Support Requests

- Request ID from error response (if applicable)
- Full error message and screenshots
- Example request (without API key for security)
- What you're building and your use case
- Your project domain
- Preferred contact method

---

**Last Updated:** February 15, 2026  
**API Version:** 2.0.0  
**Documentation Version:** 1.1

---

## 🎓 Our Mission

**Democratizing AI for Every Student & Developer**

Enally.in was built on a simple belief: Advanced artificial intelligence should not be gatekept by expensive subscription fees. If you're a talented student with a great idea, your bank account shouldn't determine your access to world-class AI tools.

We're proving that sustainable, free AI for students is possible—not through ads, not through selling your data, but through commitment to the mission.

---

## 💪 Built By Students, For Students

- **Made in India** for the global student community
- **Zero marketing budget** spent on ads—just good word-of-mouth
- **Completely transparent** about how it works
- **Continuously improving** based on student feedback
- **No VC funding** means no pressure to monetize or exit

---

## 1️⃣ Quick Stats

| Metric | Value |
|--------|-------|
| Cost to Students | ₹0 Forever |
| Credit Card Needed | ❌ Never |
| API Requests Successfully Served | 1,000,000+ |
| Current Uptime | 99.9%+ |
| Rate Limits | 30/min, 500/hour per domain |
| Security Features | Origin validation, Key-Domain binding, CORS |
| Rate Limiting | ✅ Enabled |
| Request Logging | ✅ Enabled |
| Open Source | ✅ GitHub available |

---

## 🚀 Getting Started Right Now

1. **Visit:** https://ai.enally.in/
2. **Request API Key:** Go to https://ai.enally.in/api
3. **Fill Details:** Enter email, name, domain, and project details
4. **Verify Email:** Complete OTP verification
5. **Receive Key:** Get your API key and domain whitelist confirmation
6. **Test API:** Use https://ai.enally.in/test-api to test your integration
7. **Start Building:** Follow documentation and code examples
8. **Explore GitHub:** https://github.com/03prashantpk/enally.in-ai for samples

---

## 🔗 Important Links

| Resource | URL | Description |
|----------|-----|-------------|
| **Main Website** | https://ai.enally.in/ | Home page and features |
| **API Request Form** | https://ai.enally.in/api | Get your free API key |
| **API Testing Interface** | https://ai.enally.in/test-api | Interactive API playground |
| **GitHub Repository** | https://github.com/03prashantpk/enally.in-ai | Documentation & examples |
| **Support Email** | services@enally.in | Technical support |

---

**© 2026 Enally Technologies. Built with ❤️ for students worldwide.**

**Made free by Prashant Kumar | Keeping AI accessible to all.**

