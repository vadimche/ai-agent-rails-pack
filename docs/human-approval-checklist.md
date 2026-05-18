# Human Approval Checklist

Use this before approving agent-generated changes.

## Intent

- [ ] The change solves the stated problem.
- [ ] The change does not include unrelated work.
- [ ] The behavior change is understandable.

## Architecture

- [ ] Existing boundaries are respected.
- [ ] No duplicate implementation was introduced.
- [ ] Naming and structure match the repository style.

## Risk

- [ ] Critical invariants are preserved.
- [ ] Sensitive areas were explicitly approved.
- [ ] Rollback path is clear.

## Tests

- [ ] Relevant automated tests were added/updated, or a clear reason is given.
- [ ] Manual verification steps are listed.
- [ ] Test output or command results are included.

## Final decision

- [ ] Approve
- [ ] Request changes
- [ ] Split into smaller task
- [ ] Reject
