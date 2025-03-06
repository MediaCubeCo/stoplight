---
stoplight-id: 3g98z3bpvvrdj
tags: [changelog]
---

# Changelog

## March 06, 2025

### Added
- New `POST /payments/v2/payout` endpoint: Allows the creation of payouts for different user wallets. For more details, refer to the [Create Payout Payment [v2]](reference/api.yaml/paths/~1payments~1v2~1payout/post).
- New `GET /payments/v2/status` endpoint: Enables retrieval of payment statuses. For more details, refer to the [Get Payment [v2]](reference/api.yaml/paths/~1payments~1v2~1status/get).

### Changed
- Updated `GET /oauth/user` response: Added a new `wallets` field to replace the deprecated `wallet` field. It is recommended to use `wallets` instead. For more details, refer to the [User](reference/api.yaml/paths/~1oauth~1user/get).
- Updated `GET /oauth/user/common` response: Added a new `wallets` field to replace the deprecated `wallet` field. It is recommended to use `wallets` instead. For more details, refer to the [Common Scope](reference/api.yaml/paths/~1oauth~1user~1common/get).
- Updated `GET /oauth/user/balance` endpoint:  
  - Added a new `wallet` query parameter to specify a particular wallet. If not provided, the default wallet is used.  
  - Introduced a `wallet` object in the response.  
  - For more details, refer to the [Balance Scope](reference/api.yaml/paths/~1oauth~1user~1balance/get).