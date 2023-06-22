+++
title = "Enable Collaboration"
chapter = false
weight = 70
pre = "<b>6. </b>"
+++

We want to bring in a second organization and enable collaboration with the first organization. This way your customers can not only access their secured and isolated environment, but also be invited to other environments.

### 1. Create additional Enterprise Connection and Organization

1. Create a new Enterprise Connection with the name `Okta2`
    - Follow the instructions of chapter [4.1 Enterprise Connections]( {{< ref "40_Add Business Login/1_Enterprise Connections" >}}).
    - If you use your own Okta tenant, just create a new OIDC Application `Auth0 Org2`. A new Okta tenant is not required!
    - The new Okta connection cannot be tested yet, as the Organization **org1** only allows access from the enterprise connection **Okta1**.
2. Create a new Organization with the name `org2` and the metadata `license` = `premium`.
    - Follow the instructions of chapter [4.2 Auth0 Organization]( {{< ref "40_Add Business Login/2_Auth0_Organizations" >}})
    - Enable the Enterprise Connection only for **Okta2** and not **Okta1**!
    - Make sure to test the login with `org2`. The license in the user profile should show **premium** and as org_id **org2**:

```js #10
{
  "https://myapp.com/license": "premium",
  "https://myapp.com/organization": "org2",
  ...
}
```

### 2. Enable Collaboration
To enable collaboration, we need to provide our second organization (**org2**) access to our first organization (**org1**). 
1. In the navigation bar on the right of the Auth0 Dashboard, go to **Organizations** and click on **org1**.
2. Go to the tab **Connections** and click on **Enable Connections**.
3. Select **Okta2** and click on **Enable Connection**.
4. Keep the default selection of **Disable Auto-Membership**

### 3. Test Org1 login before inviting user from Org2

1. Navigate to your application, **logout** and login again (`http://localhost:3000`). 
2. Enter as organization `org1`.
3. Two enterprise Connections for Okta are shown, select the **2nd displayed Enterprise Connection**.
4. The access is denied. The error is not properly displayed in our application, but you can see in the URL of the browser the error message:
    - **http://localhost:3000/?error=access_denied&error_description=..**

### 4. Invite a member of Org2 to Org1

1. In the navigation bar on the right of the Auth0 Dashboard, go to **Organizations** and click on **org1**.
2. Go to the tab **Members** and click on **Add Members**.
3. Search for the user and select the one with the tag **Okta2**.
4. Click on **Add Member(S)**.


### 5. Test Org1 login after inviting user from Org2

1. Navigate to your application, **logout** and login again (`http://localhost:3000`). 
2. Enter as organization `org1`.
3. Two enterprise Connections for Okta are shown, select the **2nd displayed Enterprise Connection**.
4. This time the login is successful.
5. Check the user profile:

```js #10
{
  "https://myapp.com/license": "corporate",
  "https://myapp.com/organization": "org1",
  ...
}
```

### 6. Congratulations
- Congratulations, you completed the basic use cases of the lab!
- In this short time, you were able to integrate a secure login to your application, customize its look and feel, onboard business customers, tailor your application to them and even made them collaborate and access each other's environment.
- Hopefully, this provided you with some good ideas about the capabilities of such features in a real-world application and for your own projects.