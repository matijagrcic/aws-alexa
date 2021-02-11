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
