---
tags: [Payments]
---

# Status

```json
1 - processing
2 - success
3 - error
```

# Error Message Codes

```json
1000 - ERROR_CODE_OAUTH_TOKEN
2000 - ERROR_CODE_PERMISSION_DENIED
3000 - ERROR_CODE_BALANCE_LESS_THEN_REQUESTED_AMOUNT
4000 - ERROR_CODE_APPLICATION_EXCEPTION    
```

# Grant type
```json
authotization_code - this type of token provision should be used for authorization flow through code.
рartner - providing an authorization token for payments, getting by credentials oauth flow
```

# KYC statuses
```json
1 - new
2 - pending
3 - approved
```