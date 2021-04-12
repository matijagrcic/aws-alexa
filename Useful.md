[Alexa Skills Kit Blog](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit)

[Alexa Design Guide](https://developer.amazon.com/en-US/docs/alexa/alexa-design/get-started.html)

# Account Linking

> Your system must support OAuth 2.0 and the authorization code grant type.

[Understand Account Linking for Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/account-linking/understand-account-linking.html)

[How to Set Up Alexa Account Linking with Amazon Cognito User Pools to Create a Personalized Customer Experience](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/11/how-to-set-up-alexa-account-linking-with-amazon-cognito-user-pools-to-create-a-personalized-customer-experience)

[Amazon Cognito - Post Confirmation Lambda Trigger](https://docs.amazonaws.cn/en_us/cognito/latest/developerguide/user-pool-lambda-post-confirmation.html)

[Calling DynamoDB using AWS Cognito triggers](https://docs.amplify.aws/guides/functions/cognito-trigger-lambda-dynamodb/q/platform/js)

[AWS SDK for JavaScript CognitoIdentityProvider](https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-cognito-identity-provider/index.html)

[Validate and Use Access Tokens in Custom Skill Code](https://developer.amazon.com/en-US/docs/alexa/account-linking/add-account-linking-logic-custom-skill.html#validate-token)

For a request that requires authentication, your code should do at least two checks:

- Verify that the accessToken exists.
- Verify that the token represents a valid user in your resource server.

```js
exports.handler = async (event, context) => {
  let date = new Date();

  const tableName = process.env.TableName;
  const region = process.env.Region;

  console.log(`Table: ${tableName} Region: ${region}`);

  AWS.config.update({ region: "REGION" });

  // If the required parameters are present, proceed
  if (event.request.userAttributes.sub) {
    let ddbParams = {
      TableName: tableName,
      Item: {
        id: { S: event.request.userAttributes.sub },
        UserEmail: { S: event.request.userAttributes.email },
        given_name: { S: event.request.userAttributes.given_name },
        family_name: { S: event.request.userAttributes.family_name },
        address: { S: event.request.userAttributes.address },
        phone_number: { S: event.request.userAttributes.address },
        createdAt: { S: date.toISOString() },
      },
    };

    // Call DynamoDB
    try {
      await ddb.putItem(ddbParams).promise();
      console.log("Success");
    } catch (err) {
      console.log("Error", err);
    }
    console.log("Success: Everything executed correctly");
    context.done(null, event);
  } else {
    // Nothing to do, the user's email ID is unknown
    context.done(null, event);
  }
};
```

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

```js
import got from "got";
import {
  AlexaClientId,
  AlexaClientSecret,
  AlexaUserId,
  proactiveEventsApi,
} from "./config";

function getMediaContentAvailableSchema(userId: string, message: string) {
  let timestamp = new Date();
  let expiryTime = new Date();
  expiryTime.setMinutes(expiryTime.getMinutes() + 60);

  let referenceId = `ReferenceIdPairing-${new Date().getTime()}`;

  const mediaContentJson = {
    timestamp: timestamp.toISOString(),
    referenceId: referenceId,
    expiryTime: expiryTime.toISOString(),
    event: {
      name: "AMAZON.MediaContent.Available",
      payload: {
        availability: {
          startTime: timestamp,
          provider: {
            name: "localizedattribute:providerName",
          },
          method: "RELEASE",
        },
        content: {
          name: "localizedattribute:contentName",
          contentType: "GAME",
        },
      },
    },
    localizedAttributes: [
      {
        locale: "en-GB",
        providerName: "Provider Name",
        contentName: message,
      },
    ],
    relevantAudience: {
      type: "Unicast",
      payload: {
        user: userId,
      },
    },
  };

  return mediaContentJson;
}

const getToken = async () => {
  try {
    const response = await got.post("https://api.amazon.com/auth/o2/token", {
      json: true,
      headers: {
        "Content-Type": "application/x-www-form-urlencoded",
      },
      body: {
        grant_type: "client_credentials",
        client_id: AlexaClientId,
        client_secret: AlexaClientSecret,
        scope: "alexa::proactive_events",
      },
      form: true,
    });

    // {
    //     access_token: 'Atc|XXXXXXXXXXXXXXXXXXXXXXXXX',
    //     scope: 'alexa::proactive_events',
    //     token_type: 'bearer',
    //     expires_in: 3600
    // }
    const tokenRequestId = response.headers["x-amzn-requestid"];
    console.log(`Token requestId: ${tokenRequestId}`);
    const accessToken = response.body.access_token;
    console.log(`accessToken: ${accessToken}`);

    return accessToken;
  } catch (error) {
    return error.response.body;
  }
};

const sendEvent = async (token: string, userId: string, message: string) => {
  try {
    const response = await got.post(
      proactiveEventsApi.development.northAmerica.url,
      {
        json: true,
        headers: {
          "Content-Type": "application/json",
          Authorization: `Bearer ${token}`,
        },
        body: getMediaContentAvailableSchema(userId, message),
      }
    );

    if ([200, 202].includes(response.statusCode)) {
      console.log("successfully sent event");
      console.log(`requestId: ${response.headers["x-amzn-requestid"]}`);
    } else {
      console.log(`Error https response: ${response.statusCode}`);
      console.log(`requestId: ${response.headers["x-amzn-requestid"]}`);

      if ([403].includes(response.statusCode)) {
        console.log(`userId ${userId} may not have subscribed to this event.`);
      }
    }
  } catch (error) {
    return error.response.body;
  }
};

async function notify(userId: string, message: string) {
  const token = await getToken();
  const status = await sendEvent(token, userId, message);

  return status;
}

notify(AlexaUserId, "Your device has been paired").then((p) => console.log(p));
```

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

[Obtain Customer Settings Information with the Alexa Settings API](https://developer.amazon.com/en-US/docs/alexa/smapi/alexa-settings-api-reference.html)

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

[Location-aware Alexa Skills with HERE Location Services](https://developer.here.com/tutorials/alexa-hls/)

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

[5 Common Error Messages for Custom Alexa Skills and How to Troubleshoot Them](https://developer.amazon.com/blogs/alexa/post/0d8c5234-3c7a-4b77-9906-b43a5310bde4/5-common-error-messages-for-custom-alexa-skills-and-how-to-troubleshoot-them)

Alexa: "There was a problem with the requested skill's response." - response JSON your skill sent back was malformed  
Alexa: "Unable to reach the requested skill" - Alexa is unable to hit your endpoint

[Lambda functions and custom skills](https://developer.amazon.com/en-US/docs/alexa/custom-skills/host-a-custom-skill-as-an-aws-lambda-function.html#about-lambda-functions-and-custom-skills)

> You do not need to verify that requests are coming from the Alexa service yourself. Access to execute your function is controlled by permissions within AWS instead.

> It is recommended that you also enable skill ID verification for the function and provide the skill ID (also called the application ID) for your skill. This means your function can be invoked only if the skill ID in the Alexa Skills Kit request matches the skill ID configured in the trigger.When using skill ID verification, you do not need to include code to verify that the request is intended for your service. Requests from unverified skills do not invoke your function.

[Progressive Response](https://developer.amazon.com/en-US/docs/alexa/custom-skills/send-the-user-a-progressive-response.html)

> Progressive response is interstitial SSML content (including text-to-speech and short audio) that Alexa plays while waiting for your full skill response.

# Extend a Built-in Intent with Sample Utterances

[Extend a Built-in Intent with Sample Utterances](https://developer.amazon.com/en-US/docs/alexa/custom-skills/implement-the-built-in-intents.html#extending)

> You can extend the standard built-in intents by providing additional sample utterances. This is useful for invoking the intents with skill-specific utterances.

> You cannot extend any of the other built-in intents, such as WeatherForecast or LocalBusiness.

[Available standard built-in intents for Alexa-enabled devices with a screen](https://developer.amazon.com/en-US/docs/alexa/custom-skills/standard-built-in-intents.html#built-in-intents-echo-show)

[AWS Certified Alexa Skill Builder – Specialty (AXS-C01) Exam Learning Path](https://jayendrapatil.com/aws-certified-alexa-skill-builder-specialty-axs-c01-exam-learning-path/)

# Request and Response JSON Reference

[Request and Response JSON Reference](https://developer.amazon.com/en-US/docs/alexa/custom-skills/request-and-response-json-reference.html)

[Request Types Reference (LaunchRequest, CanFulfillIntentRequest, IntentRequest, SessionEndedRequest)](https://developer.amazon.com/en-US/docs/alexa/custom-skills/request-types-reference.html)

# Delegate the Dialog to Alexa

[Delegate the Dialog to Alexa](https://developer.amazon.com/en-US/docs/alexa/custom-skills/delegate-dialog-to-alexa.html)
