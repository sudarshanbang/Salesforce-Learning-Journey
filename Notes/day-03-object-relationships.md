# Day 03 — Object Relationships and Schema Builder

## Learning Objectives

On Day 3, I learned:

- Lookup relationships
- Master-Detail relationships
- Parent and child objects
- Roll-Up Summary fields
- Formula fields
- Schema Builder
- Relationship design for the Expense Manager project

---

## 1. Object Relationships

An object relationship connects one Salesforce object to another.

Example:

```text
Expense → Expense Category
```

In this relationship:

- `Expense Category` is the parent object.
- `Expense` is the child object.
- One category can have many expense records.

---

## 2. Lookup Relationship

A Lookup relationship creates a loose connection between two objects.

### Key Points

- Parent and child can exist independently.
- The relationship can be optional or required.
- Parent and child keep separate ownership and security.
- Deleting the parent does not normally delete the child.
- Native Roll-Up Summary fields are not supported.

### Expense Manager Example

```text
Expense__c → Expense_Category__c
```

The Expense object uses a Lookup relationship with Expense Category because expense records should not be deleted when a category is removed.

---

## 3. Master-Detail Relationship

A Master-Detail relationship creates a strong parent-child connection.

### Key Points

- The detail record cannot exist without the master.
- The master controls access to the detail record.
- Deleting the master deletes related detail records.
- Roll-Up Summary fields are supported.
- The relationship field is always required.

### Expense Manager Example

```text
Budget__c → Budget_Item__c
```

A Budget Item has no purpose without its related Budget.

---

## 4. Lookup vs Master-Detail

| Feature | Lookup | Master-Detail |
|---|---|---|
| Connection | Loose | Strong |
| Parent required | Optional or required | Required |
| Ownership | Independent | Controlled by master |
| Security | Independent | Inherited from master |
| Cascade delete | Normally no | Yes |
| Roll-Up Summary | No | Yes |
| Child can exist alone | Yes | No |

---

## 5. Roll-Up Summary Field

A Roll-Up Summary field calculates values from related detail records and displays the result on the master record.

Supported operations:

```text
COUNT
SUM
MIN
MAX
```

### Expense Manager Example

The `Total_Allocated__c` field on Budget calculates the total allocated amount from related Budget Item records.

```text
SUM(Budget_Item__c.Allocated_Amount__c)
```

---

## 6. Formula Field

The Remaining Budget field calculates how much budget is still available.

```text
Budget_Amount__c - Total_Allocated__c
```

Expected API name:

```text
Remaining_Budget__c
```

---

## 7. Expense Manager Relationship Model

```text
Expense Category
       |
       | Lookup
       v
    Expense


Budget
   |
   | Master-Detail
   v
Budget Item
   |
   | Lookup
   v
Expense Category
```

---

## 8. Metadata-Style Field Definitions

These examples document the fields created in Salesforce.

### Expense Category Lookup on Expense

```xml
<fields>
    <fullName>Expense_Category__c</fullName>
    <label>Expense Category</label>
    <referenceTo>Expense_Category__c</referenceTo>
    <relationshipLabel>Expenses</relationshipLabel>
    <relationshipName>Expenses</relationshipName>
    <required>true</required>
    <type>Lookup</type>
</fields>
```

### Budget Master-Detail Field on Budget Item

```xml
<fields>
    <fullName>Budget__c</fullName>
    <label>Budget</label>
    <referenceTo>Budget__c</referenceTo>
    <relationshipLabel>Budget Items</relationshipLabel>
    <relationshipName>Budget_Items</relationshipName>
    <reparentableMasterDetail>false</reparentableMasterDetail>
    <type>MasterDetail</type>
    <writeRequiresMasterRead>false</writeRequiresMasterRead>
</fields>
```

### Expense Category Lookup on Budget Item

```xml
<fields>
    <fullName>Expense_Category__c</fullName>
    <label>Expense Category</label>
    <referenceTo>Expense_Category__c</referenceTo>
    <relationshipLabel>Budget Items</relationshipLabel>
    <relationshipName>Budget_Items</relationshipName>
    <required>true</required>
    <type>Lookup</type>
</fields>
```

### Allocated Amount Field

```xml
<fields>
    <fullName>Allocated_Amount__c</fullName>
    <label>Allocated Amount</label>
    <precision>16</precision>
    <scale>2</scale>
    <type>Currency</type>
</fields>
```

