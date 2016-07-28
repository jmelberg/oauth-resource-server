# Okta OAuth2 Resource Server
This project is intended to be used with the [Okta Angular](https://github.com/jmelberg/angular-sso-samples), Okta w/ AppAuth OAuth2 [iOS](https://github.com/oktadeveloper/okta-openidconnect-appauth-sample-swift), and [Android](https://github.com/oktadeveloper/okta-openidconnect-appauth-sample-android) samples.

## Running the Sample with your Okta Organization

###Pre-requisites
This sample application was tested with an Okta org. If you do not have an Okta org, you can easily [sign up for a free Developer Okta org](https://www.okta.com/developer/signup/).

To test out the [custom claims/scopes](http://openid.net/specs/openid-connect-core-1_0.html#AdditionalClaims) ability with the returned `accessToken`, additionally configure the following:

1. Select the configured **OpenID Connect Application**
2. In the **Authorization Server** screen, click the **OAuth 2.0 Access Token** *Edit* button
3. Add the custom scope `gravatar`.
4. Add the custom claim *name* `user_email` and *value* `appuser.email`
5. Add the **gravatar** scope to your defined scopes:

###[Android](https://github.com/oktadeveloper/okta-openidconnect-appauth-sample-android)
```java
// OktaAppAuth.java

public static final String SCOPE = "openid profile email address phone groups offline_access gravatar";
```
###[iOS](https://github.com/oktadeveloper/okta-openidconnect-appauth-sample-swift)
```swift
// OktaAppAuth.swift

let request = OIDAuthorizationRequest(configuration: config!,
  clientId: self.appConfig.kClientID,
  scopes: [
      ...
      "gravatar",
  ],
```

## Setup
> This document assumes you have `npm` installed.

Once the project is cloned, install the required packages:
  ```
    npm install
  ```

Configure the **orgUrl** and **clientId** in the `server.js` file.
```javascript
var OktaConfig = {
  orgUrl: 'https://example.oktapreview.com',
  clientId: 'CLIENT_ID',
  };
```

By default, the port used is `9000`. You can adjust it in the `server.js` file.
```javascript
var argv = yargs
.usage('\nSimple API Server with OAuth 2.0 Bearer Token Security\n\n' +
      'Usage:\n\t$0 -iss {url} -aud {uri}', {
    port: {
      description: 'Web Server Listener Port',
      required: true,
      alias: 'p',
      default: 9000 // Change me
    },
  ...
```

## Run the Server
Simply run the server in the root project folder with the following command:
```
node server.js
```
