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

### 1. Create an Organization
Auth0 has a native concept of Organizations that makes it easier for you as a developer to organize and manage all your business customers and their login into your solution.

1. At the navigation bar on the right of the Auth0 Management Dashboard, go to **Organizations** and click on **+ Create Organization**.
2. Enter the name `org1` and click **Add Organization**.

### 2. Enable Enterprise Login for Organization
Next, you need to enable the Okta connection you just created in the new organization.

1. In your created organization, switch to the tab **Connections**
2. Click on **Enable Connections**.
3. Select **Okta1** and click on **Enable Connection**.
4. In the next window, select **Enable Auto-Membership** and **Save**.
    - This means that users who will access your app through this connection will automatically be part of your organization.

### 3. Assign Organization to Application
Lastly, we need to let our application know that we expect business users to sign in instead of everyday end users.

1. At the navigation bar on the right of the Auth0 Management Dashboard, go to **Applications** -> **Applications**
2. Click on the name of the **CIC Workshop** Application.
3. Switch to the tab **Organizations**.
4. Select **Business Users** and as Login Flow **Prompt for Organization**.
5. Click on **Save Changes**.

### 4. Test

1. Navigate to your application, logout and login again (`http://localhost:3000`). 
2. You will be asked to enter your organizations name. Enter `org1` and click on **Continue**.
    - The login will automatically redirect you to your Identity Provider (aka Okta if you follow the lab), where you can sign in with your user's credentials.
3. After successful login, click on your Profile on the top left right corner and click on **Profile**.
4. You will notice, that the displayed JSON has the new parameter **org_id**:

```js #10
{
  ...
  "org_id": "org_9EbOosmUXcoSBwj7"
}
```

### 5. Next Step
- Congratulations, you can now start your successful B2B business! By completing these steps, we can now safely integrate our business customers into our application and even make sure to keep track of them through organizations. Under the hood, this brings a lot of value:
    - Your customer's admins can still provision / deprovision users
    - control who has access to your app
    - and see how frequently your app is used.
    - And you just saved a few days of building your own OpenID Connect integration!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to the next lab to see how you can give your application a lot more information about our users.