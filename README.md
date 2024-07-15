# AI Meeting Assistant POC

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1TG0CEwTKTsfmKg5DpzmNlCgvzNCT8-0z?usp=sharing)

This project implements transcription and speaker identification for audio recordings. It's designed as a Proof of Concept (POC) to make a ai meeting assistant tool which will integrate with existing meeting flow of any workspace and  can be used to  transcribe meetings with speakers, summarize meeting,  action items tracking, and meeting analytics with support for indian languages. . The goal is to address common meeting challenges like information loss , ineffective follow-ups and project transparency.

## Current Features

- Audio transcription using WhisperX
- Speaker diarization
- Speaker embedding generation and matching with SpeechBrain
- Flask API for speaker enrollment and audio transcription

## How to Use

1. Run the Colab notebook to start the server.
2. Copy the generated ngrok URL.
3. Access the demo frontend at https://note-taker-poc.vercel.app/
4. Alternatively, use the provided Postman collection for API testing.

## Setup

To run this project, you'll need to set up the following environment variables/ secrets in the google colab link:

- `HF_TOKEN`: Your Hugging Face token
- `NGROK_AUTHTOKEN`: Your Ngrok authentication token

## API Endpoints

### Speaker Enrollment
- **POST /enroll**
  - Enrolls speakers with voice samples and creates embeddings
  - Request body:
    - num_speakers: int (number of speakers to enroll)
    - names: list of strings (names of speakers)
    - audio_[i]: audio file for each speaker (i = 0 to num_speakers - 1)
  - Response: JSON with message and list of enrolled speakers

### Audio Transcription
- **POST /transcribe**
  - Transcribes and diarizes an audio file
  - Request body:
    - audio: audio file to transcribe
  - Response: JSON with transcription text



## Additional Information

- The server uses ngrok for public access
- Enrolled speaker data is stored in memory (known_speakers dictionary)
- Supports multiple audio formats (converted to WAV internally)
- Saves transcription results to a text file
- CORS is enabled for cross-origin requests

## Future Improvements

- Browser Extension for easy meeting integration
- AI-generated meeting summaries
- Automatic Action items tracking and delgation
- Search functionality across meeting transcripts and summaries
- Web Application for dashboards and recordings
- Calendar integration (e.g., Google Calendar)

