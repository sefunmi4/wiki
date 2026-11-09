Operational Lessons Learned & Risk Mitigation

Infrastructure & Cloud Cost Governance

AWS Sandbox Infrastructure Audit & Cost Resolution — November 2026

* Incident: Recurring unmonitored AWS charges were identified from legacy infrastructure used during the initial full-stack testing phase. The recurring baseline was approximately $12.99/month, representing approximately $155.88 in annualized avoidable spend if left running.
* Root Cause: Legacy EC2/EBS test infrastructure and associated VPC/network resources remained active after local database and testing workflows had migrated to alternative infrastructure, including GitHub-based data integration.
* Financial Impact: The stale AWS infrastructure was responsible for an identified recurring cost that was subsequently eliminated. Approximately 100% of the identified stale recurring AWS cost was removed.
* October Financial Context: The October operating-expense ledger recorded $12.59 in AWS spending. Total listed October operating expenses were $53.54, meaning AWS represented approximately 23.5% of the month’s listed operating expenses.
* November Cleanup Context: Before final cleanup, the identified November baseline consisted of approximately $1.50 in Compute and $0.66 in VPC-related costs, or $2.16 combined. Against the reported $3.11 month-to-date baseline, those identified infrastructure categories represented approximately 69.5% of the baseline.

Resolution

1. Terminated all active EC2 test instances.
2. Removed unattached Elastic IP resources.
3. Deleted the default VPC (vpc-0b6bcff3a70897798) and its seven dependent network resources in the N. Virginia region.
4. Verified zero active EC2 instances, volumes, VPCs, and Elastic IPs remaining across the audited regions.
5. Verified the remaining month-to-date AWS baseline after resource termination.
6. Paused the virtual payment card ending in 4274 on Relay Financial during dormant development periods to establish an additional spending-control layer.

Financial Management Lesson

The incident established a core financial-management principle for Architecture of Homosapiens:

Cloud infrastructure is an operating expense and must be treated as a continuously monitored financial liability, not merely as a technical resource.

Unused development infrastructure should be terminated immediately after testing. Network resources, storage, IP addresses, and other dependent resources must also be audited because terminating an application server does not necessarily terminate every billable dependency.

Preventative Production Standard

Future AWS production workloads, including the planned Java full-stack application, will:

* Deploy exclusively under the dedicated enterprise AWS account:
    oluwaseunfunmi@architectureofhomosapiens.com
* Use explicit ownership and environment labeling.
* Enable AWS Budget monitoring before production resources are provisioned.
* Maintain a $1.00 budget-alert threshold for early detection of unexpected spend.
* Require an infrastructure cleanup review after development/testing phases.
* Avoid leaving dormant EC2, EBS, VPC, Elastic IP, or related resources active without a documented business purpose.

AWS Zero-Spend Monitoring

* Budget: My Zero-Spend Budget configured for AWS service monitoring.
* Notification: Email notification configured for charges above $0.01 to oluwaseunfunmi@architectureofhomosapiens.com.
* Post-Cleanup Status: 0 running instances, 0 VPCs, and automated spending alerts verified.

Financial Operations & Records Management

As Architecture of Homosapiens’ financial manager, operating-expense records are being consolidated and transferred from Relay Financial into personal iCloud file storage through the iPhone Files workflow for financial recordkeeping and analysis.

The current financial-record transfer includes account CSV exports and planned PDF statement archives. The business maintains 14 Relay sub-accounts; sub-accounts not yet transferred are currently reported at $0 balances and therefore are not expected to materially affect the Architecture of Homosapiens burn-rate calculation.

Current AI/software tools used for business work—including ChatGPT/Codex, Claude, and Gemini—are presently paid through personal rather than business Relay accounts. These should be tracked as business-related fixed operating expenses when appropriate. Future evaluation may include Grok and Muse AI as potential enterprise software expenses.

The October 2026 operating-expense export provides a baseline for this tracking process, including AWS, Twilio, and Google expenditures. Financial records should be reconciled against the corresponding PDF statements before being treated as the authoritative accounting record.

Operational Lesson

Financial management is part of infrastructure management. Every technical resource should have:

an owner → a purpose → a budget → an expiration/review point → a cleanup procedure.

The AWS incident demonstrated that relatively small recurring infrastructure charges can become persistent burn-rate leakage when ownership and lifecycle controls are unclear. The corrective action therefore focused not only on eliminating the immediate AWS cost, but also on establishing budget alerts, account separation, payment controls, and recurring infrastructure audits.