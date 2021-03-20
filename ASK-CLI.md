[Manage Credentials with ASK CLI](https://developer.amazon.com/en-US/docs/alexa/smapi/manage-credentials-with-ask-cli.html)

[ASK CLI Command Reference](https://developer.amazon.com/en-GB/docs/alexa/smapi/ask-cli-command-reference.html#smapi-command)

```bash
ask clone -s amzn1.ask.skill.XXXXXXX-XXXX-XXX-XXXX-XXXXXXXXXXXX -p ProfileName

ask configure --profile ProfileName --aws-setup

ask init --hosted-skill-id amzn1.ask.skill.XXXXXXX-XXXX-XXX-XXXX-XXXXXXXXXXXX

ask smapi update-skill-manifest -g development -s

amzn1.ask.skill.XXXXXXX-XXXX-XXX-XXXX-XXXXXXXXXXXX --manifest "$(cat skill-manifest.json)"

ask smapi get-skill-manifest -s amzn1.ask.skill.XXXXXXX-XXXX-XXX-XXXX-XXXXXXXXXXXX -g development > skillmanifest.json

```

```bash
set ASK_DEFAULT_PROFILE="ProfileName"
```
