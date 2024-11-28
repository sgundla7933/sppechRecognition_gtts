# Audio-based ChatGPT Bot

## Overview
This project is an audio-based bot that listens for a wake word, transcribes the audio input, generates responses using ChatGPT, and provides a verbal reply via text-to-speech. It integrates multiple libraries for seamless audio processing, speech-to-text conversion, and interaction with OpenAI's GPT models.

---

## Features
- **Wake Word Detection**: Activates only when a specified wake word (e.g., "hey computer") is detected.
- **Speech-to-Text**: Uses OpenAI's Whisper model for transcription.
- **Natural Language Understanding**: Sends user queries to OpenAI's ChatGPT model for a conversational response.
- **Text-to-Speech**: Converts the generated response into speech using `gTTS`.
- **Multithreading**: Processes recording, transcription, and reply generation in parallel for smooth operation.

---

## Prerequisites
- Python 3.8 or higher
- Required libraries:
  - `os`, `re`, `queue`, `threading`
  - `torch`, `numpy`
  - `speech_recognition`
  - `gTTS`, `pydub`
  - `openai`, `dotenv`
  - `whisper`
- Hardware:
  - Microphone for audio input
  - Speaker for audio output

---

## Installation

1. Clone the repository:
   git clone https://github.com/your-repo/audio-chatgpt-bot.git
   cd audio-chatgpt-bot

2. Install dependencies:
   pip install -r requirements.txt

3. Set up your `.env` file with your OpenAI API key:
   OPENAI_API_KEY=your_openai_api_key_here

4. Verify that `ffmpeg` is installed for `pydub` to work.

   brew install ffmpeg  # For macOS users
   sudo apt install ffmpeg  # For Ubuntu users

---

## Usage

Run the main script:
python main.py

### Parameters
- **model**: Specify the Whisper model to load (`base`, `small`, `medium`, etc.).
- **wake_word**: The keyword that triggers the bot.
- **verbose**: Enable or disable detailed logs.

Example:
python main.py --model base --wake_word "hey computer" --verbose


## Architecture

1. **Audio Recording**:
   - Captures audio input from the microphone in real-time.
2. **Transcription**:
   - Converts the audio into text using Whisper.
   - Detects the wake word before proceeding.
3. **ChatGPT Interaction**:
   - Sends transcribed text to ChatGPT for a response.
   - Processes the response for further use.
4. **Text-to-Speech**:
   - Converts the response to audio and plays it back.
5. **Multithreading**:
   - Separate threads for recording, transcription, and response generation ensure smooth execution.


## Example

**User:** "Hey computer, what is the weather like today?"

**Bot:** (via speaker) "I'm sorry, I can't provide live weather updates at the moment."


## Troubleshooting

- **Missing `.env` file**:
  Ensure the `.env` file is present and contains the correct OpenAI API key.

- **Audio not playing**:
  Verify `ffmpeg` is installed and properly configured.

- **Wake word not detected**:
  Adjust microphone sensitivity by modifying `energy_threshold` and `pause_threshold` in `record_audio`.

- **Error communicating with OpenAI API**:
  Check your internet connection and API key validity.


Google slide presentation - https://docs.google.com/presentation/d/16scGxEgmluW-mTHP4izSB1XWcRCq9BAzeOkREt8bllI/edit?usp=sharing


