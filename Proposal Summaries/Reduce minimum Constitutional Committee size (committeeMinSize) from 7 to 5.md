# Reduce Minimum Constitutional Committee Size (`committeeMinSize`) from 7 to 5

## Understanding the "Safety Buffer" Proposal

To understand why this change is being made, focus on the three numbers that control how the Constitutional Committee (CC) works:

1. **Current committee size (7 members)**  
   This is the actual group elected by the community to review proposals. Right now, there are **7 seats**.

2. **Minimum size / operational floor (currently 7, proposed 5)**  
   This is a protocol liveness rule. If active members fall below this floor, the committee is considered **non-operational** and cannot vote.

3. **Voting threshold (66.7%)**  
   This is the passing requirement. A proposal needs at least **66.7% "Yes" votes** from current active members.

---

## Concise Beginner Explanation

### The Problem

The operational floor is currently set to `7`, the same as the full committee size.  
That means there is **zero buffer**: if even one member resigns or becomes unavailable, committee voting can halt until replacements are elected.

### The Proposed Change

Lower the operational floor to `5`.

- With 7 total members, up to **2 members** can be unavailable and the committee still remains operational.
- This prevents governance freezes and gives the community time to run a proper election process instead of rushing an emergency replacement.

### Does This Make Passing Proposals Easier?

Not in a meaningful way. The **66.7% threshold** still protects decision quality.

```text
required_yes_votes = ceil(active_members * 0.667)
```

- **7 active members** -> **5 Yes** votes required
- **6 active members** -> **5 Yes** votes required
- **5 active members** -> **4 Yes** votes required

### Bottom Line

This proposal is mainly about **liveness and resilience**, not lowering governance standards.  
It helps ensure the CC does not shut down due to normal member turnover or temporary unavailability.