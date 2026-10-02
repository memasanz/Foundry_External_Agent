# Foundry external-agent notebooks

These notebooks register an externally hosted agent for Foundry observability. Foundry does not host or invoke the external runtime; it associates OpenTelemetry traces in Application Insights with an external-agent registration.

## Setup

1. Copy `.env.example` to `.env`.
2. Fill in the Foundry project endpoint, Application Insights connection string, agent name, and OpenTelemetry agent ID.
3. Authenticate with Azure:

   ```powershell
   az login
   ```

4. Start Jupyter:

   ```powershell
   .\.venv\Scripts\jupyter-lab.exe
   ```

5. Select the **Python (Foundry External Agent)** kernel and run the notebooks in order:
   - `00_validate_configuration.ipynb`
   - `01_emit_external_agent_trace.ipynb`
   - `02_register_and_verify.ipynb`
   - `03_run_external_agent.ipynb`

`03_run_external_agent.ipynb` calls the model deployment configured by
`MODEL_DEPLOYMENT_NAME`, returns the agent response, and emits correlated
OpenTelemetry spans and Python logs for each invocation.

## Required Azure access

- **Foundry User** on the Foundry project.
- **Reader** or **Monitoring Reader** on the connected Application Insights resource.

External agents are a preview feature. Registration uses `allow_preview=True`.