### Total Allocated Roll-Up Summary Field

```xml
<fields>
    <fullName>Total_Allocated__c</fullName>
    <label>Total Allocated</label>
    <summaryForeignKey>Budget_Item__c.Budget__c</summaryForeignKey>
    <summaryOperation>sum</summaryOperation>
    <summaryField>Budget_Item__c.Allocated_Amount__c</summaryField>
    <type>Summary</type>
</fields>
```

### Remaining Budget Formula Field

```xml
<fields>
    <fullName>Remaining_Budget__c</fullName>
    <formula>Budget_Amount__c - Total_Allocated__c</formula>
    <formulaTreatBlanksAs>BlankAsZero</formulaTreatBlanksAs>
    <label>Remaining Budget</label>
    <precision>16</precision>
    <scale>2</scale>
    <type>Currency</type>
</fields>
```

---

## 9. SOQL Practice

### Query Expenses with Categories

```sql
SELECT
    Id,
    Name,
    Amount__c,
    Expense_Date__c,
    Expense_Category__r.Name
FROM Expense__c
ORDER BY Expense_Date__c DESC
```

### Query Budget Items with Budget and Category

```sql
SELECT
    Id,
    Name,
    Allocated_Amount__c,
    Budget__r.Name,
    Expense_Category__r.Name
FROM Budget_Item__c
ORDER BY Allocated_Amount__c DESC
```

### Query Budget Calculations

```sql
SELECT
    Id,
    Name,
    Budget_Amount__c,
    Total_Allocated__c,
    Remaining_Budget__c
FROM Budget__c
```

### Parent-to-Child Query

```sql
SELECT
    Id,
    Name,
    Budget_Amount__c,
    (
        SELECT
            Id,
            Name,
            Allocated_Amount__c
        FROM Budget_Items__r
    )
FROM Budget__c
```

---

## 10. Sample Data

### Budget

```text
Budget Name: July 2026 Budget
Budget Amount: ₹20,000
Status: Active
```

### Budget Items

| Category | Allocated Amount |
|---|---:|
| Food | ₹5,000 |
| Petrol | ₹3,000 |
| Travel | ₹2,000 |

### Expected Result

```text
Total Allocated: ₹10,000
Remaining Budget: ₹10,000
```

---

## 11. Practical Tasks Completed

- Created Expense Category Lookup on Expense
- Created Budget Item custom object
- Created Budget Master-Detail field on Budget Item
- Created Expense Category Lookup on Budget Item
- Created Allocated Amount field
- Created Total Allocated Roll-Up Summary field
- Created Remaining Budget Formula field
- Added sample Budget and Budget Item records
- Verified calculations
- Viewed relationships in Schema Builder
- Practised relationship-based SOQL queries

---

## 12. Interview Questions

### What is a Lookup relationship?

A Lookup relationship creates a loose connection between two objects while allowing both records to maintain independent ownership and security.

### What is a Master-Detail relationship?

A Master-Detail relationship creates a strong parent-child connection in which the master controls the detail record's lifecycle, security, and ownership.

### Can a detail record exist without a master?

No. A detail record requires a related master record.

### What happens when a master record is deleted?

Its related detail records are also deleted.

### What is a Roll-Up Summary field?

A Roll-Up Summary field calculates values from related detail records and displays the result on the master record.

### Which relationship supports native Roll-Up Summary fields?

Master-Detail relationships.

### What is a junction object?

A junction object connects two objects to create a many-to-many relationship.

### Why was Lookup used between Expense and Expense Category?

Lookup keeps Expense records independent and prevents category deletion from automatically deleting historical expense data.

---

## 13. Key Takeaways

- Lookup is suitable for loosely connected records.
- Master-Detail is suitable for dependent records.
- Roll-Up Summary fields require Master-Detail.
- Relationship design affects deletion, security, reporting, and automation.
- Poor relationship design can cause accidental data loss.
- Schema Builder helps visualise the complete Salesforce data model.

---

## Day 03 Status

- [x] Lookup relationship studied
- [x] Master-Detail relationship studied
- [x] Budget Item object created
- [x] Relationships implemented
- [x] Roll-Up Summary field created
- [x] Formula field created
- [x] Sample records created
- [x] SOQL queries practised
- [x] Schema Builder reviewed
