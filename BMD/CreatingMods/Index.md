This guide provides detailed instructions on creating mods for Bot Maker for Discord (BMD).

Also, please follow the general structure when creating mods. Therefore, add **\_MOD** after your mod name, don't include any additional dots or spaces, and make sure to include the info object within your modded action.
Feel free to add a short description for your action as seen in [**animeSearch_MOD.js**](https://github.com/RatWasHere/bmods/blob/master/Actions/animeSearch_MOD.js).

## :icon-image: Interface Components

- **Separators**: "-"
- **Variable Inputs**: [Pastebin Link](https://pastebin.com/WUmLP4p8)
- **Storage Inputs**: [Pastebin Link](https://pastebin.com/XxShh9px)
- **User Inputs**: [Pastebin Link](https://pastebin.com/X83hJSgH)
- **Channel Inputs**: [Pastebin Link](https://pastebin.com/1xqMaYkj)
- **Toggles**: [Pastebin Link](https://pastebin.com/6wcXr8wu)
- **Menus**: [Pastebin Link](https://pastebin.com/XHUV83Ez)
- **Classic Dropdowns**: [Pastebin Link](https://pastebin.com/65ridJs7)
- **Typed Dropdowns**: [Pastebin Link](https://pastebin.com/AgnnSRv3)
- **Input Groups**: [Pastebin Link](https://pastebin.com/UK537p64)
- **Inputs**: [Pastebin Link](https://pastebin.com/K3XVipSZ)

## Actions

Use [this website](https://devvyyxyz.github.io/bmd-action-maker/) as an easy way to create an action.

### Example action code

```js
module.exports = {
  data: {
    name: "Name", //Mods name
  },
  category: "Category", //Category that will group together
  info: {
    source: "https://github.com/<username>/<repo>",
    creator: "Author", //Creators Name
    donation: "https://paypal.me/<username>"
  },
  UI: [
  {
    "element": "input",
    "name": "Name",
    "storeAs": "Variable"
  }
],
  subtitle: (values) => {return `Path: ${values.path}`},
  compatibility: ["Any"],

  //Script
  //Code here...
};
```

### Elements

+++ Interaction

**Interaction Inputs**:

  ```json
  {
    "element": "interaction",
    "storeAs": "string_pointing_to_object"
  }
  ```

+++ Image

**Image Inputs**:

  ```json
  {
    "element": "image",
    "storeAs": "string_pointing_to_object"
  }
  ```

+++ Message

**Message Inputs**:

  ```json
  {
    "element": "message",
    "storeAs": "string_pointing_to_object"
  }
  ```

+++ Other

**Actions**:

  ```json
  {
    "element": "actions",
    "storeAs": "string"
  }
  ```

  **Conditional Actions & Additional Options**:

  ```json
  {
    "element": "condition",
    "storeAs": "string_pointing_to_object",
    "storeActionsAs": "string_pointing_to_array"
  }
  ```

+++ Role

**Role Inputs**:

  ```json
  {
    "element": "role",
    "storeAs": "string_pointing_to_object"
  }
  ```

+++ Text

**Text**:

  ```json
  {
    "element": "text",
    "text": "string"
  }
  ```

  **Large Inputs**:

  ```json
  {
    "element": "largeInput",
    "storeAs": "string_pointing_to_string"
  }
  ```

+++

## Events

Use [this website](https://devvyyxyz.github.io/bmd-action-maker/) as an easy way to create an event.

### Example event code

```js
module.exports = {
  data: {
    name: "Name", //Mods name
  },
  category: "Category", //Category that will group together
  info: {
    source: "https://github.com/<username>/<repo>",
    creator: "Author", //Creators Name
    donation: "https://paypal.me/<username>"
  },
  UI: [
  {
    "element": "input",
    "name": "Name",
    "storeAs": "Variable"
  }
],
  subtitle: (values) => {return `Path: ${values.path}`},
  compatibility: ["Any"],

  //Script
  //Code here...
};
```

### Elements

## Themes

### Elements

## Bridge Controls

+++ Call

**call**:

  ```javascript
  (blob, actions) :: [ASYNC] Blob: Condition generated Object | Actions: Condition generated array :: Promise
  ```

**callActions**:

  ```javascript
  (blob) :: [ASYNC] Blob: Object with any of these properties: {stop, jump, skip, actions} - Stop: Boolean, Jump: Number, Skip: Number, Actions: Array :: Promise
  ```

+++ Create

**createTemporary**:

  ```javascript
  (blob) :: Blob: Object with these properties: {class, name, value} - Class: String (Optional) - Name: String - Value: Any; Creates temporary values in storage for sharing between a group's actions for context, inaccessible to the user. See joinVoiceChannel actions for examples :: Void
  ```

**createGlobal**:

  ```javascript
  (blob) :: Blob: Object with these properties: {class, name, value} - Class: String (Optional) - Name: String - Value: Any; Creates global values in storage for sharing between a group's actions for context, inaccessible to the user. See createAnchor for examples :: Void
  ```

+++ Get
**get**:

  ```javascript
  (blob) :: Blob: variableInput generated object :: Value of variable
  ```

**getUser**:

  ```javascript
  [ASYNC] (blob) :: Blob: userInput generated Object :: [User](https://docs.oceanic.ws/v1.9.0/classes/User.html) with a `member` [OPTIONAL] property
  ```

**getChannel**:

  ```javascript
  [ASYNC] (blob) :: Blob: channelInput generated Object :: [Channel](https://docs.oceanic.ws/v1.9.0/classes/Channel.html)
  ```

**getImage**:

  ```javascript
  [ASYNC] (blob) :: Blob: image (input) generated Object :: Image Buffer
  ```

**getRole**:

  ```javascript
  [ASYNC] (blob) :: Blob: roleInput generated Object :: [Role](https://docs.oceanic.ws/v1.9.0/classes/Role.html)
  ```

**getTemporary**:

  ```javascript
  (blob) :: Blob: Object with these properties: {class, name} - Class: String (Optional) - Name: String :: Any
  ```

**getGlobal**:

  ```javascript
  (blob) :: Blob: Object with these properties: {class, name} - Class: String (Optional) - Name: String :: Any
  ```

**getInteraction**:

  ```javascript
  [ASYNC] (blob) :: Blob: interactionInput generated Object :: [Interaction](https://docs.oceanic.ws/v1.9.0/classes/Interaction.html)
  ```

+++ generate

**generateCustomID**:

  ```javascript
  () :: null :: Number
  ```

+++ Runner

**runner**:

  ```javascript
  (actions) :: [ASYNC] Blob: actions generated Array :: Promise
  ```

+++ Store

**store**:

  ```javascript
  (blob) :: Blob: storageInput generated Object :: Void
  ```

+++ Transfer

**transf**:

  ```javascript
  (inputText) :: inputText: text to transform variables from ${...} to their values :: String
  ```

+++