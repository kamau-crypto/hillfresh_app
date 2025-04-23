# SETTING UP THE DOCUMENTS

## LINKS

1. Each field is references via the `name`. This means that for every entry, that is associated with another link within each `DocType` it has to have a `name` property.

## 1. ACCOUNTING

1.2. COMPANY ACCOUNTS.

1.1. BANK ACCOUNTS

- To link a bank account to the Company's account requires that the company account be of type `BANK` to begin with and no other way is acceptable unless customized.
- A bank Account can have its own `Payroll entry among other options`.

## 2. CUSTOMER

- You can setup `Users/Portal Users` for a Customer.
- You can also merge an existing customer with another customer, should you choose to merge one customer to another...
-

### 2.1. CUSTOMER MUST BE CONNECTED TO A PROJECT.

- [ ] A customer must be connected to a project.
  - To connect a customer to a project simply scroll the Dashboard to the `Customer Details` and connect them to their proper dashboard...
  -
- [ ]

### 2.1 CUSTOMER MUST HAVE A BANK ACCOUNT.

```ts

1. You can enable a CUSTOMER to create a sales Invoice without a `Sales Order`
2. You can enable a CUSTOMER to create a `Delivery Note`


```

- [ ] Customer Default Bank Account has to be **`A COMPANY ACCOUNT`**.

## 3. PROJECT

3.1 A project has to have a cost center under `Cost and Billing`.
3.2 A project has to have a customer under `Customer Details`.
3.3 In the shop masters, each shop can have its own `BOM`, `MATERIAL REQUEST`
3.4 A project Has its own `Expense claims among other` such as

```ts
    Project
    Task
    Timesheet
    Issue
    Project Update
    Material
    Material Request
    BOM
    Stock Entry
    Sales
    Sales Order
    Delivery Note
    Sales Invoice
    Purchase
    Purchase Order
    Purchase Receipt
    Purchase Invoice
    Claims
    Expense Claims
```

## 4. COST CENTERS

- TO create a cost center, you have to go to `Accounting/Cost Center` tab/ shortcut to create a new cost center.
  - `NOTE` You can attach an employee to a cost center.

## 5. ITEMS

- Each Item from the Item Dashboard has multiple convolusions such as

```ts
      Groups
      BOM
      Product Bundle
      Item Alternative
      Pricing
      Item Price
      Pricing Rule
      Sell
      Quotation
      Sales Order
      Delivery Note
      Sales Invoice
      Buy
      Material Request
      Supplier Quotation
      Request for Quotation
      Purchase Order
      Purchase Receipt
      Purchase Invoice
      Manufacture
      Production Plan
      Work Order
      Item Manufacturer
      Traceability
      Serial No
      Batch
      Stock Movement
      Stock Entry
      Stock Reconciliation
```

## 6. STOCK

- Everything associated with stocks from stock entries to stock records are located in this section.
- For efficient stock movement purposes, each shop must have its own `warehouse` for purposes best known to man...

## 7. ASSETS

- For an asset to exist, it has to have the following:
  - `A location`. If one is not set, you have to create one for that Item within the system.
  - `The Asset as an Item`. It has to be an item.
  -
