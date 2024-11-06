---
description: How to request and use Access Tokens.
---

# Authentication

## 1. Get your ClientID and Secret <a href="#get-your-clientid-and-secret" id="get-your-clientid-and-secret"></a>

**If you are an Institution**: make sure that you have generated your ClientID and Secret for institutional use on the [Identity Service](https://identity.instructure.com/login/) page.

**If you are a Partner of Instructure**: make sure that you have received your ClientID and Secret from your Institution.

{% hint style="info" %}
Keep your ClientID and Secret in a safe place! Do not share with anyone else!
{% endhint %}

## 2. Requesting the Access Token <a href="#requesting-the-access-token" id="requesting-the-access-token"></a>

Using the ClientID and Secret you are ready to request for an `access token`. The `access token` is a JSON Web Token, that grants access to the targeted Instructure service. This is a short lived token, it needs to be renewed periodically. Typically expires in one hour.

The following code snippet uses `curl` to send the request and `jq` to extract the `access token` from the answer:

```bash
ACCESS_TOKEN=$(curl --request POST https://api-gateway.instructure.com/ids/auth/login \
--user "${CLIENT_ID}:${SECRET}"  \
--data-urlencode 'grant_type=client_credentials' | jq -r '.access_token')

echo $ACCESS_TOKEN
```

## 3. Using the Access Token <a href="#example-using-the-access-token" id="example-using-the-access-token"></a>

Once you received the `access token` you can call the desired service. The example below will demonstrate this by querying the list of table names that exist in Canvas using the [CD2 service](https://data-access-platform-api.s3.amazonaws.com/index.html). The `access token` shall be passed as a bearer token in the Authorization header:

```bash
curl --request GET 'https://api-gateway.instructure.com/dap/query/canvas/table' \
--header "Authorization: Bearer ${ACCESS_TOKEN}" 
```

Upon success the call returns with a list of table names available Canvas.

#### Deprecation Notice for `x-instauth` Header Parameter <a href="#deprecation-notice-for-x-instauth-header-parameter" id="deprecation-notice-for-x-instauth-header-parameter"></a>

The use of `x-instauth` header parameter to pass the `access token` is considered deprecated. Instead use the `Authorization` header parameter as shown above. In case both header parameters are filled (`x-instauth` and `Authorization`), `Authorization` will take precedence.

Due to compatibility reasons `x-instauth` will be still supported for a while, but all clients are encouraged to switch to the new header value as soon as possible.
