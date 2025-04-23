# CHANGES

- To migrate from Dolibarr to ERPNext, we need a point of origin from where we can get the
  1. Cost Center.✅
     1. A Cost Center is needed when creating a `Purchase Order` and
     2. A `Sales Invoice`.
  2. Customer.✅
     1. Creating a `Sales Invoice`.
  3. Bank Account/Income Account.
     1. For selling purposes we can use the `Sales -HF` income account.
  4. Project.✅
     1. Needed when creating a `PO`.
     2. Needed when creating a `SI`.
  5. Warehouse.✅
     1. A warehouse is needed when creating a `Purchase Order` to show where the products will go once they purchase, delivered, and Invoiced.
     2. When making a `Sales Invoice`, a warehouse is needed to affect quantities of products/items sold.
  6. Expense Account.
     1. When creating expenses
  7. Accounts.
     1. Lipa Na Mpesa Account `LNM ACC`
     2. Bank Account `Bank Account`
     3. Cash Account `Cash Account`
  8. Company. A company to make against the `PO` and `SI`.✅
  9. Tank For Tank Readings ✅
  10. WMeters for Water Readings ✅

## FIELDS EFFECTED

1. Sales `POS Profile` customer set to `mandatory`
2. Tank `DOCTYPE` connected to a customer.
3. Tank has a connection to a `Water Meter`
4. Water Meter has a`Water Reading`
5. Water Reading `DocType` connected to a `Water Meter`.
