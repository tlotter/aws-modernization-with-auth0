+++
title = "Customize Login Flow"
chapter = false
weight = 60
pre = "<b>5. </b>"
+++
You already configured Auth0 to handle your users data and make sure businesses have secure access to your app. But our application still misses a lot of information, for example, what pizzas that organization is allowed to order based on their license or what organization is actually called (remember, right now all we know is an organization ID). This is what we will achieve in this lab!

### 1. Add Metadata to Organization

1. Go to your organization by navigating to **Organizations** in the Auth0 sidebar.
2. Selecting the organization you have created in the previous lab.
3. Scroll down in the **Overview** tab, find the metadata table, and create new metadata with the key `license` and the value `corporate` (it's important to write both in lowercase).

### 2. Create Auth0 Action

To get this information to our application, we need to utilize Auth0 Actions. Actions are JavaScript code snippets that run during the login flow (or in other places, depending on where you integrate them) and which allow you to modify the login flow to your liking.

1. To build our action, go to **Actions** -> **Flows** in the Auth0 Sidebar and select **Login** (This is where the action will be executed).
2. In the top right, click on the **plus** next to **Add Action** -> **Build Custom**.
3. Give your action some expressive name (like `Enrich ID Token`) and click on **Create**.
4. In the code editor you have just opened, you can now write your logic to add two new attributes (called claims) to the ID Token that Auth0 issues on every login. The two claims we need are the following:
    - https://pizza0.net/organization with the organizations display name as a value
    - https://pizza0.net/license with the organizations license (which we just set in the metadata) as a value.
5. Paste the following Code Snippet
```
/**
* Handler that will be called during the execution of a PostLogin flow.
*
* @param {Event} event - Details about the user and the context in which they are logging in.
* @param {PostLoginAPI} api - Interface whose methods can be used to change the behavior of the login.
*/
exports.onExecutePostLogin = async (event, api) => {
    if(event.organization) {
      api.idToken.setCustomClaim("https://pizza0.net/license", event.organization.metadata.license);
      api.idToken.setCustomClaim("https://pizza0.net/organization", event.organization.display_name);
    }
  };
```

- The **api** object lets you modify the ID Token
- The **event** token holds information about an organization.
    - `event.organization.name` will give you the organization name
    - `event.organization.metadata.<key_name>` will let you access the value of a specific metadata.
- You can insert these values into the ID Token with `api.idToken.setCustomClaim(claimName, claimValue)`.
- You can also check for the organization with `if(event.organization)`.

### 3. Deploy and use Auth0 Action
- Click on Deploy and **Add to flow** (or go back to **Actions** -> **Post-Login**, choose **Custom** in the sidebar and drag your Action into the flow)
- Click on **Save** and log your user in once again.
- You should now be able to order all pizzas on the site and should see the organizations name in the top bar.

### 4. Next Step
- Congratulations, your application just got a lot smarter!
- If you are doing this lab in a guided class, please wait for your instructor to continue the course.
- Otherwise, you may proceed to the next lab to see how you can enable collaboration between organizations.