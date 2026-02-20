---
stoplight-id: 3g98z3bpvvrdj
tags: [changelog]
---

# Changelog

## Februay 20, 2026

### Added
- New [Export transactions](reference/api.yaml/paths/~1payments~1v2~1transactions~1export) endpoint: Allows you to download csv files of your transactions for the selected period
- Custom Transaction Identifier (v2): Added a new optional `custom_id` string field to the B2P payments [v2] endpoints. This field allows partners to provide a custom string for easier transaction tracking and reconciliation. CSV exports support for `custom_id`

## January 28, 2026

### Added
- New rate limit 300 request per minute

## January 14, 2026

### Added
- New [Get company positions](reference/api.yaml/paths/~1oauth~1company~1positions/get) endpoint: Allows to get company positions.
- New [Create employee invitations](reference/api.yaml/paths/~1oauth~1employee-invitations/post) endpoint: Allows to create employee invitations.
- New [Get employee invitations](reference/api.yaml/paths/~1oauth~1employee-invitations/get) endpoint: Allows to get employee invitations.

## September 08, 2025

### Added
- New [Get Payment Methods](reference/api.yaml/paths/~1payment-requests~1v1~1payment-methods/get) endpoint: Retrieve a list of all available Payment Methods.
- New [Get Payment Method Fields](reference/api.yaml/paths/~1payment-requests~1v1~1payment-methods~1fields/post) endpoint: Retrieve the required fields for a specific Payment Method.
- New [Create template](reference/api.yaml/paths/~1payment-requests~1v1~1templates/post) endpoint: Create a new Payment Request template.
- New [Get templates](reference/api.yaml/paths/~1payment-requests~1v1~1templates/get) endpoint: Retrieve all existing Payment Request templates.
- New [Request Template Information](reference/api.yaml/paths/~1payment-requests~1v1~1templates~1{templateId}/get) endpoint: View details of a specific template by its ID.
- New [Delete Template](reference/api.yaml/paths/~1payment-requests~1v1~1templates~1{templateId}/delete) endpoint: Delete a template by its ID.
- New [Calculate Payment Request](reference/api.yaml/paths/~1payment-requests~1v1~1calculate/get) endpoint: Perform a preliminary calculation for a Payment Request to see fees, exchange rates, and totals.
- New [Create Single Payment Request](reference/api.yaml/paths/~1payment-requests~1v1~1single/post) endpoint: Create a single Payment Request synchronously; returns the final transaction if validation passes.
- New [Create Bulk Payment Requests](reference/api.yaml/paths/~1payment-requests~1v1~1bulk/post) endpoint: Create multiple Payment Requests (up to 50 per batch). Basic validation is performed synchronously; additional checks run asynchronously.
- New [Get Payment Request Status](reference/api.yaml/paths/~1payment-requests~1v1~1status/get) endpoint: Retrieve the status of a Payment Request using the request_id from single or bulk creation.
- New [Get Status of Payout batch](reference/api.yaml/paths/~1payment-requests~1v1~1payout~1{payoutId}/get) endpoint: Retrieve the status of a payout batch and a summary of all included Payment Requests, including how many reached a final status.

## March 06, 2025

### Added
- New [Create payout payment v2](reference/api.yaml/paths/~1payments~1v2~1payout/post) endpoint: Allows the creation of payouts for different user wallets.
- New [Get payment](reference/api.yaml/paths/~1payments~1v2~1status/get) endpoint: Enables retrieval of payment statuses.

### Changed
- Updated `GET /oauth/user` response: Added a new `wallets` field to replace the deprecated `wallet` field. It is recommended to use `wallets` instead. For more details, refer to the [User](reference/api.yaml/paths/~1oauth~1user/get).
- Updated `GET /oauth/user/common` response: Added a new `wallets` field to replace the deprecated `wallet` field. It is recommended to use `wallets` instead. For more details, refer to the [Common Scope](reference/api.yaml/paths/~1oauth~1user~1common/get).
- Updated `GET /oauth/user/balance` endpoint:  
  - Added a new `wallet` query parameter to specify a particular wallet. If not provided, the default wallet is used.  
  - Introduced a `wallet` object in the response.  
  - For more details, refer to the [Balance Scope](reference/api.yaml/paths/~1oauth~1user~1balance/get).