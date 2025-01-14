---
title: User Object in Rules
description: Available properties of the user object in Rules.
toc: true
topics:
  - rules
  - extensibility
contentType: reference
useCase: extensibility-rules
---

# User Object in Rules

The `user` object represents the logged in user, returned by the identity provider.

## Properties of the `user` object

The following properties are available for the `user` object.

| Property | Data Type        | Description |
|----------|------------------|-------------|
| `user.app_metadata` | object | Custom fields that store info about a user that influences the user's access, such as support plan, security <dfn data-key="role">roles</dfn>, or access control groups. For more info, see [Metadata](/metadata). |
| `user.created_at` | date time | Timestamp indicating when the user profile was first created. |
| `user.email` | text | (unique) The user's email address. |
| `user.email_verified` | boolean | Indicates whether the user has verified their email address. |
| `user.family_name` | text | The user's family name. |
| `user.given_name` | text | The user's given name. |
| `user.identities` | array (object) |  <%= include('../_includes/_user-prop-identities.md') %> |
| `user.last_password_reset` | date time | Timestamp indicating the last time the user's password was reset/changed. At user creation, this field does not exist. |
| `user.multifactor` | array (text) | List of <dfn data-key="multifactor-authentication">multi-factor authentication (MFA)</dfn> providers with which the user is enrolled. This array is updated when the user logs in with MFA successfully for the first time, and is not updated when enrollment is completed or when an administrator resets a user's MFA. |
| `user.name` | text | The user's full name. |
| `user.nickname` | text | The user's nickname. |
| `user.permissions` | text | The permissions assigned to the user's ID token |
| `user.phone_number` | text  | The user's phone number. Only valid for users with SMS connections. |
| `user.phone_verified` | boolean | Indicates whether the user has been verified their phone number. Only valid for users with SMS connections. |
| `user.picture` | text | URL pointing to [the user's profile picture](/user-profile/user-picture). |
| `user.updated_at` | date time | Timestamp indicating when the user's profile was last updated/modified. Changes to `last_login` are considered updates, so most of the time, `updated_at` will match `last_login`. |
| `user.user_id` | text | (unique) The user's unique identifier. |
| `user.user_metadata` | object | Custom fields that store info about a user that does not impact what they can or cannot access, such as work address, home address, or user preferences. For more info, see [Metadata](/metadata). |
| `user.username` | text | (unique) The user's username. |

## The `user` object with Delegation flows

However, if you execute the rule in the context of a call made to the delegation endpoint, the `user` object will also include the original JSON Web Token (JWT) claims:

```json
{
  "name": "FirstName LastName",
  "email": "FirstNameLastName@example.com",
  "iss": "https://example.auth0.com/",
  "sub": "auth0|user_id",
  "aud": "<audience id for my auth0 app>",
  "iat": 1566405149,
  "exp": 1566441149,
  "persistent": {}
}
```