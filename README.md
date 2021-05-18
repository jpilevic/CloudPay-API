# Introduction

CloudPay was built from the ground-up with a JSON API that makes it easy for credit card payment gateway.

## Authentication

All API requests require the use of a given credentials from CloudPay. To authenticate an API request, You should provider your credentials in the `Header`

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `CP-MERCHANT-API` | `string` | **Required**. Your Merchant API key |
| `CP-MERCHANT-USERNAME` | `string` | **Required**. Your Merchant API Username |
| `CP-MERCHANT-PASSWORD` | `string` | **Required**. Your Merchant API Password |

## Generate New Deposit Link

```http
POST https://credit.depositcenter.xyz//api/campaigns/?api_key=12345678901234567890123456789012
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `user_id` | `string` | **Required**. Your Player ID |
| `username` | `string` | **Required**. Your Player Username |
| `email` | `string` | **Required**. Your Player Email |
| `process_id` | `string` | **Required**. Your Process ID |
| `amount` | `string` | **Required**. Your Amount |
| `fail_url` | `string` | **Required**. Your Fail URL |
| `success_url` | `string` | **Required**. Your Success URL |

## Responses

Many API endpoints return the JSON representation of the resources created or edited. However, if an invalid request is submitted, or some other error occurs, Gophish returns a JSON response in the following format:

```javascript
{
    "code": 201,
    "status": true,
    "message": "The transaction was successfully created.",
    "data": {
        "type": "transaction",
        "process_id": "f82422ba-b7e4-4b35-8ab1-f32632cd3157",
        "attributes": {
            "amount": "100",
            "username": "Ceyhun Emre BOZKURT",
            "process_id": "f82422ba-b7e4-4b35-8ab1-f32632cd3157",
            "merchant_process_id": "2000"
        },
        "links": {
            "form": "http://localhost/payment/transaction/f82422ba-b7e4-4b35-8ab1-f32632cd3157?expires=1621306248&signature=46a9b0289a1544bf2ccb583d2633e8626bc26dbcb513c325868cd93609875016"
        }
    }
}
```

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `code` | `int` | Attribute describes HTTP request status |
| `status` | `bool` | Attribute desribes if the transaction was successful or not |
| `message` | `sting` | Attribute contains a message commonly used to indicate errors and succeed messages |
| `email` | `string` | Attribute describes email of player |
| `process_id` | `string` | Attribute describes process id of client side |
| `amount` | `string` | Attribute describes amount of the transaction |
| `fail_url` | `string` | Attribute describes the transaction was failed then will be redirected page url where. |
| `success_url` | `string` | Attribute describes the transaction was succeed then will be redirected page url where. |
| `form` | `string` | Attribute describes the generated transaction payment form url, It will be expired in 10 minutes after created time. |


## Status Codes

Gophish returns the following status codes in its API:

| Status Code | Description |
| :--- | :--- |
| 200 | `OK` |
| 201 | `CREATED` |
| 400 | `BAD REQUEST` |
| 404 | `NOT FOUND` |
| 500 | `INTERNAL SERVER ERROR` |

