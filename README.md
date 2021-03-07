# aws-alexa

# Alexa Hosted Skills

[Build a Skill End-to-end Using an Alexa-hosted Skill](https://developer.amazon.com/en-US/docs/alexa/hosted-skills/build-a-skill-end-to-end-using-an-alexa-hosted-skill.html)

[Use Personal AWS Resources with Your Alexa-hosted Skill](https://developer.amazon.com/en-US/docs/alexa/hosted-skills/alexa-hosted-skills-personal-aws.html)

[Use DynamoDB for Data Persistence with Your Alexa-hosted Skill](https://developer.amazon.com/en-US/docs/alexa/hosted-skills/alexa-hosted-skills-session-persistence.html)

```js
.withPersistenceAdapter(
        new ddbAdapter.DynamoDbPersistenceAdapter({
            tableName: process.env.DYNAMODB_PERSISTENCE_TABLE_NAME,
            createTable: false,
            dynamoDBClient: new AWS.DynamoDB({apiVersion: 'latest', region: process.env.DYNAMODB_PERSISTENCE_REGION})
        })
    )
```

> Can't locally debug as you cannot get `accessKeyId` and `secretAccessKey` when using Alexa Hosted Skill given hosted skill service manage all the resources and
> there is no way to get the credential.

[Ref](https://github.com/alexa/alexa-skills-kit-sdk-for-nodejs/issues/684)
[Access key ID and secret access key](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html#cli-configure-quickstart-creds)

# Beta Testing

[Skill Beta Testing for Alexa Skills](https://developer.amazon.com/en-US/docs/alexa/custom-skills/skills-beta-testing-for-alexa-skills.html#h2_create-test-for-skill)
