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
