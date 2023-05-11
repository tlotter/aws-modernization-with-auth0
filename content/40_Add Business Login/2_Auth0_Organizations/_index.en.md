+++
title = "Auth0 Organization"
chapter = false
weight = 20
pre = "<b>4.2 </b>"
+++
The Organizations feature represents a broad update to the Auth0 platform that allows our business-to-business (B2B) customers to better manage their partners and customers, and to customize the ways that end-users access their applications. Auth0 customers can use Organizations to:

- Represent their business customers and partners in Auth0 and manage their membership.
- Configure branded, federated login flows for each business.
- Build administration capabilities into their products, using Organizations APIs, so that those businesses can manage their own organizations.

### 1. Create Organization
Auth0 has a native concept of Organizations that makes it easier for you as a developer to organize and manage all your business customers and their login into your solution.

1. To create an organization, go to **Organizations**** in the sidebar of the Auth0 Dashboard and click on **Create Organization**.
2. Give it an easy to remember name (users will need it when signing into your app) and click **Add Organization**.

### 2. Enable Enterprise Login for Organization
Next, you need to enable the OIDC connection you just created in the new organization.

1. In your organization, go to **Connections** -> **Enable Connections**.
2. Find the connection you have previously created and click **Enable Connection**.
3. In the next window, click on **Enable Auto-Membership** and **Save**.
4. This means that users who will access your app through this connection will automatically be part of your organization.

### 3. Assign Organization to Application
Lastly, we need to let our Pizza0 application know that we expect business users to sign in instead of everyday end users.

1. Find your application by navigating to **Applications** -> **Applications** in the Auth0 Dashboard and click on the application you have registered previously.
2. In the following window, you will find a tab called **Organizations**. Navigate to that, enable the Display Organization Prompt and set the dropdown to **Team members of organizations**.
3. Note: Eventually the option to enable organizations will be greyed out. There will be a warning box that some login grants have to be disabled first. Click on **Disable Grants Now** and proceed.

### 5. Test
Return to your Pizza0 site and click on login.

- You will now be asked to enter your organizations name (which is the one you gave to your organization when you registered it).
The login will automatically redirect you to your Identity Provider (aka Okta if you follow the lab), where you can sign in with your users credentials.
- After successful login, you should now have an organization ID displayed in the header of the Pizza0 site.

## 6. Next Step
- Congratulations, you can now start your successful B2B business! By completing these steps we now can safely integrate our business customers into our application and even make sure to keep track of them through organizations. Under the hood, this brings a lot of value: Your customers admins can still provision / deprovision users, control who has access to your app, and see how frequently your app is used. And you just saved a few days of building your own OpenID Connect integration!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to the next lab to see how you can give your application a lot more information about our users.