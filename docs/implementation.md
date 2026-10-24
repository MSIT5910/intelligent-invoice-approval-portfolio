# Implementation and Architecture

## Business workflow

The solution addresses repeated manual invoice entry, approval requests, supporting-form preparation, and reconciliation of email responses with service requests. It structures the approval record without replacing human financial judgment.

## Implemented reference stack

| Responsibility | Demonstrated component | Adaptation considerations |
|---|---|---|
| Invoice intake | Outlook / Exchange | Another approved mailbox or intake service could be used with a different connector |
| Orchestration and extraction | Power Automate + AI Builder | A replacement must support attachment processing, extraction, validation, error handling, and secure access |
| Human review | Outlook draft | Alternative review interfaces require workflow and usability validation |
| Request tracking and approval | Freshservice ESM | Another ESM platform requires new field mapping, approval logic, authorization checks, and audit review |

These alternatives are architectural possibilities, **not implemented or tested integrations**.

## Observed processing stages

1. Power Automate receives an email and checks attachments for a PDF invoice.
2. AI Builder extracts fields. A required-value gate checks vendor name, invoice date, invoice total, and invoice identifier. Missing values follow an exception path.
3. The workflow prepares a structured Outlook draft for human review, including supporting PDFs and structured data for downstream intake.
4. Freshservice email intake maps the information into a structured request.
5. An approval workflow checks eight downstream fields: invoice number, amount, date, due date, expense code, department code, project code, and business justification. The demonstration also requires department code `120`.
6. A duplicate-request guard prevents initiating another native approval while one is already requested. A designated test approver can approve or reject. Rejected requests can be corrected and resubmitted.
7. Successful approval produces a private note and reassignment to a **test agent**. Actual Purchasing handoff is not implemented.

## Engineering and control boundaries

- Fixed demonstration accounting values are not validated financial classifications.
- Human review and approval are retained deliberately.
- The original invoice and structured fields support review, but extraction accuracy is not guaranteed.
- Exception and rejection paths are part of the tested workflow; comprehensive operational recovery and alerting remain future work.
- The approval workflow is configured for a designated test approver rather than dynamic enterprise approver selection.
- A separate Payment Request Form could only be retired after Finance approval of an equivalent controlled process.

## Deployment considerations

Before adoption, configure an organization-approved tenant, connectors, mailbox permissions, service account ownership, ESM fields, approval roles, retention rules, monitoring, exception routing, and support procedures. Test with approved representative data and complete Finance, privacy, and security review. This repository does not contain an importable production package.
