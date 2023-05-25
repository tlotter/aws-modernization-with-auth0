+++
title = "Customize Login Flow"
chapter = false
weight = 60
pre = "<b>5. </b>"
+++
You already configured Auth0 to handle user data and made sure businesses have secure access to your app. But your application still misses a lot of information e.g. what licenses are assigned. All we know so far is an organization ID.

### 1. Add Metadata to Organization

1. At the navigation bar on the right of the Auth0 Management Dashboard, go to **Organizations**.
2. Click on the organization name **org1**.
3. Scroll down to the Meta section and click on it. Create a new value:
    - Key: `license`
    - Value: `corporate`
    - Click on **+ Add**.

### 2. Create Auth0 Action

To provide the organization license to our application, we need to utilize Auth0 Actions. Actions are JavaScript code snippets that run during the login flow (or in other places, depending on where you integrate them) and which allow you to modify the login flow to your liking.

1. At the navigation bar on the right, go to **Actions** -> **Flows** and click on **Login** (This is where the action will be executed).
2. Next to **Add Action**, click on the **+** button and click on **Build Custom**.
3. Enter the Name `Enrich ID Token` and click on **Create**.
4. In the displayed code editor, you will write some logic to add two new attributes (called claims) to the ID Token that Auth0 issues on every login. The two claims we add are;
    - https://myapp.com/organization with the organization display name as a value
    - https://myapp.com/license with the organization's license (which we just set in the metadata) as a value.
5. Paste the following Code Snippet and click on **Deploy**.
```
/**
* Handler that will be called during the execution of a PostLogin flow.
*
* @param {Event} event - Details about the user and the context in which they are logging in.
* @param {PostLoginAPI} api - Interface whose methods can be used to change the behavior of the login.
*/
exports.onExecutePostLogin = async (event, api) => {
    if(event.organization) {
      api.idToken.setCustomClaim("https://myapp.com/license", event.organization.metadata.license);
      api.idToken.setCustomClaim("https://myapp.com/organization", event.organization.display_name);
    }
  };
```

- The **api** object lets you modify the ID Token
- The **event** token holds information about an organization.
    - `event.organization.name` will give you the organization name
    - `event.organization.metadata.<key_name>` will let you access the value of specific metadata.
- You can insert these values into the ID Token with `api.idToken.setCustomClaim(claimName, claimValue)`.
- You can also check for the organization with `if(event.organization)`.

### 3. Use Auth0 Action
1. Click on **Back to flow**.
2. On the right switch to the tab **Custom** and drag-n-drop **Enrich ID Token** to the flow in the center.
3. Click on **Apply** in the top right.

### 4. Test

1. Navigate to your application, **logout** and login again (`http://localhost:3000`). 
2. You will be asked to enter your organization's name. Enter `org1` and click on **Continue**.
    - The login will automatically redirect you to your Identity Provider (aka Okta if you follow the lab), where you can sign in with your user's credentials.
3. After successful login, click on your Profile on the top left right corner and click on **Profile**.
4. You will notice, that the displayed JSON has two new parameters in the beginning for "https://myapp.com/license" and "https://myapp.com/organization".

```js #10
{
  "https://myapp.com/license": "corporate",
  "https://myapp.com/organization": "org1",
  ...
}
```

### 5. Next Step
- Congratulations, your application just got a lot smarter!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to the next lab to see how you can enable collaboration between organizations.