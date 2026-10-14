
# Runbook – GitHub Issue Triage

## Normal Operation
1. Start n8n locally using Docker (`localhost:5678`).
2. Ensure the workflow is published and active.
3. Start GitHub webhook forwarding:
   ```powershell
   gh webhook forward --repo GustavoPCS/n8n-sprint2-issue-triage --events issues --url "http://localhost:5678/webhook/sprint2-issue-triage"
   ```
4. Create a GitHub issue and verify the execution in n8n.
5. Confirm that one ledger row and the correct route-log row were created.

## Duplicate Delivery
- Repeated deliveries of the same issue should not create duplicate records.
- The existing `issue_key` should remain unique in the ledger.
- `last_seen_at` may update, but no additional route-log entry should be created.
- Verify this by comparing ledger and route-log records before and after redelivery.

## Route-Log Failure
- Check the n8n Executions tab for failed nodes and error messages.
- Verify the database connection and required field mappings.
- Confirm that the ledger entry exists and the route-log entry is missing.
- Do not create another GitHub issue to retry the operation.

## Recovery Action
1. Identify and correct the failed node or database operation.
2. Check existing ledger and route-log records before retrying.
3. Retry the failed execution or original webhook delivery when safe.
4. Verify that the missing route-log entry is created without duplicates.

## Safely Disable the Workflow
1. Stop GitHub CLI forwarding using `Ctrl+C`.
2. Deactivate or unpublish the workflow in n8n.
3. Confirm that no new webhook executions are triggered.
4. Preserve existing ledger records, route logs, and execution evidence.
5. Stop the Docker container if n8n is no longer needed.
