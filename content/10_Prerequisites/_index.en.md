+++
title = "Prerequisites"
chapter = false
weight = 20
pre = "<b>1. </b>"
+++
To follow this workshop, you’ll need access to Auth0. You can follow with your local IDE or use the Cloud9 IDE, which requires an AWS Account.

### 1. Create Auth0 Tenant
You need access to an Auth0 Tenant. If you are doing this lab in a guided class, we might provide an Auth0 Tenant via demo.okta.com. Otherwise, please sign-up for a new Auth0 Tenant, as we use some features that are only available as part of the 30 Day Free Trial (for the Business Login UseCase).

1. [Click here to create your free Auth0 Tenant](https://auth0.com/signup). No credit card is required.
2. Sign in with a **Social Identity Provider** or enter a **Password**.
3. Follow the sign-up wizard, the default values work fine for this workshop.

### 2. Follow with local IDE
1. A **code editor** such as **Visual Studio Code** for the live coding
2. **Node.js** Version 16 or higher (check: `node -v`)
3. Install **git/gh cli** (check: `git --version`, https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
4. Clone the lab repository to your local machine
    - `git clone https://github.com/escobar022/okta-cic-workshop-sandbox.git`
5. Install dependencies
    - `cd okta-cic-workshop-sandbox && npm i`

### 3. Follow with Cloud9 IDE (AWS Account required)
If you want to use Cloud9, you need access to an AWS Account.
- If you join an Immersion Day, we will provide AWS Accounts.
- If you don’t already have an AWS Account, create one now.
[Click me to create an AWS Account ](https://aws.amazon.com/getting-started/). You can also find [additional Guidance](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/) on how to Create an AWS Account.

The next step is to clone the sample application to the Cloud9 IDE:
1. Sign-in to your AWS Accound and open the Cloud9 IDE.
![Open Cloud9](images/10_10_open_cloud9.png)
2. Clone the lab repository
    - `git clone https://github.com/escobar022/okta-cic-workshop-sandbox.git`
3. Install dependencies
    - `cd okta-cic-workshop-sandbox && npm i`

The Cloud9 Environment has a different URL than if you follow with your local IDE. Get the URL of the Cloud9, that we need in the next step for the local callback URL
1. Go to **Preview** and click on **Preview Running Application**.
2. A window with the preview is added. The error message is fine, as we don't run our sample application yet.
3. Click on the icon to **Open Preview** in a new Browser Window and copy the URL. It should looks like https://abcde12345.vfs.cloud9.region.amazonaws.com/
![Get Cloud9 URL](images/10_20_get_cloud9_url.png)

{{% notice warning %}}
For resources provisioned in personal/work AWS accounts - charges may apply. It is highly encouraged to delete the resources once the workshop is completed.
Follow the steps outlined in Chapter **Cleanup** from the menu on the left to delete all resources provisioned during this workshop.
{{% /notice %}}