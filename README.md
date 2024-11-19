# BFSI Demo Use Cases

## Credit Card Payment Service

#### Setup Env Variables
````
FRMFRAUDERYURL = "https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/frmbeservice/v1.0/validate"
COREBANKAUTHURL = "https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/corebankingbeservice/v1.0/cc/auth"
````
### GET Credit Rating

#### Sample Path Param
```
1234567891
```

#### Sample Request
```
curl -X 'GET' \
  'https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/ccpaymentservice/v1.0/creditRating/1234567891' \
  -H 'accept: */*' \
  -H 'api-key: eyJraWQiOiJnYXRld2F5X2NlcnRpZmljYXRlX2FsaWFzIiwiYWxnIjoiUlMyNTYifQ.eyJzdWIiOiJjZWM1OWJhNS00ODA5LTRiM2EtYWE2My0wNzlhM2NiNjc3NGRAY2FyYm9uLnN1cGVyIiwiYXVkIjoiY2hvcmVvOmRlcGxveW1lbnQ6c2FuZGJveCIsImlzcyI6Imh0dHBzOlwvXC9zdHMuY2hvcmVvLmRldjo0NDNcL2FwaVwvYW1cL3B1Ymxpc2hlclwvdjJcL2FwaXNcL2ludGVybmFsLWtleSIsImtleXR5cGUiOiJTQU5EQk9YIiwic3Vic2NyaWJlZEFQSXMiOlt7InN1YnNjcmliZXJUZW5hbnREb21haW4iOm51bGwsIm5hbWUiOiJDQ1BheW1lbnRTZXJ2aWNlIC0gQ3JlZGl0Q2FyZFBheW1lbnRBUEkgN2JjIiwiY29udGV4dCI6IlwvYjQ4Y2M5M2UtZmEzMy00NDIwLWExNTUtYmM2NTNiNGQ0NmJlXC9iZnNpYmFja2VuZHNcL2NjcGF5bWVudHNlcnZpY2VcL3YxLjAiLCJwdWJsaXNoZXIiOiJjaG9yZW9fcHJvZF9hcGltX2FkbWluIiwidmVyc2lvbiI6InYxLjAiLCJzdWJzY3JpcHRpb25UaWVyIjpudWxsfV0sImV4cCI6MTczMTk5OTMyOSwidG9rZW5fdHlwZSI6IkludGVybmFsS2V5IiwiaWF0IjoxNzMxOTk4NzI5LCJqdGkiOiIzZWM2ZTAwYS00NDZkLTQ5NGUtYmM5ZS0xYWMxMzBhMjEzMWEifQ.d1j65VINk6KQ--zAOu_XtceazokSHjmEQXVcdSyi6IE6e6Ap7mBFXl8zWPpmtDBZ2AabhpsRinGqrq3nq-BGqbJd6VGw9FQ2IpT25kEe4baFddrIdrOvu2iNKIZ73UZBH7FyedTByUtadh3ypIw4dKTSSftNlrRQzjRMCeowFB9YWOOY8DnaYUu9Gwqq760TRX2MFC_XCaaBJ7wLWiTLc-YBMe4YNnMsMC2FcTemK8KiuUAfWXkeJHvgqLQSpA0hYLUgV0Ak2DQkJ0dWodiV1vzqxiunGAw-I2XK0JkDQiM3BGd-eiy1u69124gXrWRQNWQVetYsUhHdcwHZ41Oop5c3GKmuVbE9qxpM8Qu_RblomMpPHiFqHUl6OdGNS0CA15FD1OK6jAhWU09TAmWxWg2ixpMt_tJ-M0nqmjiBzvqwEUE7UPEak6fC89JrhHeABTIiL5xsWXzgRYGtDWMPRL8YrmrrY1uCoFD2KBvxuKXvIHSIPzQ3htE3-dbt4BdeC3YpLcunsBTJiGYNp-1MJikQq4ew4MNgKX3fTC560U9GNjUcpbhuha3yK53q4B8apz1GLsDKZwn6VMzhMyRs25jpVxo-tn6KODR28tD7Jog0s4z_-sszJ2AyCzEUDVz0858tQB6aYlLBtpv1E1vbH91Acq99kHJJTLonnwDoEYQ'
```
#### Sample Response
```
{
  "user_id": "1234567891",
  "credit_score": 590,
  "credit_rating": "Poor",
  "credit_limit": 8000,
  "outstanding_balance": 7000,
  "available_credit": 1000,
  "credit_history": "Late payments for the past year",
  "open_accounts": 1,
  "total_accounts": 4,
  "late_payments": 5,
  "derogatory_marks": 1,
  "recent_credit_inquiries": 3,
  "public_records": 1
}
```

### POST Make a Payment

#### Request Payload - Success Scenario
```
{
  "merchant_id": "MERCHANT123",
  "amount": 100.00,
  "currency": "USD",
  "card_number": "**** **** **** 3456",
  "expiry_date": "12/24",
  "cvv": "123",
  "timestamp": "2023-11-10T12:30:00Z"
}
```

