# Agent instructions

## CI failure triage — evidence from the failing job

When investigating a failed, timed-out, or unexpectedly canceled CI check:

1. Record the exact repository, commit SHA, provider, pipeline/workflow ID, failing job, and attempt. Confirm the log belongs to the commit under investigation.
2. Read the **actual failing job's step logs** before diagnosing or changing code. For CircleCI, try the connected CircleCI tool or authorized API first. If that cannot expose the logs, use the CircleCI web UI through an **authorized cloud browser** when permitted; request user approval or account access if needed. Never bypass access controls or assume a session exists.
3. Identify the first actionable failure in the log; distinguish application regressions from runner, dependency, credential, and infrastructure failures. Do not rely on a red GitHub check or summary alone.
4. Make a scoped change on a dedicated branch, run the relevant validation, and inspect the new job logs/status at the **new SHA**. Do not claim the issue is fixed without evidence from a completed run.
5. If job logs remain inaccessible, report the blocker and the exact URL instead of guessing. Redact credentials, tokens, private data, and sensitive log excerpts from issues, PRs, and messages.

If the repository uses a CI provider other than CircleCI, apply the same evidence-first process using that provider's job logs. Prefer remote CI; do not require builds on the user's local PC for ordinary diagnosis.
