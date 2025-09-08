---
tags: [Cookbook]
stoplight-id: 557339a3cbec6
---

# Cookbook

## OAuth

### Redirect to  server

```php
$query = http_build_query([
    'client_id' => 1,
    'redirect_uri' => 'https://example.com/callback',
    'response_type' => 'code',
    'scope' => 'user.common user.channels user.balance',
]);

return redirect('https://mp-stage.mediacube.dev/oauth/authorize/'.'?'.$query);
```

### Issue authorization token

```php
Http::asJson()
  ->post('https://mp-stage.mediacube.dev/oauth/token', [
      'grant_type' => 'authorization_code',
      'client_id' => 1,
      'client_secret' => '<secret>',
      'redirect_uri' =>'https://example.com/callback',
      'code' => $request->code,
  ]);
```

## Payments

### Issue payment token

```php
Http::asJson()
  ->post('https://mp-stage.mediacube.dev/oauth/token', [
      'grant_type' => 'partner',
      'client_id' => 1,
      'client_secret' => '<secret>',
  ]);
```

### Create payout payment

```php
$headers = [
  'Authorization' => 'Bearer <payment_token>',
  'Content-Type' => 'application/json', 
  'Accept' => 'application/json',
];

$requestData = [
  'request_id' => 'c02e79a2-d30c-46e3-b3dd-c0e6a987acf8',
  'currency' => 'USD',
  'region' => 'cyprus',
  'data' => [
      [
        'amount' => '10',
        'wallet' => '1111222233334444',
        'description' => 'Test payment 1',
      ],
      [
        'amount' => '6.8',
        'wallet' => '5555666677778888',
        'description' => 'Test payment 2', 
      ],
  ],
];

$response = Http::asJson()
      ->withHeaders($headers)
      ->post('https://mp-stage.mediacube.dev/payments/v2/payout', $requestData);
```

### Create debit payment

```php
$headers = [
  'Authorization' => 'Bearer <payment_token>',
  'Content-Type' => 'application/json', 
  'Accept' => 'application/json',
];

$requestData = [
  'request_id' => '715f685f-03f4-442a-a49f-add9a9f88ac0',
  'data' => [
      [
        'amount' => '15.25',
        'wallet' => '3333444455556666',
        'description' => 'Test payment 3',
      ],
      [
        'amount' => '8.3',
        'wallet' => '6666777788889999',
        'description' => 'Test payment 4', 
      ],
  ],
];

$response = Http::asJson()
      ->withHeaders($headers)
      ->post('https://mp-stage.mediacube.dev/payments/debit', $requestData);
```


### Statuses

- 2 - Success
- 3 - Error

```json
"data": {
  "request_id":"c02e79a2-d30c-46e3-b3dd-c0e6a987acf8",
  "status": 2,
  "err_msg": null,
  "transactions": [
    {
      "id": 1,
      "invoice_path": "/api/transactions/1/invoice"
    },
    {
      "id": 2,
      "invoice_path": "/api/transactions/2/invoice"
    }
}
```

```json
"data": {
  "request_id":"c02e79a2-d30c-46e3-b3dd-c0e6a987acf8",
  "status": 3,
  "err_msg": 3000,
  "transactions": []
}
```