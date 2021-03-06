# Set up prerequisites for launchpad level0 open_source

The purpose of the CAF Level 0 (L0) bootstrap Azure AD application is to own the creation of the launchpads. During that process a new Azure AD application is created with less permissions on the directory and also more specific Azure permissions to fulfill the Azure operations of the
level0 (subscription creation for example)

This document explains the manual process to create the L0 Azure AD app and the following information must be captured:

| Variable             | Value                    | ID |
| -------------------- | ------------------------ | -- |
|ARM\_CLIENT\_ID       | Application (client) ID  |    |
|ARM\_CLIENT\_SECRET   | Client secret            |    |
|ARM\_TENANT\_ID       | Directory (tenant) ID    |    |
|ARM\_SUBSCRIPTION\_ID | Subscription ID          |    |

## Create Azure AD L0 App

Go to Azure Active Directory

![](./images/setup_prereqs.md/image1.png)

Create a **new** Azure **Active Directory Application**

![](./images/setup_prereqs.md/image2.png)

![](./images/setup_prereqs.md/image3.png)

From the property pane select "**API permissions**"

![](./images/setup_prereqs.md/image4.png)

**Remove** the default one

![](./images/setup_prereqs.md/image5.png)

**Confirm the deletion**

![](./images/setup_prereqs.md/image6.png)

Click on "**Add a permission**"

![](./images/setup_prereqs.md/image7.png)

Select "**Application permissions**"

![](./images/setup_prereqs.md/image8.png)

Select from "**Application**", "**Application.ReadWrite.OwnedBy**"

![](./images/setup_prereqs.md/image9.png)

Then from "**Directory**" select "**Directory.ReadWrite.All**"

![](./images/setup_prereqs.md/image10.png)

Complete the operation by pressing the blue button "**Add permissions**"

Click again on "*Add permission*"

![](./images/setup_prereqs.md/image11.png)

Select the "**Microsoft Graph**"

![](./images/setup_prereqs.md/image12.png)

Select "**Application permissions**"

![](./images/setup_prereqs.md/image13.png)

From "**AppRoleAssignment**" select "**AppRoleAssignment.ReadWrite.All**"

![](./images/setup_prereqs.md/image14.png)

From "**DelegatedPermissionGrant**" select "**DelegatedPermissionGrant.ReadWrite.All**"

![](./images/setup_prereqs.md/image15.png)

Complete the operation by clicking on the blue button "**Add permissions**"

You need to be logged-in with a user who has directory role "**Global Admin**" or permission to grant consents. When ready press the button "**Grant admin consent for \[name of your tenant\]**"

![](./images/setup_prereqs.md/image16.png)

Confirm

![](./images/setup_prereqs.md/image17.png)

You can see the consents have been given with the green tick button

![](./images/setup_prereqs.md/image18.png)

Now the Azure Active Directory Application has been created and given the right permission on the APIs, you need to set a complex password.

From the property pane select "**Certificates & secrets**"

![](./images/setup_prereqs.md/image19.png)

Click on "**New client secret**"

![](./images/setup_prereqs.md/image20.png)

Put a description -- *date of the creation of the secret* as an example

![](./images/setup_prereqs.md/image21.png)

When ready click on the blue button "Add". Note the password will be displayed only after the creation. Copy the password as you will not be able to retrieve it again later. If you missed that step, delete the password and recreate a new one.

![](./images/setup_prereqs.md/image22.png)

### Capture the tenant ID

![](./images/setup_prereqs.md/image23.png)

Capture the client ID

![](./images/setup_prereqs.md/image24.png)

### Capture the subscription ID

From the Azure Portal search bar, type "**Subscription**"

![](./images/setup_prereqs.md/image25.png)

Capture the subscription ID

![](./images/setup_prereqs.md/image26.png)

## Grant subscription owner to level0-security

![](./images/setup_prereqs.md/image25.png)

Click on the subscription

![](./images/setup_prereqs.md/image26.png)

Go to "**Access control (IAM)**"

![](./images/setup_prereqs.md/image27.png)

Select "**Add**".. "**Add role assignment**"

![](./images/setup_prereqs.md/image28.png)

Select Role as "**Owner**". Set the Azure Active Directory application name you created earlier.

![](./images/setup_prereqs.md/image29.png)

Click on the name and then on the "**save**" button

![](./images/setup_prereqs.md/image30.png)

If all the steps have been completed successfully, you are ready to deploy the level 0 open source launchpad.
