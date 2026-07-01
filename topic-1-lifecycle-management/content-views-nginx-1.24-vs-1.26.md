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
