# Validation Results and Limitations

**Evidence basis:** Limited synthetic-data MVP testing documented through October 18, 2026. Results below are historical observations, not new tests performed for this public portfolio.

## Recorded results

| Area | Recorded observation | Interpretation |
|---|---|---|
| Invoice extraction | 19 of 20 sampled fields correct (95%); one vendor over-extraction required human correction | Small synthetic sample; not a generalized accuracy estimate |
| Valid integrations | Four of four attempted valid integrations succeeded in the earlier evaluation | Does not establish reliability at operational scale |
| Automation duration | Four Power Automate runs of 19, 25, 13 and 14 seconds; mean 17.75 seconds | Automation segment only, **not** end-to-end approval time |
| Current-configuration tests | U7-R01 through U7-R10 covered configuration inspection, intake, approval, duplicate guard, rejection, resubmission, required-field and department-code blocks, upstream missing-date handling, and limited authorization denial | Mixed inspections and scenarios; **not ten independent end-to-end invoice transactions** |

## Representative test outcomes

- A synthetic invoice created a structured Freshservice request with supporting PDFs and demonstration coding.
- Native approval, activity history, and test-agent reassignment were observed after an authorized approval.
- Repeated requests did not create a second native approval while the first remained requested in the tested case.
- Rejection and subsequent correction/resubmission were exercised.
- Missing justification and invalid demonstration department code blocked new approval initiation.
- A missing invoice date followed the upstream exception path rather than normal intake.
- A non-designated test account was denied the tested sign-in and email-approval paths. This does not establish comprehensive authorization coverage.

## Known issues

- One rejection-related activity label was confusing despite the recorded rejection outcome.
- An approval email subject contained an unresolved amount placeholder; the email body showed the amount.
- Missing-field exception notes were generic rather than identifying every missing field.

## Not established

No production deployment, Finance-led acceptance, real Purchasing handoff, accounting/payment integration, comprehensive security assessment, load/reliability testing, enterprise authorization coverage, quantified savings, backlog reduction, or complete approval elapsed time was validated. Broader evaluation would require additional representative cases, operational ownership, and formal business acceptance.

## Evaluation conclusion

The observed tests support the feasibility of the documented MVP workflow under limited conditions. They do not prove production readiness or organizational benefit. Human review, controlled deployment, and additional validation remain essential.
