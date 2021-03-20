[Manage the Skill Session and Session Attributes](https://developer.amazon.com/en-US/docs/alexa/custom-skills/manage-skill-session-and-session-attributes.html)

```js
const sessionAttributes = handlerInput.attributesManager.getSessionAttributes();
const favoriteColor = getSlotValue(
  handlerInput.requestEnvelope,
  "favoriteColor"
);
sessionAttributes.favoriteColor = favoriteColor;
handlerInput.attributesManager.setSessionAttributes(sessionAttributes);

const sessionAttributes = handlerInput.attributesManager.getSessionAttributes();
if (sessionAttributes.favoriteColor) {
  //do something
}
```

[Managing Attributes](https://developer.amazon.com/en-US/docs/alexa/alexa-skills-kit-sdk-for-nodejs/manage-attributes.html)

[How to Use Session Attributes in Your Alexa Skill to Enhance the Voice Experience](https://developer.amazon.com/blogs/alexa/post/08edaa00-59e2-46b7-aace-4080f2a87450/using-session-attributes-in-your-alexa-skill-to-enhance-the-voice-experience)

[Alexa Skill Recipe: Using Session Attributes to Enable Repeat Responses](https://developer.amazon.com/blogs/alexa/post/2279543b-ed7b-48b4-a3aa-d273f7aab609/alexa-skill-recipe-using-session-attributes-to-enable-repeat-responses)
