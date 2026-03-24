---
name: Databricks CLI notebook execution lessons
description: Mistakes and fixes learned from running notebooks via Databricks CLI on this workspace
type: feedback
---

Learned from repeated failures running hypothesis notebooks via `databricks jobs submit`.

**Serverless compute spec:** Use `"environments": [{"environment_key": "default", "spec": {"client": "2"}}]`. `client: "1"` is not supported on this workspace — throws INVALID_PARAMETER_VALUE. Classic clusters are also unsupported (serverless-only workspace).

**Invalid notebook path:** `databricks jobs submit` requires notebooks to be pre-uploaded to the workspace. Use `databricks workspace import --file <local> --format SOURCE --language PYTHON --overwrite <workspace_path>` first. The workspace path must be absolute (e.g. `/Workspace/Users/edevard.hvide@gmail.com/...`). Do NOT pass a local path as the notebook_path in the job JSON.

**Inline notebooks not supported:** The `"source": "INLINE"` with base64 content does not work for notebook tasks — throws "Invalid notebook path". Always upload first, then reference by workspace path.

**get-run-output requires task-level run ID:** `databricks jobs get-run-output <job_run_id>` fails with "multiple tasks" error. Must first get the task-level run_id from `databricks jobs get-run <job_run_id> --output json`, then call `databricks jobs get-run-output <task_run_id>`.

**notebook_output.result is empty unless dbutils.notebook.exit() is called:** print() statements go to cell logs, not to the API-accessible output. Always add `dbutils.notebook.exit(json.dumps({...}))` at the end of any notebook you want to read results from via CLI.

**MLflow on serverless runtime:** `mlflow.anthropic.autolog()` throws AttributeError and `mlflow.set_experiment()` throws CONFIG_NOT_AVAILABLE. Wrap both in try/except. The workspace MLflow tracking server config isn't available in serverless job context.

**pypdf not pre-installed:** Must add `pypdf` to the `%pip install` line explicitly — it's not bundled with the serverless runtime.

**Why:** Each of these caused a separate failed run during hypothesis notebook execution for Phase 01.

**How to apply:** Before submitting any notebook job: (1) upload via workspace import, (2) use client "2" serverless spec, (3) guard mlflow calls, (4) ensure all pip deps are explicit, (5) add dbutils.notebook.exit() for output, (6) use task-level run_id for get-run-output.
