https://github.com/GustavoPCS/n8n-sprint2-issue-triage

# GitHub Issue Triage – n8n Sprint 2

## Purpose
Automate GitHub issue classification and routing using n8n, while preventing duplicate records from repeated webhook deliveries.

## Services
- GitHub – Issue creation and webhook events
- GitHub CLI – Webhook forwarding
- n8n – Workflow automation
- Docker – Local n8n hosting
- Database – Issue ledger and route logs

## Public Repository URL
https://github.com/GustavoPCS/n8n-sprint2-issue-triage

## Node Sequence
1. GitHub Webhook (POST)
2. Extract and normalize issue fields
3. Check/create ledger record
4. Classify issue using regex
5. Route to appropriate category
6. Record routing action

## Field Mapping
- `repository_full_name` – Full name of the GitHub repository
- `issue_number` – GitHub issue number
- `issue_key` – Unique repository and issue identifier
- `issue_url` – URL of the GitHub issue
- `title` – Original issue title
- `title_lower` – Lowercase issue title for classification
- `reporter` – GitHub username of the issue creator
- `opened_at` – Issue creation timestamp
- `last_seen_at` – Most recent processing timestamp

## Exact Classification Rules
Applied to `{{ $json.title_lower }}`:

- Bug: `\b(bug|error)\b`
- Feature: `\b(feature|request)\b`
- Help: `\b(help|question)\b`

## Setup Notes
1. Run n8n locally using Docker (`localhost:5678`).
2. Publish the workflow.
3. Forward GitHub events using:
   ```powershell
   gh webhook forward --repo GustavoPCS/n8n-sprint2-issue-triage --events issues --url "http://localhost:5678/webhook/sprint2-issue-triage"
   ```
4. Create GitHub issues and verify n8n executions.
5. Redeliver the same event to test duplicate prevention.

## Evidence Links / Screenshots
- [GitHub Test Issue](https://github.com/GustavoPCS/n8n-sprint2-issue-triage/issues)
- [Workflow / Execution Screenshot](evidence/execution.png)
- [Ledger Screenshot](evidence/Ledger1.png)
- [Ledger Screenshot 2](evidence/Ledger2.png)
- [Redelivery Screenshot](evidence/redelivery.png)

