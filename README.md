# Searcho-tutorial-

### Inspiration
Personally, there has been so many times when we found ourselves naviagting through a website and found it hard/time consuming to do so with websites constantly evolving and trying to figure out how to get to the right page to do the most basic things


## Overview

In this tutorial, we will be creating a search app powered by natural language processing(nlp). It uses the power of NLP to search through pages of any website. It will help you to find any page very fast. The key things we will explore is how to:

*   Design the user interaction
*   Create and train a Wit app to do natural language processing (NLP)
*   Integrate Wit with your Api
*   Serve the response using reactjs

## Prerequisites
*   Download and install [nodejs](https://nodejs.org/en/)
*   Create a [Wit.ai](https://wit.ai/) account


## Design the User Interaction

When designing applications with voice interactions, it's important to understand the various ways that a user may interact with your app. Some techniques that can help with modeling the conversation is writing a script or creating a flow diagram. For our greeting app, let's write a script to outline it.

Let's consider the following conversation as the happy path:
```

```

Now let's think about scenarios were the user can deviate:
```

```

There are many other scenarios to consider as well, but for the tutorial let's just focus on these.

## Add an introduction to your Android app

Import the [Wit.ai Voice demo base-setup](https://github.com/wit-ai/android-voice-demo/tree/base-setup) into Android Studio and open **app** > **src** > **main** > **java** > **com.facebook.witai.voicedemo** > **MainActivity.java**.

Next update `initializeTextToSpeech` function to include the introduction announcement as follows:

```java

```

## Training your Wit app to do natural language processing (NLP)

Now that the Android app can speak the introduction, let’s train our Wit app to process the user’s response to the app.

1. Go to [Wit.ai](https://wit.ai/).
2. Create a new Wit.ai app:
    1. Enter a name e.g. _VoiceDemo_
    2. Select **English**
    3. Select **Open** or **Private** for visibility
    4. Click **Create**.
3. Add an utterance:
    1. Make sure you are on the **Train Your App** page by selecting **Understanding** from the left-hand menu.
    1. Type _My name is Pan_ into the **Utterance** text box.
    2. Label an entity in the utterance by highlighting _Pan_ with your mouse and select `wit/contact` as the Entity type.
4. Add an intent
    1. Click on the **Intent** dropdown.
    2. Enter _Greeting_Intent_ as the name of your new Intent.
    3. Click **Create Intent**.
5. Submit your first utterance by clicking **Train and Validate**. The training should start within a few seconds - you can see the training status in the top right.

![Gif to demo steps to train your Wit app for the Greeting Intent](https://github.com/wit-ai/android-voice-demo/blob/master/wit-training-greeting-intent.gif)

You might have heard that the most important part of machine learning is the training data. At this point, we’ve only provided our Wit app with one data point, so let's think of natural variations that a user might respond with and repeat steps #2 through #4.


For more information on this, see the [Quick Start](https://wit.ai/docs/quickstart) guide.




```java

```

### Capture and stream the user's voice response to Wit for processing

With a configured HTTP client, let's add the Android `AudioRecord` to record the user's voice response and have it streamed to the Wit Speech API for processing.

```java

```

### Wireup `speakButton` to start recording and streaming the voice data

With a configured HTTP client, let's add the Android `AudioRecord` to capture the voice response and have it streamed to the Wit Speech API for processing.

```java

```

### Respond to the user based on the Wit results from Speech API

When the `StreamRecordingRunnable` is finished recording and streaming the voice data, Wit will return the resolved intents and entities in the response. We will need to extract that information from the JSON and respond to the user appropriately.

```java

```

## Review and continue improving your Wit app

As you are testing the app, you might notice that certain utterances are not resolving to the proper intents. To address this, go to [Wit.ai](https://wit.ai/) and on the **Understanding** page you should see utterances that have been sent to the API endpoint. You can review each utterance by expanding one and making sure that the entity is properly identified and resolving to the correct intent. If there are utterances not relevant to your use case (invalid utterances), you can mark them as **Out of Scope**.


## Next Steps

For demonstration purposes, we’ve created a very simple greeting app, but you can create a much more engaging and interactive voice-enabled app. Try sketching out a larger conversation flow with various scenarios and see our [documentation](https://wit.ai/docs) to learn more about other Wit features e.g. other built-in entities, custom entities, and traits (I recommend the [sentiment analysis trait](https://wit.ai/docs/built-in-entities#wit_sentiment)).

You can follow us on  [Twitter @searchome](https://twitter.com/searchhome).
We look forward to what you will develop! To stay connected, join the [Wit Hackers Facebook Group](https://www.facebook.com/groups/withackers) 


## Related Content

* [Reactjs](https://reactjs.org/)
* [Wit.ai](https://wit.ai/)


## Contributing
See the [CONTRIBUTING](CONTRIBUTING.md) file for how to help out.

## License
This tutorial and code is licensed, as found in the [LICENSE](LICENSE) file.
