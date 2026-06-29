# Configuring Red Hat Lightspeed Client

## Configuring Red Hat Lightspeed Client (Topic 0.2)

This section details how to connect the primary Satellite Server to the Red Hat Insights telemetry engine to enable the AI-powered **Red Hat Lightspeed** companion service features.

***

### 1. Connecting the Platform Core to Red Hat Insights

To unlock generative AI playbooks and advanced threat modeling vectors, the local Satellite daemon must be registered against the Red Hat Insights cloud analyzer engine via the core installer scenario utility.

Run the registration append switch from your management console:

```bash
sudo satellite-installer --register-with-insights
```
