<p align="center">
<img src="https://www.flow.cl/images/header/logo-flow.svg" width="300px"></img>
</p>

## Introduction

This project is designed to facilitate the use of the most famous payment gateway in Chile [Flow](https://www.flow.cl/) Using [Node](https://nodejs.org/en) or [Bun](https://bun.sh/).

### Requirements
- Node.js 19 or higher 
- Bun 1.1.36 or higher

### Installation
```bash
bun i @evairx/flow
```
or
```bash
npm i @evairx/flow
```

### Official Flow Documentation
[Flow API 3.01](https://www.flow.cl/docs/api.html#)

## Getting Started
1. **You must first import  ``@evairx/flow``**

using `require`
```js
const Flow = require("@evairx/flow");
```
using `import`
```js
import Flow from "@evairx/flow/esm/index.js";
```
2. **Let's instantiate Flow**
```js
const flow = new Flow({
	apiKey: process.env.FLOW_APIKEY || "your-api-key",
	secretKey: process.env.FLOW_SECRET_KEY || "your-secret-key",
	apiUrl: process.env.FLOW_APIURL || "https://sandbox.flow.cl/api"
});
```

## Guides
- [Create payment transaction](#)
- [Gets the status of a payment order.](#getStatus)

## getStatus
This way you can get the status of each transaction using the payment token.

**Example:**
```js
const tokenPayment = "A29F46F6E9AE16EEDDA0F8C0598A8FD31B6E040C";
const data = await flow.getStatus(tokenPayment);
console.log(data);
```
**Output**
```json
{
  success: true,
  data: {
    flowOrder: 2541015,
    commerceOrder: '1739475694748',    
    requestDate: '2025-02-13 16:41:36',
    status: 1,
    subject: 'Test Payment',
    currency: 'CLP',
    amount: '10000',
    payer: 'client@gmail.com',
    optional: null,
    pending_info: { media: null, date: null },
    paymentData: {...},
    merchantId: null
  }
}
```