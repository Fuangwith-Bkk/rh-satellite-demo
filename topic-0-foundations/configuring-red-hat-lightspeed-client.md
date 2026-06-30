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

### 2. Authenticating Podman Against the Red Hat Registry

Because the localized Lightspeed microservices run as automated systemd container layers, Podman requires explicit image download credentials bound to the installer environment path prior to launching deployment scripts.

Inject your Red Hat portal account verification tokens into the specific core authorization table:

Bash

```
sudo podman login --authfile /etc/foreman/registry-auth.json registry.redhat.io
```

### 3. Provisioning the On-Premises Lightspeed Backend

With the storage engine authenticated, execute the structural installation routine to deploy the full generative AI analytics processing layers and message broker loops:

Bash

```
sudo satellite-installer --enable-iop
```

### 4. Operational Container Infrastructure Verification

Once the installer finishes compiling the system structures, audit the local Podman engine to guarantee that all runtime microservices are active and processing data normally.

Bash

```
sudo podman ps --format "table {{.Names}} {{.Status}}"
```
