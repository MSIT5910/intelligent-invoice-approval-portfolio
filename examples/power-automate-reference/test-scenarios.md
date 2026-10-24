# Proposed reference-code test scenarios

**Status: NOT EXECUTED.** These are proposed tests for future use, not capstone test results.

| ID | Scenario | Expected design behavior | Status |
|---|---|---|---|
| REF-01 | Valid synthetic invoice | Normalize and construct routing recommendation | Not run |
| REF-02 | Missing vendor name | Build exception record | Not run |
| REF-03 | Negative amount | Build exception record | Not run |
| REF-04 | Unsupported currency | Build exception record | Not run |
| REF-05 | Duplicate invoice ID | Not supported without durable storage | Not run |
| REF-06 | Unauthorized approver | Not supported without identity/ESM integration | Not run |
| REF-07 | Human rejection | Not supported; sample approval JSON is illustrative only | Not run |
| REF-08 | Purchasing handoff | Not supported without integration | Not run |

This reference must not be cited as evidence of executed testing or functional deployment.
