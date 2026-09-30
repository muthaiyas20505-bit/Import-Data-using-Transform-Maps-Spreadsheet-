# Project Documentation

## Import Data using Transform Maps (Spreadsheet)

### Description

This micro project focuses on importing structured data from an external spreadsheet into the ServiceNow platform using Import Sets and Transform Maps. The spreadsheet is loaded into an Import Set table, which acts as a staging area. A Transform Map then maps source fields to the appropriate target table fields. After transformation, records are created in the target table and validated.

### Phase 1 — Prepare the Spreadsheet

1. Create a new Google Spreadsheet.
2. Enter the sample employee data.
3. Download the spreadsheet in `.xlsx` format.

### Phase 2 — Create the Custom Table

Create a custom table:

- Label: `Employee Test`
- Name: `u_employee_test`

Add these fields:

| Field | Type |
|---|---|
| Employee ID | String |
| Employee Name | String |
| Email | String |
| Department | String |
| Location | String |

### Phase 3 — Create the Import Set Table

Navigate to **Load Data** and create/load an import table.

- Label: `Employee Import`
- Name: `u_employee_import`

After submission, use **Create Transform Map**.

### Phase 4 — Create the Transform Map

Create:

- Name: `Sample Spreadsheet Import`
- Source Table: `Employee Import`
- Target Table: `Employee Test`

Use **Auto Map Matching fields** where appropriate and **Mapping Assist** to map the source and target fields.

Save the Transform Map and run the transformation.

### Phase 5 — Transform and Validate

Open the Employee Test table and verify that the imported records were created successfully.

The project report states that the records are successfully imported into ServiceNow using the Import Set and Transform Map.

### Phase 6 — Enable Coalesce

Coalesce is used to avoid duplicate records when the same employee data is imported multiple times.

Open the `Sample Spreadsheet Import` Transform Map and, under Field Maps, set the appropriate employee identifier field to **Coalesce = True**.

Save the Transform Map.

### Phase 7 — Insert New Excel Data

Load another Excel file into the existing `Employee Import` table.

- Import set table: Existing table — `Employee Import`
- Source: File
- Sheet number: `1`
- Header row: `1`

Run the transform using the existing Transform Map.

The project report demonstrates that repeated employee IDs can result in updates while new employee IDs are inserted. When the same sheet is uploaded again without changes, the report records the rows as ignored.

### Phase 8 — Create Reports

#### Employees by Department

- Report name: `Employees by Department`
- Table: `Employee Test`
- Type: Pie Chart
- Group By: Department
- Aggregation: Count

#### Employees by Location

- Report name: `Employees by Location`
- Table: `Employee Test`
- Type: Bar Chart
- Group By: Location
- Aggregation: Count

#### Employee List Report

- Report name: `Employee List Report`
- Table: `Employee Test`
- Type: List
- Columns:
  - Employee ID
  - Employee Name
  - Email
  - Department
  - Location

### Phase 9 — Add Reports to Dashboard

Create the dashboard:

`Employee Analytics Dashboards`

Add all three reports to the dashboard:

1. Employees by Department
2. Employees by Location
3. Employee List Report

The project report also notes that users, groups, and roles can be restricted through sharing options.

## Conclusion

The project implements an employee data management workflow using ServiceNow Import Sets and Transform Maps. Coalesce helps identify existing employee records so repeated imports can update records rather than creating redundant entries. Reports and a dashboard provide centralized visibility into employee data.

## Source

This documentation is based on the uploaded project report:

`Import Data using Transform Maps.pdf`
