[Alexa Live On-Demand](https://build.amazonalexadev.com/Alexa-Live-on-Demand-1.html)

[![Build Conversational Interfaces Faster with Alexa Conversations](https://img.youtube.com/vi/r_r2OrdMr0Y/0.jpg)](https://www.youtube.com/watch?v=r_r2OrdMr0Y)

Released in 2014
Over 100k Skills on Alexa
4-5 customers that have Echo devices uses Skills
Skills are available in 80 countries, 30 language variants

One-shot interactions
Multi-turn interactions (series of questions)

Happy path
-single dialog turn
-linear multi turn (easy to build)

Not a happy path
-single dialog turn
-non-linear multi turn, conversations deviate from the script (tracking state, context)

Alexa Conversations - deep learning, tracks the context, less code for state management

Alexa CConversations - opens up new experiences for your customers

## Build a skill with Alexa Conversations

Default Dialog Manager
Custom Skill Dialog Manager (portion of the dialog)

5 build-time components

Dialogs
Utterance Set (dialog acts - Invoke, Inform, Affirm)
Slots (singular slot, compound slot)
API definitions
Response Templates (dialog acts - Request, Confirm, Notify)

## JSON request

Request type
API name
API arguments

## JSON response

API response slot

Pros
State management out of the box
Confirmations
User corrections (user changes their mind while defining)
Proactive offers
Interoperability (extend existing Alexa skill with Alexa Conversations)

## Technical Details

Dialog Simulator consists of simulated dialog flows which produce dialog with variations
Using paraphrasing the natural language variations are generated
Last step is to train the dialogs

Goal Oriented dialog (take turns and preform actions, Alexa follow up with questions to get more information)

### Simulating different dialog paths in advanced

User more cooperative (gives all information)
User changes their mind (not sure)
User is less cooperative (gives less information)

### Conversational models

NER (named entity recognition) model (recognizes slots in user utterances)
AP (action prediction) model (predicts what is the next Alexa model)
AF (argument filling) model (fills in the values of API arguments from the dialog context)

## Benefits

Easier to capture and handle user corrections
Less time spent for writing slots and confirming new slots
Easy to extend existing skill

## Useful docs

Reference skills
[alexa.design/ac-github](alexa.design/ac-github)
Technical documentation for Alexa Conversations
[alexa.design/ac-docs](alexa.design/ac-docs)
Learn the fundamentals of building with Alexa CConversations
[alexa.design/ac-tutorial](alexa.design/ac-tutorial)

[![The Secret to Building Better Customer Experiences](https://img.youtube.com/vi/vPedk_ZqW_s/0.jpg)](https://www.youtube.com/watch?v=vPedk_ZqW_s)

## Tools

[NLU Evolution](https://developer.amazon.com/en-US/docs/alexa/custom-skills/batch-test-your-nlu-model.html)
[Utterance Profiler](https://developer.amazon.com/en-IN/docs/alexa/custom-skills/test-utterances-and-improve-your-interaction-model.html)
[Intent Chaining](https://developer.amazon.com/en-US/blogs/alexa/alexa-skills-kit/2019/03/intent-chaining-for-alexa-skill)

ASR (automatic speech recognition) - converts user speech to text
[Automatic Speech Recognition (ASR) Evaluation tool](https://developer.amazon.com/en-IN/docs/alexa/asr/about-asr.html)

> ASR evaluation tools saves time testing your skill

Out of Domain utterances

Sensitivity Tuning - review your customer's utterances in Intent History

Change fallbackIntentSensitivity setting level:

Low - your skill requires large numbers of different words and phrases that might not be in your sample utterances
Medium - specific utterances are covered by your skill model
High - interaction model supports most utterances

## Slots and Catalog Management

> allows richer and more consistent experiences

Shared Slots - share slot with multiple skills
Catalog Management -

## Alexa Entities

Resolve common entities (more detail about the utterance, giving a slot link)

[http://alexa.design/entities](http://alexa.design/entities)

## Personalize Alexa

> More personalization, more engagement

3 different ways of personalization:

Account Linking
Customer Profile API (fetch user details)
Voice profiles

App-to-App Account Linking (from your app or Alexa App)

> link Amazon identity with the identity in your app (removes friction of remembering account credentials, both on iOS and Android)

## Account linking from Alexa App

Enable Universal Links (iOS), App Links (Android)
Configure the skill for account linking
Handle the authorization request in your app
Redirect the user back to the Alexa App
Use the access token in the skill

## Person Profile API

Enable permissions
Prompt the user to give consent
Get the access token (refresh on each request)
Call Personal Profile API

# Tool

[Alexa Skills Toolkit for Visual Studio Code](https://github.com/alexa/ask-toolkit-for-vscode)
