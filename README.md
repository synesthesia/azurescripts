# Example scripts for working with Microsoft Graph and Azure AD (aka Entra ID)

## Microsoft 365 Account needed

To use these samples you need to have access to a Microsoft work or school account with an Exchange Online mailbox. If you don't have a Microsoft account, you can sign up for the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) to get a free Microsoft 365 subscription.

## Language options

- [Python](./python/README.md)
  - [Microsoft MS Graph per-user example](./python/user-auth/README.md)
  - [Microsoft MS Graph application permissions example](./python/app-auth/README.md)


## Install tooling

The following tooling/configuration is needed for all the examples in this repo. (instructions assume running on Windows 11)

- [Visual Studio Code](https://code.visualstudio.com/docs/?dv=win64user)
- [Git for Windows](https://git-scm.com/download/win)
- [Generate SSH keypair](https://www.howtogeek.com/762863/how-to-generate-ssh-keys-in-windows-10-and-windows-11/) if you haven't already got one set up on your machine and with your Github account
- [Create a Github user account](https://docs.github.com/en/get-started/quickstart/creating-an-account-on-github) (or use an existing one)
  - make sure the public key from your SSH keypair is added to your  Github account.

## Fork and clone this repository

- in Github, fork this repository into your own Github account
- in your shell of choice `cd` to the parent directory you want to put this code in
- `git clone git@github.com:YOURUSERNAME/azurescripts.git`
- `cd azurescripts`
- then change directory into the subdirectory for the language of your choice, open VS Code (`code .`) and follow further instructions in the **README**
  - [Python](./python/README.md)

## Authentication

Application access to the Microsoft Graph requires an application registration in Azure AD. There are two methods of authentication used by applications in this sample repository:

- [Access on behalf of a signed-in user](https://learn.microsoft.com/en-us/graph/auth-v2-user?tabs=http) using the [OAuth 2.0 authorization code grant flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow) or the [OAuth 2.0 device authorization grant flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-device-code)
- [Access without a user](https://learn.microsoft.com/en-us/graph/auth-v2-service?tabs=http) using the [OAuth2 client credentials flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow).

Before using any of the samples you need to ensure you have the requisite application registrations in your Azure AD tenant.

### Per-user samples

- for per-user examples, register an app to use device code flow:
  - Open a browser and navigate to the [Azure Active Directory admin centre](https://aad.portal.azure.com/) and login using a Work or School Account with global admin permissions.
  - navigate to [Application registrations](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/RegisteredApps)
  - select New Registration
  - Add a suitable name e.g. `MS Graph Per-User Console`
  - select **Accounts in this organizational directory only**
  - Leave redirect URL blank
  - Click **Register**
  - On the **Overview** page copy the value of the Application (client) ID and save it,  also copy the Directory (tenant) ID and save it.
  - select **Authentication** under **Manage** on the left menu
  - locate the Advanced settings section and change the **Allow public client flows** toggle to Yes, then choose **Save**
  - Notice that you did not configure any Microsoft Graph permissions on the app registration. This is because the sample uses [dynamic consent](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-permissions-and-consent#incremental-and-dynamic-user-consent) to request specific permissions for user authentication.
  
> **Note**
The first time you use this app it may (depending on the settings on your Azure AD tenant and what activity has happened with other users) require an admin to approve the application permissions. Also, if you change the permissions requested then re-approval may be needed.

### Application permissions samples

- for application-only examples, register an app to use the client credentials flow
  - Open a browser and navigate to the [Azure Active Directory admin centre](https://aad.portal.azure.com/) and login using a Work or School Account with global admin permissions.
  - navigate to [Application registrations](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/RegisteredApps)
  - select New Registration
  - Add a suitable name e.g. `MS Graph App-Only Console`
  - select **Accounts in this organizational directory only**
  - Leave redirect URL blank
  - Click **Register**
  - On the **Overview** page copy the value of the Application (client) ID and save it,  also copy the Directory (tenant) ID and save it.
  - Select API permissions under Manage.
  - Remove the default `User.Read` permission under Configured permissions by selecting the ellipses (...) in its row and selecting Remove permission.
  - Select Add a permission, then Microsoft Graph.
  - Select Application permissions.
  - Select `User.Read.All``, then select Add permissions.
  - Select Grant admin consent for..., then select Yes to provide admin consent for the selected permission.
  - Select Certificates and secrets under Manage, then select New client secret.
  - Enter a description, choose a duration, and select Add.
  - Copy the secret from the Value column, you will need it in the next steps. Once you leave this page it won't be shown again.
  
> **Note**
If you need further permissions you need to edit the registration AND re-grant admin consent
