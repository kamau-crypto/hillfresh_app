# Managing Truck Odometer Readings and Maintenance in ERPNext

In ERPNext, you can manage truck (asset) odometer readings and maintenance without creating custom doctypes by leveraging several built-in features:

1. Asset Maintenance (Core Feature)
   ERPNext has a built-in Asset Maintenance system that's perfect for tracking truck servicing:

Navigation: Assets > Asset Maintenance

Features:

Schedule periodic maintenance tasks

Track maintenance history

Assign maintenance team

Record maintenance costs

How to set up:
Create an Asset Maintenance record for your truck

Define maintenance tasks (oil change, tire rotation, etc.)

Set maintenance schedules (time-based or usage-based)

2. Asset Maintenance Log
   Each maintenance occurrence is recorded in an Asset Maintenance Log:

Automatically created from scheduled maintenance

Can be manually created for ad-hoc maintenance

Tracks:

Maintenance date

Tasks performed

Parts replaced

Service provider

Costs

3. Tracking Odometer Readings
   For odometer tracking, you have two good options:

Option A: Use Custom Fields on Maintenance Logs
Add a custom field "Odometer Reading" to the Asset Maintenance Log doctype

Go to: Customize Form > Asset Maintenance Log

Add Float field "Odometer Reading"

Update this field during each maintenance log entry

Option B: Use Asset Value Adjustment (for historical tracking)
Create periodic Asset Value Adjustment records

Use the "Current Odometer Reading" field in the notes/comments

This creates an audit trail of readings over time

4. Linking to Deliveries
   To connect truck usage with deliveries:

Add a custom field "Truck" (Link to Asset) in the Delivery Note doctype

When creating deliveries, select the truck used

Add odometer readings in the delivery note comments

5. Reporting
   Use built-in reports:

Asset Maintenance History: Shows all maintenance for a truck

Asset Depreciation Ledger: Can be adapted to show usage metrics

Custom Reports: Create using Report Builder with fields like:

Delivery date

Truck (asset) used

Odometer reading

Maintenance performed

Best Practice Implementation:
For each truck:

Create a detailed Asset record

Set up maintenance schedule (every 10,000 km or 3 months, etc.)

For each delivery:

Record the truck used

Update odometer reading (manually or via mobile app)

For maintenance:

Create maintenance logs automatically when thresholds are reached

Record all service details and parts replaced

This approach gives you comprehensive tracking without custom doctypes, using ERPNext's built-in asset management capabilities.
