# WooCommerce Connector - GL Account Numbers

_Updated July 17, 2026_

## Table of Contents

- [Overview](#overview)
- [Accounting Integration Considerations](#accounting-integration-considerations)
- [Default Account Numbers](#default-account-numbers)
- [Account Details](#account-details)
- [Conclusion](#conclusion)

---

## Overview

The WooCommerce connector creates a new WooCommerce store (**202**) in Counterpoint.

As part of the store setup, several general ledger (GL) accounts must be configured for WooCommerce-related activity, including:
- WooCommerce payments
- Order deposit liabilities
- Sales tax payable
- Shipping fees
- Investigation / fallback activity

These accounts are required for Counterpoint Store configuration, even if you are not integrating Counterpoint with an accounting system.

---

## Accounting Integration Considerations

### Clients Without an Accounting Integration

- If you do not use an accounting integration, you can continue using standard Counterpoint reporting for all store activity, including the WooCommerce store.
- In most cases, the default account values listed in this document can be used without modification.

### Clients Using an Accounting Integration

- If you integrate Counterpoint with an accounting system, please review the default WooCommerce account numbers listed below.
- These defaults are based on Rapid's standard chart of accounts.
- If you use a custom chart of accounts or would like to modify any defaults, please notify Rapid prior to connector installation.

>#### Profit Centers with an Accounting Integration
>
>- Profit centers are commonly used by multi-store clients who utilize classes within their accounting software.
>- During installation, if the connector detects that profit centers are enabled for the company, the Profit Center Method will automatically be changed from: **None** to **Store**
>- If you are using profit centers, please notify Rapid prior to connector installation if you would like the Store 202 profit center set to something other than 202.

---

## Default Account Numbers

### Quick Reference Table

| Function | Default Account | Purpose |
|---|---|---|
| WooCommerce Tender | 1302 | Records WooCommerce customer payments |
| WooCommerce Deposit Liabilities | 2252 | Records deposits collected on WooCommerce orders |
| WooCommerce Sales Tax Payable | 2312 | Records WooCommerce tax amounts |
| Shipping | 4950 | Records shipping charges |
| WooCommerce Needs Investigation | 9902 | Catch all account for unexpected activity |

---

## Account Details

### WooCommerce Tender

| Field | Value |
|---|---|
| Default Account Number | 1302 |
| Label | Pay Codes - Account |
| Tab | Pay Codes/Main Tab |
| Table | SY_PAY_COD |
| Column | PAY_COD_ACCT_NO |

### Notes

This account records amounts paid by customers on WooCommerce.
- WooCommerce payments are imported into Counterpoint using the generic tender of `EC_WOOCOMM`.
- This pay code is recorded in the order header of imported WooCommerce orders to indicate payment was collected on WooCommerce.

**Note:** The HOME currency code is used by default. If a different currency is preferred, please notify Rapid staff.

---

## WooCommerce Deposit Liabilities

| Field | Value |
|---|---|
| Default Account Number | 2252 |
| Label | Orders - Deposits Received |
| Tabs | Stores/Orders Tab, Stores/Layaways Tab |
| Table | PS_STR |
| Columns | ORD_DEP_RECVD_ACCT_NO, LWY_DEP_RECVD_ACCT_NO |

### Notes

When a customer makes a payment (deposit) on a WooCommerce order:
- the WooCommerce Tender account (`EC_WOOCOMM`) is debited
- the WooCommerce Deposit Liabilities account is credited

This liability is relieved when:
1. the order is released in Counterpoint, and
2. the associated WooCommerce drawer is posted.

---

## WooCommerce Sales Tax Payable

| Field | Value |
|---|---|
| Default Account Number | 2312 |
| Label | Tax Authority - Tax Account |
| Tab | Tax Authorities/Rules/Main Tab |
| Table | SY_TAX_AUTH |
| Column | TAX_ACCT_NO |

### Notes

This account records tax amounts collected from customers on WooCommerce.
- WooCommerce controls all tax calculation and reporting.
- An `EC_WOOCOMM` Tax Authority and Tax Rule are automatically created so tax amounts flow into Counterpoint exactly as charged on WooCommerce.

---

## Shipping

| Field | Value |
|---|---|
| Default Account Number | 4950 |
| Label | Shipping |
| Tab | Point of Sale Control/Shipping Tab |
| Table | PS_CTL |
| Column | MISC_4_ACCT_NO |

### Notes

This account is assigned to the miscellaneous charge configured as the shipping fee in Counterpoint.
- It records shipping fees collected from WooCommerce customers.
- Depending on system configuration, this account may also record shipping fees from other order types, such as in store POS orders.

**Note:** This may be assigned to a different MISC charge number depending on configuration.

---

## WooCommerce Needs Investigation

### Applies To

- Default Pay-In Account
- Default Pay-Out Account
- Deposits Forfeited (Orders)
- Deposits Forfeited (Layaways)

| Field | Value |
|---|---|
| Default Account Number | 9902 |
| Label | WooCommerce Needs Investigation |
| Tabs | Stores/Tickets-3 Tab, Stores/Orders Tab, Stores/Layaways Tab |
| Table | PS_STR |
| Columns | PAY_IN_ACCT_NO, PAY_OUT_ACCT_NO, ORD_DEP_FORF_ACCT_NO, LWY_DEP_FORF_ACCT_NO |

### Notes

Counterpoint requires all possible store activity types to be assigned to accounts, even for activity types not used by the WooCommerce connector.

Rapid recommends using a shared catch all account of **9902 - WooCommerce Needs Investigation**. Most clients use this single investigation account rather than creating separate accounts for each unused activity type.

This account should normally never receive activity.

If transactions are recorded in this account:
1. investigate the source of the posting, and
2. report the activity to Rapid for review.

---

## Conclusion

The default account configurations outlined in this guide are designed for standard WooCommerce connector implementations within Counterpoint (using Rapid's standard chart of accounts).

**Most clients can use these defaults without modification.** However, clients using a custom chart of accounts should review all account assignments prior to installation.

If you have questions about any account configuration or would like to request changes to the defaults, please coordinate with Rapid prior to installation.
