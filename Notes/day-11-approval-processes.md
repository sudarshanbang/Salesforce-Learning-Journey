# Day 11 — Approval Processes in Salesforce

## Learning Objectives
- Approval Processes
- Entry Criteria
- Approval Steps
- Approvers
- Initial Submission Actions
- Approval and Rejection Actions
- Final Approval and Rejection Actions
- Recall Actions
- Record Locking
- Approval History
- Email Alerts
- Approval Process vs Flow

## What is an Approval Process?
An Approval Process automates how Salesforce records are submitted, reviewed, approved, or rejected.

```text
Record → Submit → Entry Criteria → Approval Step → Approver → Approved/Rejected → Final Actions
```

## Entry Criteria
Entry Criteria determine whether a record is eligible for the Approval Process.

Example:
```text
Discount > 20%
```

## Approval Steps
Approval Steps determine who reviews the record and under what conditions.

Example:
```text
Manager → Director → Finance
```

## Initial Submission Actions
Actions performed when a record enters the Approval Process.

Examples:
- Field Update
- Email Alert
- Task
- Outbound Message

## Approval Actions
Actions executed when an approval step is approved.

## Rejection Actions
Actions executed when an approval request is rejected.

## Final Approval Actions
Actions executed after all required approval steps are completed successfully.

## Final Rejection Actions
Actions executed when the record reaches final rejection.

## Recall Actions
Actions executed when an approval request is recalled.

## Record Locking
Records can be locked while approval is pending to prevent inappropriate changes.

## Approval History
Approval History tracks submission, approvers, decisions, comments, and status.

## Approval Process vs Flow

| Approval Process | Flow |
|---|---|
| Specialized for formal approvals | General automation platform |
| Approval/rejection lifecycle | Broad business-process automation |
| Approval steps and approvers | Flow elements and logic |
| Approval history | Different execution/debugging tools |

## Example
```text
Opportunity
    ↓
Discount > 20%
    ↓
Submit for Approval
    ↓
Sales Manager
   /       \
Approve   Reject
```

## Practical Tasks
- [ ] Explore Approval Processes in Setup
- [ ] Create a simple test Approval Process
- [ ] Define Entry Criteria
- [ ] Configure an Approver
- [ ] Configure submission actions
- [ ] Configure approval/rejection actions
- [ ] Submit a test record
- [ ] Approve a test request
- [ ] Reject a test request
- [ ] Review Approval History

## Interview Questions
1. What is an Approval Process?
2. What are Entry Criteria?
3. What is an Approval Step?
4. What are Initial Submission Actions?
5. What are Final Approval Actions?
6. What are Final Rejection Actions?
7. What is record locking?
8. What is Approval History?
9. What is a Recall Action?
10. What is the difference between Flow and Approval Process?

## Scenario Questions
### Scenario 1
Discount greater than 20% requires manager approval.

**Solution:** Approval Process with entry criteria based on Discount.

### Scenario 2
Status must become Approved after final approval.

**Solution:** Configure a Final Approval field update.

### Scenario 3
The owner must receive an email after rejection.

**Solution:** Configure an Email Alert as a rejection/final rejection action.

## Best Practices
- Define clear entry criteria.
- Keep approval chains as simple as possible.
- Use meaningful process and step names.
- Test approval and rejection paths.
- Verify record locking.
- Document the business reason for each approval step.

## Key Takeaways
- Approval Processes automate formal approvals.
- Entry Criteria control eligibility.
- Approval Steps determine reviewers.
- Actions automate the approval lifecycle.
- Approval History provides an audit trail.
- Approval Process and Flow are not interchangeable.

## Day 11 Status
Change these to `[x]` only after actually completing them:

- [ ] Approval Process studied
- [ ] Entry Criteria practiced
- [ ] Approval Steps practiced
- [ ] Approval/Rejection actions practiced
- [ ] Record locking understood
- [ ] Approval History reviewed
- [ ] Test approval request completed
- [ ] Interview questions revised
