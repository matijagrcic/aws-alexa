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

# DAZN Lambda Powertools

[DAZN Lambda Powertools](https://github.com/getndazn/dazn-lambda-powertools)

[lambda-powertools-logger](https://www.npmjs.com/package/@dazn/lambda-powertools-logger)

[dazn-lambda-powertools](https://serverlessrepo.aws.amazon.com/applications/us-east-1/570995107280/dazn-lambda-powertools)

# AWS Powertools

> AWS Powertools are based on idea from DAZN Powertools

[AWS Lambda Powertools (Python)](https://github.com/awslabs/aws-lambda-powertools-python)

[AWS Lambda Powertools (Java)](https://github.com/awslabs/aws-lambda-powertools-java)

[How to Monitor Custom Alexa Skills Using Amazon CloudWatch Alarms](https://developer.amazon.com/blogs/alexa/post/99fb071e-9aaf-481b-b9af-0186c0f712a5/how-to-monitor-custom-alexa-skills-using-amazon-cloudwatch-alarms)

> In case of errors with a skill request, the skill receives a `SessionEndedRequest` that contains the error message and error type. You can log this error information to identify the cause of errors with their skill.

[How to Debug Errors for Custom Alexa Skills](https://developer.amazon.com/blogs/alexa/post/a8b8b146-0e62-44da-ba8e-63b411d8f4c6/how-to-debug-errors-for-custom-alexa-skills)

```js
const SessionEndedRequestHandler = {
  canHandle(handlerInput) {
    return handlerInput.requestEnvelope.request.type === "SessionEndedRequest";
  },
  handle(handlerInput) {
    if (null != handlerInput.requestEnvelope.request.error) {
      console.log(JSON.stringify(handlerInput.requestEnvelope.request.error));
    }

    return handlerInput.responseBuilder.getResponse();
  },
};
```

[Handle Requests Sent by Alexa](https://developer.amazon.com/en-US/docs/alexa/custom-skills/handle-requests-sent-by-alexa.html)

> If you host your skill with AWS Lambda, you can provide your skill ID as part of the Alexa Skills Kit trigger. This adds a verification check before your function is ever invoked, so unverified skills cannot invoke your function. In this case, you do not need to check the skill ID in your code.

```js
//code rejects any requests where the skill ID does not match "amzn1.ask.skill.1"
const skillBuilder = Alexa.SkillBuilders.custom();

exports.handler = skillBuilder
  .withSkillId("amzn1.ask.skill.1")
  .addRequestHandlers(
    HelloWorldIntentHandler,
    LaunchRequestHandler,
    HelpIntentHandler,
    CancelAndStopIntentHandler,
    SessionEndedRequestHandler
  )
  .addErrorHandlers(ErrorHandler)
  .addRequestInterceptors(LoggingRequestInterceptor)
  .addResponseInterceptors(LoggingResponseInterceptor)
  .lambda();
```

[SessionEndedRequest](https://developer.amazon.com/en-US/docs/alexa/custom-skills/request-types-reference.html#sessionendedrequest)

- The user says "exit" or "quit".
- The user does not respond or says something that does not match an intent defined in your voice interface while the device is listening for the user's response.
- An error occurs.

> The Skill Management API (SMAPI) also allows developers to test their live skills programmatically using the `Simulation API `and `Invocation API `that help create automated tests that can identify bugs and regressions. You can perform end-to-end testing with these APIs to ensure that your skill is functioning as expected.

[What’s New with Request and Response Interceptors in the Alexa Skills Kit SDK for Node.js](https://developer.amazon.com/blogs/alexa/post/0e2015e1-8be3-4513-94cb-da000c2c9db0/what-s-new-with-request-and-response-interceptors-in-the-alexa-skills-kit-sdk-for-node-js)

> _Request interceptors_ are invoked immediately before the execution of the selected handler for an incoming request. You can use them to add any logic that needs to be performed for each request, irrespective of the type of request.

_Response interceptors_ are invoked immediately after execution of the selected request handler. Because response interceptors have access to the output generated from execution of the request handler, they are ideal for tasks such as response sanitization, internationalization, and validation.

```js
const LocalizationInterceptor = {
  process(handlerInput) {
    const localizationClient = i18n.use(sprintf).init({
      lng: handlerInput.requestEnvelope.request.locale,

      overloadTranslationOptionHandler:
        sprintf.overloadTranslationOptionHandler,

      resources: languageStrings,

      returnObjects: true,
    });

    const attributes = handlerInput.attributesManager.getRequestAttributes();

    attributes.t = function (...args) {
      return localizationClient.t(...args);
    };
  },
};
```

```js
.addRequestInterceptors(LocalizationInterceptor)
    .addErrorHandlers(ErrorHandler)
    .lambda();
```

# Skill Simulation API

[Skill Simulation API](https://developer.amazon.com/en-US/docs/alexa/smapi/skill-simulation-api.html)

> The Skill Simulation API enables skill developers to simulate skill execution. You can test your skill and see the intent that a simulated device returns from your interaction model. In the API, the Intent Debugging returns the consideredIntents returned in the JSON response and shows the intents that were considered and discarded.

# Skill Invocation API

[Skill Invocation API](https://developer.amazon.com/en-US/docs/alexa/smapi/skill-invocation-api.html)

> The Skill Invocation API invokes the AWS Lambda or third-party HTTPS endpoint for a specified skill.

> This API is only available for custom skills.

[3 Tips to Troubleshoot Your Custom Alexa Skill's Back End](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/04/3-tips-to-troubleshoot-your-custom-alexa-skill-s-back-end)
