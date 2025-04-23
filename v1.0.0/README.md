# App Update Version 1.0.1 - Minor Fixes & Improvements

## Changelog

### Banking

- [x] Pulled all payments against recent partly paid invoices to enable double banking of sales invoices.
- [x] Identified reasons for banking failures:
  - Mode of payment `Bank` not added successfully.
  - Accounts must be company accounts linked to their Bank Account under Current Assets.

### Stock

- [x] Fixed error when taking stock against Shop4/other shops.
- [x] Rectified tank reading calculations.
- [x] Corrected volume computation issues.

### Items

- [x] Updated Purchase and Sales Items with correct Valuation Rates and images.

### Sales Invoices

- [x] Resolved Sales Invoice saving issues caused by:
  - Meter reading `last_serviced` default value conflict.
  - Date-time conflict in Meter reading records.
  - **Fix:** Dropped the default value for the field.

### Purchases Page

- [x] Prevented buttons from being hidden by the keyboard.
- [x] Added purchases from each page.
- [x] Investigated and fixed limited item visibility (only 3 items shown).
- [x] Improved visibility distinction between Sales Bulk and Bottled Water items.

### Water Reading

- [x] Implemented auto-calculation of volume on the server.
- [x] Made meter reading an optional field.

### Expense Page

- [x] Added a list of expense accounts for banking.
- [x] Included expense account in Shop POS-Profile.
- [x] Added an Income Account.
- [x] Fixed keyboard avoidance view in the expense page.

### General Fixes

- [x] Resolved warehouse display issues.
- [x] Handled request timeouts when the server is unreachable.
- [x] Configured 4% waste in sales (adjustable via POS Profile as operations improve).

### User Session & Preferences

- [x] Added persistent login (stays logged in until manual logout).
- [x] Saved shop selection (e.g., Shop4 remains selected until changed).

---

**Next Version (1.2.3)** will focus on major changes.  
**Current Version (1.0.1)** addresses minor fixes and optimizations.
