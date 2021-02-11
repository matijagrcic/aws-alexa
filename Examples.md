# Store last access time

```js
const attributesManager = handlerInput.attributesManager;
const persistentAttributes = await attributesManager.getPersistentAttributes();
const userIdTail = handlerInput.requestEnvelope.session.user.userId.substr(-6);
let speechOutput = `I've saved now as the last access time. Your user id ends with <say-as interpret-as='spell-out'>${userIdTail}</say-as>.`;

if (persistentAttributes.lastAccessTime) {
  // not the first time accessing the skill, so share the saved info
  const lastTime = parseInt(persistentAttributes.lastAccessTime, 10);
  const thisTime = Date.now();
  const difference = (thisTime - lastTime) / 1000;

  speechOutput = `The last time you accessed this skill was ${difference} seconds ago. ${speechOutput}`;
}

persistentAttributes.lastAccessTime = Date.now();
attributesManager.setPersistentAttributes(persistentAttributes);
await attributesManager.savePersistentAttributes();
```

# Skill Disabled so delete persistent data

```js
const SkillDisabledEventHandler = {
  canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === "AlexaSkillEvent.SkillDisabled";
  },
  handle(handlerInput) {
    console.log(JSON.stringify(handlerInput.requestEnvelope));
    const userId = handlerInput.requestEnvelope.context.System.user.userId;
    console.log(`skill was disabled for user: ${userId}`);
    if (
      handlerInput.requestEnvelope.request.body
        .userInformationPersistenceStatus === "NOT_PERSISTED"
    ) {
      handlerInput.attributesManager.deletePersistentAttributes();
    }
  },
};
```

```json
// skill.json
"subscriptions": [
        {
          "eventName": "SKILL_DISABLED"
        }
      ]
```
