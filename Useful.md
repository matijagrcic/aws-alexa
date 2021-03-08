[Alexa Skills Kit Blog](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit)

[Alexa Design Guide](https://developer.amazon.com/en-US/docs/alexa/alexa-design/get-started.html)

# Account Linking

[Understand Account Linking for Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/account-linking/understand-account-linking.html)

[How to Set Up Alexa Account Linking with Amazon Cognito User Pools to Create a Personalized Customer Experience](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/11/how-to-set-up-alexa-account-linking-with-amazon-cognito-user-pools-to-create-a-personalized-customer-experience)

[Amazon Cognito - Post Confirmation Lambda Trigger](https://docs.amazonaws.cn/en_us/cognito/latest/developerguide/user-pool-lambda-post-confirmation.html)

[Calling DynamoDB using AWS Cognito triggers](https://docs.amplify.aws/guides/functions/cognito-trigger-lambda-dynamodb/q/platform/js)

[AWS SDK for JavaScript CognitoIdentityProvider](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-cognito-identity-provider/index.html)

# Reminders API

[Remind Customers of Important Tasks or Events with the Reminders API](https://developer.amazon.com/blogs/alexa/post/e65a0e17-2716-4714-8d02-a50210fdd494/now-available-enable-reminders-for-your-skills-with-alexa-reminders-api)

[Integrate the Reminders API with Your Skill to Deepen Customer Engagement](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/08/integrate-the-reminders-api-with-your-skill-to-deepen-customer-engagement1)

[Alexa Reminders Overview](https://developer.amazon.com/en-US/docs/alexa/smapi/alexa-reminders-overview.html)

[Alexa Reminders API Reference](https://developer.amazon.com/en-US/docs/alexa/smapi/alexa-reminders-api-reference.html)

[Skill Events in Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/smapi/skill-events-in-alexa-skills.html#use-events-in-your-skill-service)

[![Reminders API](https://img.youtube.com/vi/2OtvOeo0fqQ/0.jpg)](https://www.youtube.com/watch?v=2OtvOeo0fqQ)

[![Integrate the Reminders API with Your Skill to Deepen Customer Engagement](https://img.youtube.com/vi/eF7R4BEFu5c/0.jpg)](https://www.youtube.com/watch?v=eF7R4BEFu5c)

# Proactive Events API

> pre-defined set of schemas that you can leverage to set up your skill service to use proactive events. Your skill can send proactive events information that conforms to a schema via the Skill Management API (SMAPI) as part of a skill manifest. Each schema has a predefined template that represents the text that Alexa reads back to the customer.

[Proactive Events API Reference](https://developer.amazon.com/en-US/docs/alexa/smapi/proactive-events-api.html)

[Alexa Proactive Events API](https://github.com/alexa/alexa-cookbook/tree/master/feature-demos/skill-demo-proactive-events)

[Proactive Events Sender (beta)](https://proactive.voicefirst.tools/)

[Get started with Amazon Alexa Skills Proactive Events API](https://medium.com/swlh/get-started-with-amazon-alexa-skills-proactive-events-api-5b082bcb282c)

[![Get started with Amazon Alexa Skills Proactive Events API](https://img.youtube.com/vi/6Ul_ry2hq2w/0.jpg)](https://www.youtube.com/watch?v=6Ul_ry2hq2w)

[Interface ProactiveSubscriptionChangedRequest](http://ask-sdk-node-typedoc.s3-website-us-east-1.amazonaws.com/interfaces/events.skillevents.proactivesubscriptionchangedrequest.html#body)

[How to Add the ProactiveEvents API to Your Existing Alexa Skill](https://developer.amazon.com/blogs/alexa/post/a01f8f67-60f8-4f1b-9f9e-70f7bfe8e38b/how-to-add-the-proactiveevents-api-to-your-existing-alexa-skill)

[How to Send Media Event Notifications to Your Alexa Skill Customers with the ProactiveEvents API](https://developer.amazon.com/blogs/alexa/post/bbf23596-766a-4e7c-8d74-cbfc234b6791/how-to-send-media-event-notifications-to-your-alexa-skill-customers)

[Proactive Events API](https://www.jovo.tech/docs/v2/amazon-alexa/proactive-events)

## Things to check

- the `skill.json` has the right event(s) listed as being published
- the device locale matches one of the locales included in the message
- the customer id (userId) is correct - it normally will change each time you disable/re-enable the skill

# Alexa Skill Events

[Skill Events in Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/smapi/skill-events-in-alexa-skills.html)
[Alexa Skill Events](http://ask-sdk-node-typedoc.s3-website-us-east-1.amazonaws.com/modules/events.skillevents.html)

- AccountLinkedBody
- AccountLinkedRequest
- Permission
- PermissionAcceptedRequest
- PermissionBody
- PermissionChangedRequest
- ProactiveSubscriptionChangedBody
- ProactiveSubscriptionChangedRequest
- ProactiveSubscriptionEvent
- SkillDisabledRequest

# Settings API

[Personalize Your Alexa Skill with Customer-Specific Time Zones and Measurements Using the Alexa Settings API](https://developer.amazon.com/blogs/alexa/post/c2ba44fa-4bd8-4b49-925d-29dbc0330b1e/personalize-your-alexa-skill-with-customer-specific-time-zones-and-measurements-using-the-alexa-settings-api)

[Using the Alexa Settings API to Look Up the Device Time Zone](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/07/getting-started-with-cake-time-using-the-alexa-settings-api-to-look-up-the-device-time-zone)

[UserVoice](https://alexa.uservoice.com/forums/906892-alexa-skills-developer-voice-and-vote/suggestions/33147373-provide-device-timezone-in-alexa-requests)

# Skill Messaging API

[Skill Messaging API Reference](https://developer.amazon.com/en-US/docs/alexa/smapi/skill-messaging-api-reference.html)

> The Skill Messaging API is used to send message requests to skills.

# Service API

[Calling Alexa Service APIs](https://developer.amazon.com/en-US/docs/alexa/alexa-skills-kit-sdk-for-nodejs/call-alexa-service-apis.html#apiclient)

[Get the user current time from your Alexa Skill](https://medium.com/@cpenarrieta/one-way-to-get-the-user-current-time-from-your-alexa-skill-88b6d2b1aecf)

```js
const getCurrentDate = async (handlerInput) => {
  const serviceClientFactory = handlerInput.serviceClientFactory;
  const deviceId = handlerInput.requestEnvelope.context.System.device.deviceId;

  try {
    const upsServiceClient = serviceClientFactory.getUpsServiceClient();
    return (userTimeZone = await upsServiceClient.getSystemTimeZone(deviceId));
  } catch (error) {
    if (error.name !== "ServiceError") {
      return handlerInput.responseBuilder
        .speak("There was a problem connecting to the service.")
        .getResponse();
    }
    console.log("error", error.message);
  }
};
```

```js
const skillBuilder = Alexa.SkillBuilders.custom();
exports.handler = skillBuilder
	.addRequestHandlers(...)
    .withApiClient(new Alexa.DefaultApiClient())
	.withSkillId(...)
	.lambda();
```

> When you use `.standard()` Skill Builder instead of the `.custom()` one, you _ don't need to_ include `.withApiClient(new Alexa.DefaultApiClient())`. The Standard includes it by default.
> [Ref](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs/issues/356)

[Device Settings Demo](https://github.com/alexa/alexa-cookbook/blob/master/feature-demos/skill-demo-device-settings/lambda/custom/index.js)

```js
export const getUnixTimestampForTimeZone = (deviceTimeZone: string) => {
  dayjs.extend(utc);
  dayjs.extend(timezone);
  return dayjs().tz(deviceTimeZone).valueOf();
};
```

[List of tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

# Location Services

[Enhance Your Customer Experience with Real-Time Location Services for Alexa Skills](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2018/12/location-services-launch)

[Use Location Services for Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/custom-skills/location-services-for-alexa-skills.html)

> If `context.Geolocation.locationServices.access` is "ENABLED" and `context.Geolocation.locationServices.status` is "RUNNING", then the device is sharing location.

> For stationary devices like the Amazon Echo, Alexa can provide you the device's physical address with the Device Address API. _Stationary devices do not provide geo-coordinate data through location services._

[New Location Services Permissions Inconsistency](https://forums.developer.amazon.com/questions/194325/new-location-services-permissions-inconsistency.html)

```js
const LOCATION_SERVICES_PERMISSION = ["alexa::devices:all:geolocation:read"];

const [permission] = LOCATION_SERVICES_PERMISSION;
if (!isPermissionGranted(handlerInput, permission)) {
  return responseBuilder
    .speak(
      "Location Services permission is required to use this feature. Please enable it in the Alexa app."
    )
    .withAskForPermissionsConsentCard(LOCATION_SERVICES_PERMISSION)
    .getResponse();
}

/**
 * @param {Object} handlerInput Alexa handlerInput object
 * @param {String} permission Alexa Skill permission to check for
 * @returns {Boolean} true if permission is granted. false if it is not
 * @description checks to see if the desired Skill permission is granted
 */
function isPermissionGranted(handlerInput, permission) {
  const {
    requestEnvelope: {
      context: {
        System: { user },
      },
    },
  } = handlerInput;
  return (
    user.permissions &&
    user.permissions.scopes &&
    user.permissions.scopes[permission] &&
    user.permissions.scopes[permission].status === "GRANTED"
  );
}
```

[New Permissions Card for Requesting Customer Consent](https://developer.amazon.com/en-US/docs/alexa/custom-skills/device-address-api.html#permissions-card)

```js
//determine if the device is capable of supporting location services
var isGeolocationSupported =
  context.System.device.supportedInterfaces.Geolocation;

var lat = geo.coordinate.latitudeInDegrees;
var lng = geo.coordinate.longitudeInDegrees;
```

[Developing Location-Aware Alexa Skills](https://developer.here.com/blog/developing-location-aware-alexa-skills)

[AMAZON.YesIntent and AMAZON.NoIntent Now Compatible with ASK Dialog Management Features](https://developer.amazon.com/blogs/alexa/post/ea90c23d-42e2-46ee-8a2f-0df749030a3b/amazon-yesintent-and-amazon-nointent-now-compatible-with-ask-dialog-management-features)

[Using Yes/No Intents with Dialog Management](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2018/04/using-yes-no-intents-with-dialog-management)

# Intent Request History API

[Intent Request History API](https://developer.amazon.com/en-US/docs/alexa/smapi/intent-request-history.html)

> Collect all user utterance provided to your skill on a daily basis but your skill must have at least 10 unique users per locale in a day, in order for data to be available for that locale for that day

# FallbackIntent

> AMAZON.FallbackIntent in the Alexa Skills Kit (ASK) built-in library helps you handle unexpected utterances, or when a customer says something that doesn’t map to any intents in your skill
> aka “out-of-domain requests.”

[The Built-In FallbackIntent, PhoneNumber Slot (Beta), and Ordinal Slot (Beta) Get Expanded Locale Support](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/11/handle-unexpected-user-requests-with-FallbackIntent-phonenumber-ordinal-built-in-slots-expanded)

> There is no way to capture the utterance that triggered the FallbackIntent.

[Use the New Fallback Intent to Respond Gracefully to Unexpected Customer Requests](https://developer.amazon.com/blogs/alexa/post/c97f3bb7-9701-41e8-ac06-a3a44b9f1638/use-the-new-fallback-intent-to-respond-gracefully-to-unexpected-customer-requests)

[Code First Alexa Skill Development With VS Code and the ASK SDK Controls Framework](https://dzone.com/articles/code-first-alexa-skill-development-with-vs-code-an)
