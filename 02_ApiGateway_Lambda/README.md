# Use Lambda as the Integration Request Type

## 1. [Lambda service] Create a Lambda function

- Function name: kalin-bookshop-create_book
- Runtime: Node.js 8.10
- [Lambda code](lambda/kalin-bookshop-create_book/index.js)

## 2. [API Gateway service] Create POST method and use this Lambda Function

- Integration type: Lambda Function
- Lambda Function: kalin-bookshop-create_book
- ![Screenshot](2_use_lambda.png)

## 3. Allow CORS

### What is CORS?

- JS in https://www.abc.com web page invokes https://www.def.com API
- https://developer.mozilla.org/zh-TW/docs/Web/HTTP/CORS

### 3-1. Add 'Access-Control-Allow-Origin' header in "Method Response"

- ![Screenshot](3_cors_method_response.png)

### 3-2. Set Mapping Value of 'Access-Control-Allow-Origin' in "Integration Response"

- Allow JS runs in 'https://s.codepen.io' to invoke this API
- ![Screenshot](3_cors_integration_response.png)

## 4. Verify on https://codepen.io/

- [client code](client/index.js)

```
// Request header:
Content-Type: application/json;charset=utf8

// Request body:
{
  "name": "Refactoring: Improving the Design of Existing Code",
  "authors": ["Martin Fowler", "Kent Beck"]
}

// Response body:
{
  "statusCode": 200,
  "payload": {
    "name": "Refactoring: Improving the Design of Existing Code",
    "authors": ["Martin Fowler", "Kent Beck"]
  }
}
```
