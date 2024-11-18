# BFSI Demo Use Cases

## Credit Card Payment Service

### Setup Env Variables
````
FRMFRAUDERYURL = "https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/frmbeservice/v1.0/validate"
COREBANKAUTHURL = "https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/corebankingbeservice/v1.0/cc/auth"
````


### Request Payload - Success Scenario
```
{
  "creditCard": {
    "number": "1234-5678-9012-3456",
    "expirationDate": "12/24",
    "cvv": "123"
  },
  "amount": 100.00,
  "currency": "USD",
  "merchant_id": "MERCHANT123",
  "merchant_name": "Example Store",
  "timestamp": "2023-11-10T12:30:00Z",
  "order_reference":"123568976514651"
}
```

### Request Payload - Error Scenario
```
{
  "creditCard": {
    "number": "1234-5678-9012-3455",
    "expirationDate": "12/23",
    "cvv": "456"
  },
  "amount": 90.00,
  "currency": "USD",
  "merchant_id": "MERCHANT789",
  "merchant_name": "Example Store1",
  "timestamp": "2023-11-10T12:30:00Z",
  "order_reference":"123568976504651"
}
```

### Sample request
```
curl -X 'POST' \
  'https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/ccpaymentservice/v1.0/payment' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -H 'api-key: eyJraWQiOiJnYXRld2F5X2NlcnRpZmljYXRlX2FsaWFzIiwiYWxnIjoiUlMyNTYifQ.eyJzdWIiOiJjZWM1OWJhNS00ODA5LTRiM2EtYWE2My0wNzlhM2NiNjc3NGRAY2FyYm9uLnN1cGVyIiwiYXVkIjoiY2hvcmVvOmRlcGxveW1lbnQ6c2FuZGJveCIsImlzcyI6Imh0dHBzOlwvXC9zdHMuY2hvcmVvLmRldjo0NDNcL2FwaVwvYW1cL3B1Ymxpc2hlclwvdjJcL2FwaXNcL2ludGVybmFsLWtleSIsImtleXR5cGUiOiJTQU5EQk9YIiwic3Vic2NyaWJlZEFQSXMiOlt7InN1YnNjcmliZXJUZW5hbnREb21haW4iOm51bGwsIm5hbWUiOiJDQ1BheW1lbnRTZXJ2aWNlIC0gQ3JlZGl0Q2FyZFBheW1lbnRBUEkgN2JjIiwiY29udGV4dCI6IlwvYjQ4Y2M5M2UtZmEzMy00NDIwLWExNTUtYmM2NTNiNGQ0NmJlXC9iZnNpYmFja2VuZHNcL2NjcGF5bWVudHNlcnZpY2VcL3YxLjAiLCJwdWJsaXNoZXIiOiJjaG9yZW9fcHJvZF9hcGltX2FkbWluIiwidmVyc2lvbiI6InYxLjAiLCJzdWJzY3JpcHRpb25UaWVyIjpudWxsfV0sImV4cCI6MTczMDEyMjU0NiwidG9rZW5fdHlwZSI6IkludGVybmFsS2V5IiwiaWF0IjoxNzMwMTIxOTQ2LCJqdGkiOiIzOGQ2MmZlMy1kOTE1LTQxMTUtYTY3Zi0zYjQzZDE1ZTVkZTEifQ.IbyB7l-Ww7Go6RhsQ9o5Ln8rZJSqYNF81EeejJhilbCVcCL6XK68XwrgCdnHZgWkpsAC0lVsCgWeXn9DMU3ZBXZarOkt9Jc6hA3rhmNQKyPgHBFwDtavwljFKAOinOIawm_vM9VwO40EYUvVtoWtYP7oKM3FklCbwbWXrwprJw3D2-GtCzRUI2QTIVSwx65OBS4SGJ9tG1OLI5GxstD5PAd9MlWhDt8GRqOwuKDjcFqH3YM6JjyAaoAgfBwoSuxMPLIOb2FE1bpJuRKrxwjXgSviiP5dcK-YuxobzE6EH7N1QLPLnIXVBcwWQ8yELU7EUe-KEabv8NVWvUTgX8_GPuNHjhI1wG-DNyhMh8dsls4Vklak_FoupZYCGRL3Yiu6LBMSTmugd2g78m7FP3xKDeZJN0VXDg0_hECXLtvbpzzQk70wsNcQaVOwI54cQst5jcaUJH4ugL0MwPn_Rhh6EWk7IWGbPJamd3_D_KoPLyS2891SvkvKQpRQmoCZ0zToncQIcKNsTe30elE_9cK7lYyvQWeZW0IDzWYf-vk4AZn83SyG3bOEatHiABv3VLuzUm2Qn0mPoowo537ZKHjgfq-40AsihovAKsEkjVqyM9kvE81xVrM9MgU1v69KL-TtZfYDkpDYta9uDL9KJu3B-Vc7myuYW4QGuh4lvkyHAVI' \
  -d '{
  "creditCard": {
    "number": "1234-5678-9012-3456",
    "expirationDate": "12/24",
    "cvv": "123"
  },
  "amount": 100.00,
  "currency": "USD",
  "merchant_id": "MERCHANT123",
  "merchant_name": "Example Store",
  "timestamp": "2023-11-10T12:30:00Z",
  "order_reference":"123568976514651"
}'
```

### Sample Response - Success Scenario
```
{
  "status": "success",
  "message": "Payment successful",
  "transactionId": "TXN123456789",
  "amount": "100.0",
  "currency": "USD"
}
```

### Sample Response - Error Scenario
```
{
  "status": "failure",
  "message": "Payment failed. Insufficient funds.",
  "error": {
    "code": "INSUFFICIENT_FUNDS",
    "description": "The account has insufficient funds to process the payment."
  }
}
```
