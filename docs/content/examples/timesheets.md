+++
title = "Timesheets & Billing"
description = "A chore, simplified."
weight = 1
+++

Barney runs a consulting business. Let's say they are lawyers or do software. The business flourishes. Clients really like the highly qualified staff and the way they come up with simple practial solutions, so the projects keep rolling in. They are usually time & materials: Employees or subcontractors log hours against client projects. The clients are invoiced. When working with subcontractors, Barney is billed by them and pays them.

This is currently done with spreadsheets.

> Every week the same thing. I have to chase everybody to get their hours in. Then the fun begins - duplicate submissions, Time logged against inactive projects, Excess hours for which we don't have change requests, 

Business is booming and the process is getting just a little bit unmanageable ...

> "I have to dig around way too much to figure out whether we have invoiced a client for a timesheet entry and whether we have received payment."

Managing subcontractors is also challenging ..

> They email their invoices. Comparing submitted timesheets to the hours they billed for in any given period is time consuming.

# Solution

Barney decides to build a timesheets & billing system which he can use in-house initially and then turn into an SAAS project.

- Users can register.
- Users can invite other users as either admins or consultants.
- Admins can create clients and projects
- Consultants (aka "contributors") can log hours against projects.
- Admins can mark timesheet entries as having been invoiced to the client.
- When billed by a subcontractor, admins can mark timesheet entries as having been billed for by a subcontractor.
- After the contractor has been paid, timesheet entries are marked as paid to contractor.
- When clients pay their invoices, timesheet entries are marked as paid by client.
- Barney can get statements of account for clients and contractors which show amounts billed/invoiced and paid (or received).
- There are accounts receivable and accounts payable reports. 

Here's an event storming for phase 1 of the project:

```
# Timesheets & Billing
Register -> // contributorId, email
contributor Registered // contributorId, email
Add Project -> // projectId, name
Project Added // projectId, name
Project List* // projectId, name
Create Timesheet-> // timesheetId, contributorId
Timesheet Created // timesheetId, contributorId
Log Timesheet Entry-> // timesheetId, timesheetEntryId, projectId, date, hours, isBillable, description
Timesheet Entry Logged // timesheetId, timesheetEntryId, projectId, date, hours, isBillable, description
Submit Timesheet -> // timesheetId, isSubmitted
Timesheet Submitted // timesheetId, isSubmitted
Timesheets* // timesheetId, timesheetEntryId, contributorId, projectId, date, hours, isBillable, description, isSubmitted

Update Timesheet Entry ->  // timesheetId, timesheetEntryId, projectId, date, hours, isBillable, description
Timesheet Entry Updated //  timesheetId, timesheetEntryId, projectId, date, hours, isBillable, description

Delete Timesheet Entry -> // timesheetId, timesheetEntryId
Timesheet Entry Deleted // timesheetId, timesheetEntryId

Delete Timesheet -> // timesheetId
Timesheet Deleted // timesheetId

Remove Project -> // projectId
Project Removed // projectId
```
