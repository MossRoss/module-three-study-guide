# NPM for React

| Term | Definition |
| ---- | ---------- |
| __Node.js__ | A JavaScript runtime environment built on Chrome's V8 JavaScript engine. It allows developers to run JavaScript code outside of a web browser, enabling server-side JavaScript development. |
| __npm__ | Node Package Manager for Node.js. It is a command-line tool that helps manage dependencies (third-party libraries) and facilitates the installation, sharing, and versioning of JavaScript packages. |
| __package.json__ | A file used in Node.js projects to store metadata and configuration information about the project. It includes details such as the project name, version, dependencies, scripts, and more. |
| __Modules__ | Reusable pieces of code that can be organized into separate files. Each file is treated as a module and has its own scope for variables and functions. Modules allow for better code organization and encapsulation. |
| __Import & Export__ | JavaScript syntax used to share code between modules. The export statement is used to export variables, functions, or objects from a module, making them accessible to other modules. The import statement is used to import and use exported code from other modules. |
| __JSON__ | JavaScript Object Notation is a lightweight data format that is easy for humans to read and write and easy for machines to parse and generate. It is often used to transmit data between a server and a web application as a text format. |
| __Scripts__ | In the context of package.json, a script is a command or set of commands that can be executed via the command line using npm. Scripts are defined in the "scripts" section of the package.json file and can be used for tasks such as running tests, building the application, or performing other custom operations. |

## Creating a Node.js project

- What does `mkdir` stand for?
- What does `cd` stand for?

```bash
mkdir my-node-project
cd my-node-project
npm init
```

## Exporting a Variable

- What does the `default` keyword do?

```js
export default message;
```

## Importing a Module

- The import name `importedMessage` doesn't match the export name `message` from above. Is that ok?
- Does this renaming on import change the name of the export?

```js
import importedMessage from "./messages.js";
```

## Exporting & Importing Multiple Variables

- These import and export names do match, why is that?
- Could we change them to not match?

```js
// messages.js
export { message, anotherMessage };
import { message, anotherMessage } from "./messages.js";
```

## Renaming Imported Modules

- What are some benefits of renaming imported variables?
- What are some good conventions to follow when naming variables? (use Camel Case, meaningful to what you are doing)

```js
import {message as hello, anotherMessage} from "./messages.js";
```

## Exporting a Function

- What's the purpose of exporting a function?  Ans. (To use the functionality of that function)
- How come we don't include the parameters in our export? answ. (So we don't call the function here) if customMessage() it means we are calling it)

```js
const customMessage = (message, name) => {
  return `${message} ${name}`;
};

module.exports = { message, anotherMessage, customMessage };
```

## Importing a Function

- How do we know that `customMessage` is a function?
- Why are we passing "Nice to see you," and "Ava" to the `customMessage` function?

```js
import {
  message as hello,
  anotherMessage as goodbye,
  customMessage,
} from "./messages.js";

console.log(customMessage("Nice to see you,", "Ava"));
```

## Exporting JSON

- Why isn't there an export statement anywhere?

```json
[
  {
    "id": "0001",
    "type": "donut",
    "name": "Cake"
  },
  {
    "id": "0002",
    "type": "donut",
    "name": "Raised"
  },
  {
    "id": "0003",
    "type": "donut",
    "name": "Old Fashioned"
  }
]
```

## Importing JSON

- What's different about importing JSON compared to other imports?
- Do we need to `assert` the data type for JSON in the latest version of React?

```js
import donuts from "./donuts.json" assert { type: "json" };  Answ. (importing name from a file assert is needed if you don't have  (Because web pack includes assert)
```

## Create a Custom Script in `package.json`

- What benefits can you see from creating your own scripts? 
    Answ. Creating your own npm scripts empowers you to automate tasks, customize your development workflow, improve efficiency, and maintain a consistent and manageable project environment.

```json
// package.json
{
  "name": "my-node-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "my-script": "echo 'I just ran my own script!'"
  },
  "author": "",
  "license": "ISC"
}
```

```bash
npm run my-script
```
