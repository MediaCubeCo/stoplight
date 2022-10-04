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

### Handle callback

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

### Create payment

```php
$headers = [
  'Authorization' => 'Bearer <payment_token>',
  'Content-Type' => 'application/json', 
  'Accept' => 'application/json',
];

$requestData = [
  'request_id' => 'c02e79a2-d30c-46e3-b3dd-c0e6a987acf8',
  'data' => [
      [
        'amount' => '10.0000000001',
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
      ->post('https://mp-stage.mediacube.dev/payments', $requestData);
```
