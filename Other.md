[Capture Multiple Sentences](https://stackoverflow.com/questions/36579406/amazon-alexa-capture-full-transcript)

```js
let querySentance = "";
let wordSlots = [
  "WordI",
  "WordII",
  "WordIII",
  "WordIV",
  "WordV",
  "WordVI",
  "WordVII",
  "WordVIII",
  "WordIX",
  "WordX",
  "WordXI",
  "WordXII",
  "WordXIII",
  "WordXIV",
  "WordXV",
  "WordXVI",
  "WordXVII",
  "WordXVIII",
  "WordIXX",
  "WordXX",
  "WordXXI",
  "WordXXII",
  "WordXXIII",
  "WordXXIV",
  "WordXXV",
  "WordXXVI",
  "WordXXVII",
  "WordXXVIII",
  "WordIXXX",
  "WordXXX",
];
wordSlots.forEach((word) => {
  let slot = this.event.request.intent.slots[word];
  if (
    slot !== undefined &&
    slot.value !== "" &&
    slot.value !== "?" &&
    slot.value !== null &&
    slot.value !== undefined
  ) {
    querySentance = querySentance + " " + slot.value;
  }
});
```

[Can we use "AMAZON.SearchQuery" without using "search for" or "find out" phrase?](https://forums.developer.amazon.com/questions/200957/can-we-use-amazonsearchquery-without-using-search.html)
[Remove the requirement for a leading phrase with AMAZON.SearchQuery](https://alexa.uservoice.com/forums/906892-alexa-skills-developer-voice-and-vote/suggestions/34248877-remove-the-requirement-for-a-leading-phrase-with-a)

> Make sure that your skill uses no more than one `AMAZON.SearchQuery` slot per intent. The `Amazon.SearchQuery` slot type cannot be combined with another intent slot in sample utterances.

[AMAZON.SearchQuery Reference](https://developer.amazon.com/docs/custom-skills/slot-type-reference.html#amazonsearchquery)
