# MMM-Chat

**MagicMirror Module to Chat with ChatGPT**

---

## Overview
This module integrates ChatGPT into your MagicMirror setup, allowing you to interact with an AI assistant directly through your mirror. 

### Key Features:
- Customize the AI's personality.
- Speech-to-text integration using Google STT or Whisper API.

---

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/magicmirror-sdmy/MMM-Chat.git
    cd MMM-Chat
    ```

2. Install dependencies:
    ```bash
    pip3 install -r requirements.txt
    ```

3. Add credentials to the `MMM-Chat` directory (see below for details).

---

## Configuration

### Default Installation Path
This module assumes the default installation path is `/home/pi/MagicMirror`. If you are using a different location, update `node_helper.js` with the correct directory.

### Customizing the AI Personality
You can change the personality of the AI by editing **line 26** in `MMM-Chat.js`. The default personality is set to "Drunk AI."

#### Example:
To make the AI sarcastic, use the following prompt:
```javascript
"Your name is Marvin and you are a paranoid android that reluctantly answers questions with sarcastic responses."
```

Update the `MMM-Chat.js` file with the desired prompt.

---

## Google Speech-to-Text Setup

### Prerequisites
You will need:
1. Google service account credentials.
2. A billing account. Google offers a free quota; stay within this limit to avoid charges.

### Steps
1. Visit the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project or select an existing one.
3. Navigate to **APIs & Services > Credentials**.
4. Click **Create credentials** and select **Service account key**.
5. Choose a service account name and assign the **Editor** role.
6. Go to the service account and click **Add key**.
7. Select **JSON** as the key type and click **Create**.

The JSON key file will be downloaded. Rename it to `credentials.json` and place it in the `MMM-Chat` directory.

### Testing Speech-to-Text
To verify the setup, run the following command:
```bash
python3 transcript.py
```
Speak into the microphone, and the transcription of your words should appear.

---

## Whisper API Integration
A script is provided for use with the Whisper API. However, in testing, Google STT offered better accuracy. If you'd like to use Whisper:
1. Modify **line 21** in `node_helper.js` to use `whisper.py`.
2. Install the OpenAI Python library:
    ```bash
    pip3 install openai
    ```

---

## MagicMirror Configuration
Add the following lines to your `config.js`:
```javascript
{
    module: "MMM-Chat",
    config: {}
},
```

---

## Todo
- Add a configuration option in `config.js` to support different AI personalities through prompts.

---