#### Request Payload - Error Scenario
```
{
  "merchant_id": "MERCHANT789",
  "amount": 90.00,
  "currency": "USD",
  "card_number": "**** **** **** 3456",
  "expiry_date": "12/23",
  "cvv": "123",
  "timestamp": "2023-11-10T12:30:00Z"
}
```

#### Sample request
```
curl -X 'POST' \
  'https://b48cc93e-fa33-4420-a155-bc653b4d46be-my-env.e1-us-east-azure.choreoapis.dev/bfsibackends/ccpaymentservice/v1.0/payment' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -H 'api-key: eyJraWQiOiJnYXRld2F5X2NlcnRpZmljYXRlX2FsaWFzIiwiYWxnIjoiUlMyNTYifQ.eyJzdWIiOiJjZWM1OWJhNS00ODA5LTRiM2EtYWE2My0wNzlhM2NiNjc3NGRAY2FyYm9uLnN1cGVyIiwiYXVkIjoiY2hvcmVvOmRlcGxveW1lbnQ6c2FuZGJveCIsImlzcyI6Imh0dHBzOlwvXC9zdHMuY2hvcmVvLmRldjo0NDNcL2FwaVwvYW1cL3B1Ymxpc2hlclwvdjJcL2FwaXNcL2ludGVybmFsLWtleSIsImtleXR5cGUiOiJTQU5EQk9YIiwic3Vic2NyaWJlZEFQSXMiOlt7InN1YnNjcmliZXJUZW5hbnREb21haW4iOm51bGwsIm5hbWUiOiJDQ1BheW1lbnRTZXJ2aWNlIC0gQ3JlZGl0Q2FyZFBheW1lbnRBUEkgN2JjIiwiY29udGV4dCI6IlwvYjQ4Y2M5M2UtZmEzMy00NDIwLWExNTUtYmM2NTNiNGQ0NmJlXC9iZnNpYmFja2VuZHNcL2NjcGF5bWVudHNlcnZpY2VcL3YxLjAiLCJwdWJsaXNoZXIiOiJjaG9yZW9fcHJvZF9hcGltX2FkbWluIiwidmVyc2lvbiI6InYxLjAiLCJzdWJzY3JpcHRpb25UaWVyIjpudWxsfV0sImV4cCI6MTczMTk5ODc0NCwidG9rZW5fdHlwZSI6IkludGVybmFsS2V5IiwiaWF0IjoxNzMxOTk4MTQ0LCJqdGkiOiI0YTNmNjYxNC02YzMxLTQ5MDEtODYwMS02YjA1NGVhOTczODYifQ.I_0gDjwPhS2MpsV6YrU6NrW5FTr3U2dnLBkcjrHLWbCnMTqFtfB1CkVsxS4I6tK14CLuFw_s851VeJIHVjQe61K57O7Y-exLlEHmKEku2FRGIEUys0Jdx43W3SSbFY17dragSHaVwmGzfApS0Wi6HK25Cq8YFl8Yagzf7nYfyZ6TsZrFynFJj01O2tLq1EREV8fcdfv1xA2eQkyV11zWILp2BUVQGCDwebBttQc7FNmUHEK1Npck-OAdyRWCumbn46J4uifoQwKOMnxo4ZFjPoDUmZW3tlRT7sZgTSxTqnr4cXL8Qenj8welZFTxunB8qQ3bwGX3AKH1e7saIYJnhkks3PXTyB7mgRya0q1zBOdKnqkKyRSL-1YXLcHXkc1O7vmXiaPeXRnSCQP8ZIGxI81HXpqNR3ObEvnWfvvPNtZSUSH6ATiHg9nDucnAynGc7cBrmSBZ7aQ_qbZmxAfDbOEw6xuoRwTLCv2eWEL-MbgOscenv6xWeTqO_JU6Es3dNntC8fNMtAlVSpkjJ9yg58XxwptY9f4lOTvLBRNpbpCf8hNYu7v9ORA3Y00cJ4JlKY0CAAxeQrMhd-KalZ1D4rxVeb4zYcnVU8hYynS0I105zUgjtLl4iigIBxLG2dmEd7BGVaZS7YUTbFQ77P6CLkBNqd4EzkVk6fXZWFda1Q4' \
  -d '{
  "merchant_id": "MERCHANT123",
  "amount": 100.00,
  "currency": "USD",
  "card_number": "**** **** **** 3456",
  "expiry_date": "12/24",
  "cvv": "123",
  "timestamp": "2023-11-10T12:30:00Z"
}'
```

#### Sample Response - Success Scenario
```
{
  "merchant_id": "MERCHANT123",
  "transaction_id": "TXN123456789",
  "status": "approved",
  "authorization_code": "AUTH567",
  "message": "Transaction approved successfully."
}
```

#### Sample Response - Error Scenario
```
{
  "status": "Declined",
  "message": "Payment declined"
}
```
