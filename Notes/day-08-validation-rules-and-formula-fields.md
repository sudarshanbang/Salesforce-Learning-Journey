# Day 08 — Validation Rules & Formula Fields

## Learning Objectives

Today I learned:

- Validation Rules
- Formula Fields
- Operators
- Functions
- Error Messages
- Error Locations
- Business Logic
- Best Practices

---

# 1. What is a Validation Rule?

A Validation Rule prevents users from saving invalid data.

It checks whether data meets business requirements before saving.

---

# 2. Why Use Validation Rules?

- Improve data quality
- Prevent incorrect data
- Enforce business rules
- Reduce manual checking

---

# 3. Validation Rule Structure

IF Condition = TRUE

➡ Record cannot be saved.

---

# 4. Formula Fields

Formula Fields automatically calculate values using other fields.

Example:

```text
Quantity × Price = Total Amount
```

Formula fields are read-only.

---

# 5. Common Operators

- =
- <>
- >
- <
- >=
- <=
- &&
- ||
- !

---

# 6. Common Functions

- IF()
- AND()
- OR()
- NOT()
- ISBLANK()
- ISPICKVAL()
- TODAY()
- NOW()
- TEXT()

---

# 7. Example Validation Rules

## Email Required

```text
ISBLANK(Email)
```

## Amount Must Be Positive

```text
Amount__c < 0
```

## Picklist Validation

```text
ISPICKVAL(Status__c,"Closed")
```

---

# 8. Error Message

Every Validation Rule should provide a clear error message.

Bad:
- Invalid Data

Good:
- Amount cannot be negative.

---

# 9. Error Location

- Top of Page
- Field

Prefer field-level errors whenever possible.

---

# Best Practices

- Keep formulas simple.
- Write meaningful error messages.
- Avoid duplicate validation rules.
- Test before deployment.

---

# Interview Questions

1. What is a Validation Rule?
2. Why use Validation Rules?
3. What is a Formula Field?
4. Difference between Formula Field and Validation Rule?
5. What does ISBLANK() do?
6. What is ISPICKVAL()?
7. Can Formula Fields be edited?
8. What are error locations?
9. Why should error messages be meaningful?
10. Name five formula functions.

---

# Practical Tasks

- Create a Formula Field
- Create a Validation Rule
- Test valid data
- Test invalid data
- Modify error messages

---

# Key Takeaways

- Validation Rules improve data quality.
- Formula Fields calculate values automatically.
- Error messages should help users fix problems.
- Keep formulas readable and maintainable.

## Day 08 Status

- [x] Validation Rules studied
- [x] Formula Fields studied
- [x] Functions practiced
- [x] Interview questions completed
