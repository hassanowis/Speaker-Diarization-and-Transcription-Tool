
# README: Speaker Diarization and Transcription Pipeline

This README provides a detailed explanation of the script designed to process an MP4 file, perform speaker diarization, transcribe audio, and merge the results into a structured format.

---

## Prerequisites

To run this script, you need the following libraries installed:

```bash
!pip install moviepy pyannote.audio soundfile pandas numpy speechrecognition pydub
```

### Required Libraries
1. **moviepy**: For audio extraction from video files.
2. **pyannote.audio**: For speaker diarization.
3. **soundfile**: To handle audio file formats.
4. **pandas**: To organize and structure output data.
5. **numpy**: For numerical operations.
6. **speechrecognition**: To support additional speech processing needs.
7. **pydub**: For audio file manipulation.

---

## How It Works

The script processes an MP4 file and produces a structured dataframe containing speaker labels, timestamps, and transcriptions. Here are the steps:

### Step 1: Convert MP4 to WAV
The function `convert_mp4_to_wav` extracts audio from the input MP4 file and saves it as a WAV file using `moviepy`.


---

### Step 2: Perform Speaker Diarization
The function `perform_diarization` utilizes the `pyannote.audio` library to identify speaker segments. You need a Hugging Face token to authenticate the diarization model.


---

### Step 3: Transcribe Audio using OpenAI Whisper
The function `transcribe_audio_with_whisper` uses the OpenAI Whisper model to transcribe the audio. You can specify the language for transcription (e.g., Arabic).


---

### Step 4: Merge Diarization and Transcription
The function `merge_diarization_and_transcription` aligns the speaker segments with the transcription output. Overlapping text is concatenated for each speaker segment.


---

## Example Usage

### Input
- **MP4 File**: `/content/drive/MyDrive/final_ara.mp4`
- **Output WAV File**: `audio.wav`
- **Hugging Face Token**: A valid token from Hugging Face.


---

## Output
The final output is a dataframe with the following columns:
- **speaker_id**: Label for each speaker (e.g., Speaker 1, Speaker 2).
- **start**: Start time of the segment (in seconds).
- **end**: End time of the segment (in seconds).
- **text**: Transcribed text spoken by the speaker.

### Example:
| speaker_id | start  | end    | text              |
|------------|--------|--------|-------------------|
| Speaker 1  | 0.00   | 5.00   | "السلام عليكم?"   |
| Speaker 2  | 5.01   | 10.00  | "وعليكم السلام" |

---

## Notes
- Ensure the Hugging Face token is valid and provides access to the `pyannote` models.
- Adjust the Whisper model size (`small`, `medium`, `large`) based on your system's capabilities.

---

## Future Improvements
- Add support for multiple languages.
- Optimize merging logic for overlapping transcription segments.
- Provide a graphical user interface (GUI) for easier interaction.

---

## License
This project is licensed under the MIT License.
