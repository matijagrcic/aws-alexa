# Local Debugging

[ASK SDK Local Debug (Node.js)](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs/tree/2.0.x/ask-sdk-local-debug)

> ASK SDK Local Debug is a package which enables you to test your skill code locally against your skill invocations by routing requests to your developer machine. This enables you to verify changes quickly to skill code as you can test without needing to deploy skill code to Lambda.

```bash
npm install --save ask-sdk-model@^1.29.0
npm install --save-dev ask-sdk-local-debug
```

[ask-sdk-local-debug](https://www.npmjs.com/package/ask-sdk-local-debug)

> allows you to redirect your skill requests back to your developer machine [ref](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs/issues/12#issuecomment-663098653)

```json{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Alexa Skill (Node.js)",
      "type": "node",
      "request": "launch",
      "program": "${command:ask.debugAdapterPath}", //this didn't find the ask-sdk-local-debug so used "program": "node_modules/ask-sdk-local-debug/dist/LocalDebuggerInvoker.js",
      "args": [
        "--accessToken",
        "${command:ask.accessToken}",
        "--skillId",
        "${command:ask.skillIdFromWorkspace}",
        "--handlerName",
        "handler",
        "--skillEntryFile",
        "${workspaceFolder}/lambda/index.js",
        "--region",
        "NA"
      ],
      "cwd": "${workspaceFolder}/lambda"
    }
  ]
}
```

[Ref](https://developer.amazon.com/en-US/docs/alexa/ask-toolkit/vs-code-testing-simulator.html#prepare)

> Can't locally debug Alexa Hosted Skill if used with DynamoDB as [ref](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs/issues/684#issuecomment-791359878)

[Alexa Skills Kit (ASK) Toolkit](https://marketplace.visualstudio.com/items?itemName=ask-toolkit.alexa-skills-kit-toolkit)

> Alexa Skills Toolkit for Visual Studio Code is an extension that makes it easier for you to create, test, and deploy Alexa skills. It provides a dedicated workspace for Alexa Skills in VS Code and provides features for managing and previewing APL documents along with the ability to test and debug your skills in VS Code with local debugging.

[Alexa Skills Toolkit for Visual Studio Code](https://github.com/alexa/ask-toolkit-for-vscode)
