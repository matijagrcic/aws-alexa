# AWS Certified Alexa Skill Builder - Specialty

AWS Account

https://aws.amazon.com/free/

Alexa Developer Console

https://developer.amazon.com/alexa/console/ask

## Skill Types

Custom Skills - complete control over the UX, define your own custom interaction model

Smart Home Skills - communicate with smart home devices using prebuilt model

Flash Briefing Skills - short overview of news or other content

Video Skills - provide video content

Music Skills - provide audio content

List Skills - for providing CRUD to a list

## Design Patterns

_Adaptability_ - adaptable skill understands what a user says appropriately

Multiple Utterances
Account for Over-Answering (too much information)
Request Additional Information (re-prompt the user)
Handle Corrections
Plan for Errors (gracefully handle errors, don't use generic responses)
Anticipate for Alexa not understanding (feature not available etc.)

[Be Adaptable](https://developer.amazon.com/en-US/docs/alexa/alexa-design/adaptable.html)

_Personalization_ - personalized skill remembers interactions and information about the user

Custom welcome message (explain the skill for first time, second time say welcome back etc.)
Remember user information
Remember user interactions (persist to database)

[Be Personal](https://developer.amazon.com/en-US/docs/alexa/alexa-design/personal.html)

_Availability_ - available skill guides the user and keeps all options open

Response Time Limits - 8 second time limit for user, prompt after the time limit
Effectively Manage lists - simple options, use [Speech Synthesis Markup Language (SSML)](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html)

Complete Task and End the Session - end session after you fulfill a user's request

[Be Available](https://developer.amazon.com/en-US/docs/alexa/alexa-design/available.html)

_Relatability_ - relatable skill allows the user to feel like they are having a conversation

Don't make it formal, vary responses, use transition and timeline markers

[Be Relatable](https://developer.amazon.com/en-US/docs/alexa/alexa-design/relatable.html)

## Voice Considerations

Think voice first and screen second (not a requirement), provide context and mind the 8 seconds response rule (no information overload)
Leverage Dialog Management
Prepare for the global marketplace (localization)
[Speechcons](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speechcon-reference-interjections-english-us.html) and SSML

> Speechcons are special words and phrases that Alexa pronounces more expressively.

## Skill Design

Define Purpose and Goals
Who are your users?
What can users do with the skill?
What information you need?

> Identify _customer needs_ and how your skill will address those needs

### Steps

Write a script - dialog between Alexa and users
Develop a storyboard - add variations and error cases to the script
Interaction model - use Alexa Skills Kit (ASK) to implement logic and voice interface (Alexa Developer Console and Command Line Interface can be use to define it)

> Custom (complete control) and Pre-built (requests and utterances are defined, less control) interaction models

> Script and storyboard document the information flow

Flow consists of:

- Utterance
- Situation
- Response
- Prompt

### Interaction model

consist of 4 components:

Intents - action that fulfills a user request (leverage built in intents to save time)
Utterances - spoken phrases the user says
Custom Slots - possible values
Dialog Model - defines the steps for multi turn conversation

> When you say Alexa (wake word) everything after is recorded and streamed to the cloud via WiFi. Alexa Voice Service (AVS) consists of Services, APIs and uses Machine Learning and Natural Language Understanding to process the request.

Frontend - Alexa Developer Console (Alexa Skills Kit (ASK))
Backend - AWS or whatever endpoint you prefer (HTTPS), verify is request it from Alexa, adhere to ASK JSON format

### Creation Process

Voice User Interface (VUI)

> defines the intents (user requests) and words (utterances)

Fulfillment Logic (backend, typically LAMBDA)
Connect VUI to Code
Building & Testing (thru console and real device)
Distribution (store, business, personal)
Certification (Amazon tests and verifies)

## Alexa Skills Kit (ASK)

> Collection of APIs, Tools, Documentation and Code Samples

### Skills Creation Tools

#### ASK Command Line Interface (ASK CLI)

[npm ask-cli](https://www.npmjs.com/package/ask-cli)

`bash npm install -g ask-cli`

> uses SMAPI behind the scenes

[ASK CLI Command Reference](https://developer.amazon.com/en-US/docs/alexa/smapi/ask-cli-command-reference.html)

#### Skill Management API (SMAPI)

> Manage your skill programmatically using API root api.amazonalexa.com

#### Alexa Developer Console

> Nice UI for creating skills, instead of using CLI

#### AWS Tools

AWS CodeStar,
AWS CodePipeline,
AWS CloudFormation

#### Skill Flow Builder

> GUI for designers and story writers (content) and developers to implement those

[Set up Skill Flow Builder as a Developer](https://developer.amazon.com/en-US/docs/alexa/custom-skills/set-up-the-skill-flow-builder-as-a-developer.html)

```bash
npm install --global @alexa-games/sfb-cli
npx alexa-sfb
```

```bash
 npx alexa-sfb vscode
 npx alexa-sfb new my_best_story
 npx alexa-sfb simulate <your_project_path>
```

## Invocation Name

> Only used for Custom Skill, not needed for prebuilt model

[Invocation Name Requirements](https://developer.amazon.com/en-US/docs/alexa/custom-skills/choose-the-invocation-name-for-a-custom-skill.html#cert-invocation-name-req)

Invoking using:

- IntentRequest (Alexa - tell APP to do something)
- LaunchRequest (no intent - Alexa open App)
- CanFulfillIntentRequest (no name, Alexa searches for a skill to match request)

> Intent is an action that fulfills user's request (has a NAME and list of UTTERANCES)

2 types of Intents:

- Built-in

Standard
_CancelIntent_
_HelpIntent_
_StopIntent_
_FallbackIntent (no match)_
NextIntent
YesIntent
NoIntent
PauseIntent
SearchAction (lookup information)

Standard with screen
_NavigateHomeIntent_ (ends skill session, user leaves the skill)

[Standard Built-in Intents](https://developer.amazon.com/en-US/docs/alexa/custom-skills/standard-built-in-intents.html)

- Custom (complete control)

> Slot(s) are values passed to the utterance

[Slot Type Reference](https://developer.amazon.com/en-US/docs/alexa/custom-skills/slot-type-reference.html)

## Interfaces

Audio Player - streaming audio and monitoring playback
Display/ DisplayTemplate
Video App - streaming video files
GadgetController / GameEngine
CanFulfillIntentRequest - no name
Alexa Presentation Language
Auto Delegation / Dialog

[List of Alexa Interfaces and Supported Languages](https://developer.amazon.com/en-US/docs/alexa/device-apis/list-of-interfaces.html)

## Request Types

- LaunchRequest - opening the skill
- IntentRequest - sent when intent corresponds with user query
- SessionEndedRequest - when session ends (any reason)
- CanFulFillIntentRequest - when Alexa is querying if there is a skill that can fulfill the intent (can opting but then need to implement it for all intents)

## Handlers

Request Handlers - handle incoming request and response
Exception Handlers - for errors
Handler Classes - implement the abstract class `AbstractRequestHandler` and its two methods, `can_handle()` and `handle()`

> Leverage userId and deviceId for personalization and segmentation along with DynamoDB

## Screen Devices

[Available standard built-in intents for Alexa-enabled devices with a screen](https://developer.amazon.com/en-US/docs/alexa/custom-skills/standard-built-in-intents.html#built-in-intents-echo-show)

> Must implement Amazon.PreviousIntent and Amazon.NextIntent

Card types:

- Simple (title and content)
- Standard (title, text and image)
- Linked Account
- AskForPermissionsConsent

[Cards displayed on Alexa-enabled devices with a screen](https://developer.amazon.com/en-US/docs/alexa/custom-skills/best-practices-for-skill-card-design.html#types-of-cards)

[When to include cards, and how often?](https://developer.amazon.com/en-US/docs/alexa/custom-skills/best-practices-for-skill-card-design.html#when-to-include-cards-and-how-often)

> _Limit the number of cards_ Too many will take the user out of the voice experience. Avoid pushing cards with every response, unless it is absolutely necessary.

> For screen devices, voice should remain the primary form of interaction, and as much as possible, the user should be able to navigate through the skill strictly by voice.

Display templates:

- Body Templates (1 - 7) - can't select images
- List Templates () - can select images
- Images

[Display Template Reference](https://developer.amazon.com/en-US/docs/alexa/custom-skills/display-template-reference.html)

[Display Interface Reference](https://developer.amazon.com/en-US/docs/alexa/custom-skills/display-interface-reference.html#display-templates-for-skills-that-support-screen-display)

> Display Template is used if both Display Template and Card are in the response

> check the `{device: supportedInterfaces}`

## Alexa Presentation Language (APL)

> Offer more control than Display Template(s)

[Understand Alexa Presentation Language (APL)](https://developer.amazon.com/en-US/docs/alexa/alexa-presentation-language/understand-apl.html)

## Speech Synthesis Markup Language (SSML)

[Supported SSML tags](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html#ssml-supported)

> Leverage _Voice & Tone_ tab to experiment with SSML tags

[PlaybackController](https://developer.amazon.com/en-US/docs/alexa/device-apis/alexa-playbackcontroller.html)

> The Alexa.PlaybackController interface describes messages that are used to play, stop, and _navigate_ playback for audio or video content.
