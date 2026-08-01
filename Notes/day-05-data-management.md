# Day 05 — Data Management in Salesforce

## Learning Objectives
- Data Management
- Data Import Wizard
- Data Loader
- Export Data
- Validation Rules
- Matching Rules
- Duplicate Rules
- External IDs

## What is Data Management?
Data management is the process of importing, exporting, updating, deleting and maintaining Salesforce data.

## Data Import Wizard
- Browser based
- Uses CSV files
- Good for small and medium imports
- No installation required

## Data Loader
- Desktop application
- Supports Insert, Update, Upsert, Delete, Export and Export All
- Suitable for bulk operations

## Import Wizard vs Data Loader

| Feature | Import Wizard | Data Loader |
|---|---|---|
| Interface | Web | Desktop |
| Large Data | No | Yes |
| Export | No | Yes |
| Delete | No | Yes |
| Upsert | Limited | Yes |

## CSV Example

```csv
Name,Email
John,john@example.com
```

## External ID
Used to uniquely identify records from external systems and supports Upsert.

## Validation Rules
Prevent invalid data from being saved.

Example:
Amount cannot be less than zero.

## Matching Rules
Define how duplicate records are detected.

## Duplicate Rules
Control whether duplicates are allowed, warned or blocked.

## Interview Questions
1. What is Data Management?
2. What is Data Import Wizard?
3. What is Data Loader?
4. Difference between Import Wizard and Data Loader?
5. What is Upsert?
6. What is External ID?
7. What is a Validation Rule?
8. What are Matching Rules?
9. What are Duplicate Rules?
10. Which tool is used for bulk imports?

## Practical Tasks
- Explore Data Import Wizard
- Explore Data Loader
- Create a sample CSV
- Review Validation Rules
- Review Matching Rules
- Review Duplicate Rules

## Day 05 Status
- [x] Data Management learned
- [x] Import Wizard explored
- [x] Data Loader understood
- [x] Validation Rules studied
- [x] Duplicate Management studied
