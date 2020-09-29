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

_Personalization_ - personalized skill remembers interactions and information about the user

Custom welcome message (explain the skill for first time, second time say welcome back etc.)
Remember user information
Remember user interactions (persist to database)

_Availability_ - available skill guides the user and keeps all options open

Response Time Limits - 8 second time limit for user, prompt after the time limit
Effectively Manage lists - simple options, use [Speech Synthesis Markup Language (SSML)](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html)

Complete Task and End the Session - end session after you fulfill a user's request

_Relatability_ - relatable skill allows the user to feel like they are having a conversation

Don't make it formal, vary responses, use transition and timeline markers

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

[Invocation Name Requirements](https://developer.amazon.com/en-US/docs/alexa/custom-skills/choose-the-invocation-name-for-a-custom-skill.html#cert-invocation-name-req)

Invoking using:

- IntentRequest
- LaunchRequest (no intent)
- CanFulfillIntentRequest (no name)
