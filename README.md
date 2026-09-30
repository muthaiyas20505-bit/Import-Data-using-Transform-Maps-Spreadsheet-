# ServiceNow Import Data using Transform Maps

## Project Overview

This micro project demonstrates importing structured employee data from an external spreadsheet into the ServiceNow platform using **Import Sets** and **Transform Maps**.

The project simulates a real-world scenario where bulk employee data is received in Excel format and migrated into ServiceNow. The spreadsheet data is loaded into an Import Set table, mapped to a custom Employee Test table, transformed, and validated.

## Objectives

- Import employee data from an Excel spreadsheet.
- Create a custom ServiceNow Employee Test table.
- Use an Import Set table as a staging area.
- Create and configure a Transform Map.
- Map source fields to target fields.
- Use Coalesce to prevent duplicate employee records.
- Verify inserted and updated records through Transform History.
- Create reports for employee data.
- Add reports to an Employee Analytics Dashboard.

## ServiceNow Configuration

### Target Table
- Label: `Employee Test`
- Name: `u_employee_test`

### Employee Fields
- Employee ID
- Employee Name
- Email
- Department
- Location

### Import Set Table
- Label: `Employee Import`
- Name: `u_employee_import`

### Transform Map
- Name: `Sample Spreadsheet Import`
- Source Table: `Employee Import`
- Target Table: `Employee Test`

### Coalesce
Coalesce is enabled on an employee field so that existing employee records can be updated instead of creating duplicate records during repeated imports.

## Import Workflow

```text
Excel Spreadsheet
       |
       v
   Load Data
       |
       v
 Import Set Table
       |
       v
 Transform Map
       |
       v
 Field Mapping
       |
       v
    Transform
       |
       v
 Employee Test Table
       |
       +----> Transform History
       |
       +----> Reports
                  |
                  v
          Employee Analytics Dashboard
```

## Reports Created

### 1. Employees by Department
- Table: Employee Test
- Chart: Pie Chart
- Group By: Department
- Aggregation: Count

### 2. Employees by Location
- Table: Employee Test
- Chart: Bar Chart
- Group By: Location
- Aggregation: Count

### 3. Employee List Report
- Table: Employee Test
- Type: List
- Columns:
  - Employee ID
  - Employee Name
  - Email
  - Department
  - Location

## Dashboard

Dashboard name:

`Employee Analytics Dashboards`

The dashboard contains the three reports:
- Employees by Department
- Employees by Location
- Employee List Report

## Repository Contents

- `README.md` - Project overview and implementation guide
- `data/sample_employee_data.csv` - Sample spreadsheet-style employee data
- `docs/project-report.md` - Detailed project documentation based on the project report
- `Import Data using Transform Maps.pdf` - Original project report

## How to Reproduce

1. Create the `Employee Test` custom table in ServiceNow.
2. Add the required employee fields.
3. Use **Load Data** to create/load the `Employee Import` Import Set table.
4. Create the `Sample Spreadsheet Import` Transform Map.
5. Map the source fields to the Employee Test target fields.
6. Enable Coalesce on the chosen employee identifier field.
7. Run the transformation.
8. Check Transform History for inserted, updated, or ignored records.
9. Create the three reports.
10. Create `Employee Analytics Dashboards`.
11. Add the reports to the dashboard.
12. Validate the final employee records and dashboard.

## Result

The project demonstrates an end-to-end employee data import process in ServiceNow using Import Sets and Transform Maps, with duplicate prevention through Coalesce and visual reporting through Reports and Dashboards.

## Technologies

- ServiceNow
- Import Sets
- Transform Maps
- Coalesce
- ServiceNow Reports
- ServiceNow Dashboards
- Excel / Spreadsheet data
