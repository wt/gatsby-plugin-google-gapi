# gatsby-plugin-google-gapi
Gatsby plugin to add google authentication.

This plugin is currently **alpha** quality. The API is subject to change. Please
constribute at https://github.com/wt/gatsby-plugin-google-gapi.

## Install

```shell
npm install --save gatsby-plugin-google-gapi
```

or

```shell
yarn add gatsby-plugin-google-gapi
```

## How to use
Add the plugin to your `gatsby-config.js`:

```js
  plugins: [
    {
      resolve: `gatsby-plugin-google-gapi`,
      options: {
        apiKey: `{API_KEY}`,
        clientId: `{CLIENT_ID}`,
        discoveryURLs: [
          // These are the discovery docs for various Google APIs.
          // This can be empty.
          // Find more here: https://developers.google.com/discovery
          // This one is for the Google Drive v3 api.
          "https://www.googleapis.com/discovery/v1/apis/drive/v3/rest",
        ],
        // The permission scopes your app needs.
        // For auth only, this can be empty.
        // Find more here: https://developers.google.com/identity/protocols/oauth2/scopes
        // This one is for reading a writing all files in Google Drive.
        scopes: ["https://www.googleapis.com/auth/drive"],
      },
    },
  ]
```

## Hooks
### useAuthStatus
#### Returns
 * authed (bool?) - Indicates whether a user is logged in or not. Null if
   status isn't available because the gapi lib is still initializing.
 * userFirstName (string) - The user's first name

#### Example
```js
const Example = () => {
  const { authed, userFirstName } = useAuthStatus()

  if (authed === null) {
    return
      <>
        "Login status not available"
      </>
  } else {
    return
      <>
        {authed ? `Hello, ${userFirstName}` : "Not Logged In"}
      </>
  }
```


## Methods
### loginUser
Starts a Google authentication process for the site.

### logoutUser
Logs off of the Google account for the site.


## Demo
This plugin was originally developed by Wren Turkal for https://ymatyt.com/.
Please check it out!
