# Changelog

## Version v1.0.3

### New Features & Enhancements

**Sales Invoice**

- Added Debtors (Accounts Receivable) account association for each user
- Implemented unrealized profit/loss account for mobile app compliance (Frappe requirement)

**Stock Management**

- Programmatically configured waste limits per tank
- Added user type display in mobile app dashboard after login
- Fixed misleading production label caused by iOS build profile
- Improved banking-related message clarity
- Enhanced Stock Transfer docType with:
  - Driver name field
  - Vehicle license plate field

**Banking Workflow**

- Restructured banking flow to operate against cash accounts instead of invoices
- Implemented dual banking workflows:
  1. MPESA transactions
  2. Shop Income account to organization Bank Account transfers

**Internal Procurement**

- Streamlined procurement workflow by removing Purchase Order requirement
- Eliminated supplier selector
- Implemented material transfer request initiation
- Verified and updated affected accounting journals

**User Management**

- Added password change functionality in User Preferences
- Implemented password reset via email.
- Improved forgot password flow with clear status messages:
  - Success/failure notifications
  - Email validation feedback

### Fixes

- Resolved banking testability issues
- Fixed silent failures in password recovery flow
- Corrected misleading fetch messages in banking module

### Technical Improvements

- Enhanced notification system for email communications
- Updated documentation for all new workflows
