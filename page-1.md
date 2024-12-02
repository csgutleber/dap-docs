# Page 1

### access\_tokens

Stores the access tokens for a user and developer tools.

This table in Canvas Data 2 will only share developer tool specific token metadata. All users have an option to create an access token based on their role and level of data access.

**Parameters:**

* `id` (_int64_): <mark style="color:purple;">**`primary key`**</mark> The unique identifier for an access token record.
* `developer_key_id` ([_developer\_keys_](https://developerdocs.instructure.com/services/dap/dataset/dataset-namespaces/dataset-canvas#developer_keys)): The unique identifier of a developer key.
* `user_id` ([_users_](https://developerdocs.instructure.com/services/dap/dataset/dataset-namespaces/dataset-canvas#users) _|_ _None_): The unique ID of the user the token acts as.



<details>

<summary>account_users</summary>

Join table for accounts, users and roles.

Contains users’ roles within an account (this table includes the account admins).

**Parameters:**

`id` (_int64_): <mark style="color:orange;">**`primary key`**</mark> The unique identifier for the users account association record.

`user_id` ([_users_](https://developerdocs.instructure.com/services/dap/dataset/dataset-namespaces/dataset-canvas#users)): The unique ID of a user.

`created_at` (_datetime_): Timestamp of when an account\_users record was created.

</details>

