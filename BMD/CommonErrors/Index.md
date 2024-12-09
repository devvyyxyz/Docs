This document outlines frequent console errors encountered in Bot Maker For Discord (which uses Oceanic.js) and provides their solutions.

## Error: `Unhandled Rejection DiscordRESTError: Invalid Form Body`

When attempting to register application commands (e.g., using `bulkEditGlobalCommands`), you may encounter the following error:

```bash
Unhandled Rejection DiscordRESTError: Invalid Form Body on PUT /api/v10/applications/.../commands 
0.options.0: Field "type" is required to determine the model type. 
1.options.0: Field "type" is required to determine the model type. ...
```

### Solution

1. Verify that all options for your commands include a `type` field.
2. Check your command registration code and ensure it adheres to the Discord API's [application command structure](https://discord.com/developers/docs/interactions/application-commands).

### Reason

This error occurs because the Discord API requires a `type` field for all command options to specify the option's data type (e.g., string, integer, boolean, etc.). The missing `type` field causes the request body to be invalid.

## Error: `Error [TOKEN_INVALID]: An invalid token was provided`

When initializing the bot, you may encounter the following error:

```bash
Error [TOKEN_INVALID]: An invalid token was provided.
```

### Solution

1. Double-check your bot token in the `.env` file or configuration file.
2. Regenerate the token from the Discord Developer Portal if you suspect it is compromised or incorrect.
3. Ensure that your bot is connecting to the correct gateway.

### Reason

This error occurs when the bot token used for authentication is invalid. It could be due to a typo, expired token, or an attempt to use the wrong token (e.g., client secret instead of bot token).

## Error: `Unhandled Rejection DiscordRESTError: 403 Forbidden`

When making API calls (e.g., sending messages or updating permissions), you may encounter:

```bash
Unhandled Rejection DiscordRESTError: 403 Forbidden
```

### Solution

1. Check if the bot has the required permissions in the server.
2. Ensure the bot's role is above the roles it is trying to modify.
3. Verify the bot's OAuth2 scopes and granted permissions in the Discord Developer Portal.

### Reason

This error indicates that the bot is attempting an action it does not have permission to perform. Common causes include insufficient permissions in the bot's role or missing OAuth2 scopes during authorization.

## Error: `RangeError [BITFIELD_INVALID]: Invalid bitfield flag or number`

When setting permissions or intents, you may encounter:

```bash
RangeError [BITFIELD_INVALID]: Invalid bitfield flag or number.
```

### Solution

1. Verify that the permissions or intents you are using are valid. Refer to the Discord API documentation for a list of valid flags.
2. Avoid using deprecated or removed permissions.

### Reason
This error occurs when an invalid permission or intent flag is used. Oceanic.js validates these flags against a predefined list, and any mismatch causes this error.

## Error: `Unhandled Rejection DiscordRESTError: 400 Bad Request`

When sending a request to the Discord API, you may encounter:

```bash
Unhandled Rejection DiscordRESTError: 400 Bad Request
```

### Solution

1. Inspect the request payload to ensure all required fields are included and valid.
2. Use a JSON validator to verify the structure of the request body.
3. Cross-reference the payload with the [Discord API documentation](https://discord.com/developers/docs/intro) for the specific endpoint you are using.

### Reason

This error occurs when the API receives a request with missing, invalid, or incorrectly formatted fields. Common causes include:

- Missing required fields (e.g., `name` or `description` for commands).
- Providing fields with the wrong data types (e.g., string instead of integer).

## Error: `TypeError: Cannot read properties of undefined (reading '...')`

When accessing an object property, you may encounter:

```bash
TypeError: Cannot read properties of undefined (reading '...').
```

### Solution

1. Add null checks before accessing properties of objects.
2. Ensure the object you are accessing is properly initialized.
3. Log the variable to confirm it contains the expected data.

### Reason

This error occurs when trying to access a property of `undefined` or `null`. It usually happens when the expected data from the Discord API or another source is missing or improperly handled.

## Error: `Error: Cannot find module 'oceanic.js'`

When starting the bot, you may encounter:

```bash
Error: Cannot find module 'oceanic.js'
```

### Solution

1. Install the library using npm or yarn:

   ```bash
   npm install oceanic.js
   ```

   or

   ```bash
   yarn add oceanic.js
   ```

2. Verify that `node_modules` is not excluded or missing in your project directory.
3. Confirm the import path in your code matches the library.

### Reason

This error occurs when the required dependency is not installed or the import path is incorrect. It may also happen if the `node_modules` directory is missing (e.g., after transferring the project without running `npm install`).

## Error: `UnhandledPromiseRejectionWarning`

When using async functions, you may encounter:

```bash
UnhandledPromiseRejectionWarning: Some Error Message
```

### Solution

1. Always handle promises with `.catch` or `try/catch`.

Example with `.catch`:

```javascript
someAsyncFunction().catch(err => console.error(err));
```

Example with `try/catch`:

```javascript
try {
    await someAsyncFunction();
} catch (err) {
    console.error(err);
}
```

2. Add an `unhandledRejection` handler in your bot for debugging:

```javascript
process.on("unhandledRejection", (reason, promise) => {
    console.error("Unhandled Rejection:", reason);
});
```

### Reason

This warning appears when a promise is rejected but no error handler is attached. Unhandled rejections may crash your application in future versions of Node.js.

## Error: `Error: Request entity too large`

When uploading a large file or payload, you may encounter:

```bash
Error: Request entity too large
```

### Solution

1. Reduce the size of the file or data you are uploading.
2. If uploading attachments, ensure the total size does not exceed Discord's limit (8MB for regular bots, 100MB for Nitro bots).
3. Use `Buffer` or streaming techniques for large data uploads.

### Reason

Discord imposes size limits on API requests and attachments. This error occurs when the payload exceeds these limits.