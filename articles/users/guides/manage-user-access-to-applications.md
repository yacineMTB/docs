---
description: Explains the basics of a User profile, how to create a user and view users and their profile details.
topics:
    - users
    - user-management
    - user-profiles
contentType: how-to
useCase: manage-users
---
# Manage User Access to Applications

Inside a single Auth0 tenant the users are shared between applications because all the applications in a single tenant will usually belong to the same app.

For total separation you can create a new tenant. 

1. Click on tenant name on top right of the dashboard and select **+ Create Tenant** . If you have multiple tenants, you can easily switch between them from the tenants menu.

2. To restrict some users to certain applications you can use rules. Inside a rule, the `context.clientName` and `context.clientID` variables are available to check which application the user is using for login. See [this rule for an example](https://github.com/auth0/rules/blob/master/rules/simple-user-whitelist-for-app.md).

3. To restrict users from applications by configuring a new connection and only giving access to a specific application. 

   * Go to the the **Settings** section for a connection.
   * Click on the **Applications** tab and enable/disable any application.

4. To disable users' access to your applications, you can [block and unblock users](/users/guides/block-and-unblock-users) in the Dashboard.

## Keep reading

* [User Profile Structure](/users/references/user-profile-structure)
* [Auth0 Normalized User Profile](/users/normalized)
* [User Metadata](/metadata)
* [Update Users Using Your Database](/users/guides/update-user-profiles-using-your-database)