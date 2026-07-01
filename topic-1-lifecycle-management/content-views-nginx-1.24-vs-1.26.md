# Content Views (Nginx 1.24 vs 1.26)

#### 1. Creating the Lifecycle Environments

Before creating our Content View, we must establish our environment paths (Development and Production) to map the logical progression of our software stack.

**Web UI Execution Path**

1. Navigate to Content > Lifecycle Environments.
2. Click New Environment Path on the right side.
3. Configure the Development environment using the following parameters:
   * Name: `Development`
   * Label: `Development`
   * Description: Testing and staging environment for unstable package sets (Nginx 1.26).
4. Click Save.
5. Click Add Environment at the end of the Development track to chain the Production environment:
   * Name: `Production`
   * Label: `Production`
   * Description: Locked down, highly stable baseline environment (Nginx 1.24).
6. Click Save.

<figure><img src="../.gitbook/assets/6-environment.png" alt=""><figcaption></figcaption></figure>

#### 2. Initializing the `CV_RHEL9_WebStack` Content View

With our environments configured, we will create the foundational Content View assembly engine.

**Web UI Execution Path**

1. Navigate to Content > Content Views and click Create Content View.
2. Populate the creation fields with these exact properties:
   * Name: `CV_RHEL9_WebStack`
   * Label: `CV_RHEL9_WebStack`
   * Type: `Content View` .
3. Click Save.

<figure><img src="../.gitbook/assets/7-content-view.png" alt=""><figcaption></figcaption></figure>

#### 3. Attaching Repository Data Streams

1. Inside the newly created `CV_RHEL9_WebStack` layout, navigate to the Repositories sub-tab.
2. Click Add Repositories.
3. Select the check boxes next to all four streams we synchronized during Step 4:
   * `Red Hat Enterprise Linux 9 for x86_64 - BaseOS RPMs 9`
   * `Red Hat Enterprise Linux 9 for x86_64 - AppStream RPMs 9`
   * `Red Hat Satellite Client 6 for RHEL 9 x86_64 RPMs`
   * `Nginx Production Feed RHEL 9`
4. Click Add Repositories to confirm integration.

<figure><img src="../.gitbook/assets/8-add-repo.png" alt=""><figcaption></figcaption></figure>

#### 4. Implementing Content View Version Filters

To fulfill the demo narrative—ensuring `rhel9-prod` safely tracks an isolated, corporate-approved legacy web engine while `rhel9-dev` unlocks cutting-edge features—we construct an Inclusion Filter. This blocks all packages within our custom repository unless they match our explicit version constraints.

**Step 4.1: Create the Filter Container**

1. Inside your `CV_RHEL9_WebStack` dashboard view, navigate to the Filters tab.
2. Click Create Filter to initialize the wizard modal.
3. Define the configuration container fields as follows:
   * Name: `Filter_Nginx_Versions`
   * Content type: `RPM`
   * Inclusion Policy: Select the Include filter radio button (allowing only specified packages to pass).
   * Description: `Version isolation logic for RHEL 9 cloud instance deployment pipelines.`
4. Click Create filter.

<figure><img src="../.gitbook/assets/9-filter.png" alt=""><figcaption></figcaption></figure>

**Step 4.2: Define the Nginx 1.24 Inclusion Rule**

1. Click on the newly created `Filter_Nginx_Versions` link to open its rules management page.
2. Under the Included RPMs section, click the blue Add RPM rule button.
3. Populate the package target parameters to explicitly isolate our initial production baseline:
   * RPM name: `nginx`
   * Architecture: _(Leave blank to allow all matching architectures)_
   * Version Operator: `Equal to`
   * Version: `1.24*`
4. Click Add rule to lock the constraint into the view pipeline.

<figure><img src="../.gitbook/assets/10-add-rule.png" alt=""><figcaption></figcaption></figure>

**Step 4.3: Publish & Promoting Version 1.0 (Production)**

Now that your filter container holds the rule for `1.24*`, you are ready to publish Version 1.0 of the Content View!

1. Go back up to the top of the content view page or click the Versions tab.
2. Click the blue Publish new version button.
3. Name/Description it something clear like: `Publishing baseline Nginx 1.24 for Production`.
4. Once published, click Promote next to Version 1.0 and push it directly into your Production Lifecycle Environment.

<figure><img src="../.gitbook/assets/11-publish.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/12-promote.png" alt=""><figcaption></figcaption></figure>
