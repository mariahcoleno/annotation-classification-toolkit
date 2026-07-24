## Emotion and Intent Annotation and Classification Tool 
This project serves as a technical case study demonstrating multimodal AI data workflows, human-in-the-loop annotation systems, AI-assisted labeling, and explainable machine learning evaluation.

As project lead, I designed the annotation workflow, defined data quality objectives, architected the multimodal processing pipeline, and developed tooling to support AI data generation and model improvement across text, audio, and video modalities.

The tool enables human reviewers to annotate emotional and intent-based signals while leveraging AI-generated suggestions, speech transcription, and SHAP-based explainability to improve labeling consistency and transparency.

### Multimodal AI Data Workflow
- **Multi-format Support:** Processes text, audio, and video inputs for multimodal annotation workflows.
- **Speech Processing Pipeline:** Converts audio/video content into segmented text using OpenAI Whisper transcription.
- **AI-Assisted Label Suggestions:** Generates context-aware emotion and intent predictions to support human annotation.
- **Explainability:** Uses SHAP visualizations to show feature contributions behind AI-generated suggestions.
- **Human-in-the-Loop Annotation:** Enables reviewers to validate, edit, and refine AI-generated labels before saving.
- **Data Management:** Stores annotations in SQLite and exports structured datasets for downstream analysis.
- **Smart Segmentation:** Automatically separates text into meaningful annotation segments.

### Screenshots
#### GUI Screenshots
![GUI segment 1](screenshots/EmotionandIntentAnnotator_GUI_segment1.png)
![GUI segment 2](screenshots/EmotionandIntentAnnotator_GUI_segment2.png)

#### SHAP Visualizations
![SHAP Text Force Plot Segment 1](screenshots/shap_force_text_segment1.png)
![SHAP Text Force Plot Segment 2](screenshots/shap_force_text_segment2.png)
![SHAP Summary Plot Segment 1](screenshots/shap_summary_segment1.png)
![SHAP Summary Plot Segment 2](screenshots/shap_summary_segment2.png)
![SHAP Waterfall Plot Segment 1](screenshots/shap_waterfall_segment1.png)
![SHAP Waterfall Plot Segment 2](screenshots/shap_waterfall_segment2.png)

### Technical Leadership
As project lead, I was responsible for:
- Designing a human-in-the-loop annotation framework for multimodal AI data.
- Defining annotation objectives and data quality considerations.
- Integrating speech recognition, NLP models, and explainability methods into a unified workflow.
- Evaluating AI-generated suggestions against human review processes.
- Designing workflows that balance automation efficiency with human validation.
- Establishing explainability mechanisms to improve trust and transparency in AI-assisted labeling.

### Files
- `requirements.txt`: Lists all Python dependencies required to run the tool.
- `src/setup_db.py`: Initializes SQLite database.
- `src/process_text.py`: Text segmentation and AI suggestions.
- `src/annotate_emotions.py`: The main script that runs a Tkinter-based GUI to display texts from `emotions_intents.sqlite` and save annotations (emotions/intents) to the database.
- `src/audio.py`: Handles audio transcriptions using openai-whisper and segments transcriptions for annotation. 
- `data/sample_text.txt`: File that contains sample texts.
- `data/sample_audio.m4a`: File that contains sample audio.
- `data/sample_audio.wav`: File that contains sample audio.
- `data/sample_video.mp4`: File that contains sample video.
- `emotions_intents.sqlite`: Generated SQLite database storing labeled texts (ignored by Git).
- `annotations_export.csv`: Exported CSV of labeled texts (ignored by Git).

### Requirements
- Python 3.8+ (tested with Python 3.13.3)
- pandas - for data manipulation and CSV handling
- torch - for PyTorch machine learning models
- transformers - for Hugging Face NLP models and pipelines (for emotion suggestions)
- textblob - for natural language processing
- shap - for model explainability
- matplotlib - for plotting and visualizations
- numpy - for numerical operations
- openai-whisper - for speech-to-text transcription
- nltk - for natural language toolkit (sentence segmentation)
- librosa - for advanced audio analysis and feature extraction from audio files
- opencv-python-headless - for video processing and frame extraction (headless version without GUI dependencies)
- pydub - for audio file format conversion and basic audio manipulation

### Setup and Usage
#### Option 1: From GitHub (First Time Setup)
- **Note**:
  - Start in your preferred directory (e.g., cd ~/Desktop/ or cd ~/Downloads/ or cd ~/Documents/) to control where the repository clones. 
  - If you skip this step, it clones to your current directory.
1. Clone the repository: `git clone https://github.com/mariahcoleno/annotation-classification-toolkit.git`
2. Navigate to the emotion_intent_annotator directory: `cd emotion_intent_annotator/` (from the root of your cloned repository)
3. Create virtual environment: `python3 -m venv venv`
4. Activate: `source venv/bin/activate` # On Windows: venv\Scripts\activate
5. Install dependencies: `pip install -r requirements.txt`
6. Install ffmpeg (required for audio/video processing):
   - macOS: `brew install ffmpeg`
   - Ubuntu/Debian: `sudo apt-get install ffmpeg` 
   - Windows: Download from https://ffmpeg.org/download.html and add to PATH
7. Set environment variable (optional, suppresses warnings): `export TOKENIZERS_PARALLELISM=false`  
8. Proceed to the "Run the Tool" section below.

#### Option 2: Local Setup (Existing Repository)
1. Navigate to your local repository `cd ~/Documents/annotation-classification-toolkit/` # Adjust path as needed
2. Navigate to emotion_intent_annoator directory: `cd emotion_intent_annotator/`
3. Setup and activate a virtual environmnt:
   - If existing: `source venv/bin/activate` # Adjust path if venv is elsewhere
   - If new:
     - `python3 -m venv venv`
     - `source venv/bin/activate` # On Windows: venv\Scripts\activate
4. Install dependencies (if not already): `pip install -r requirements.txt` 
5. Install ffmpeg (required for audio/video processing):
   - macOS: `brew install ffmpeg`
   - Ubuntu/Debian: `sudo apt-get install ffmpeg`
   - Windows: Download from https://ffmpeg.org/download.html and add to PATH          
6. Set environment variable (optional, suppresses warnings): `export TOKENIZERS_PARALLELISM=false`
7. Proceed to the "Run the Tool" section below.

### Run the Tool (Both Options):
1. Initialize the database: `python3 src/setup_db.py`
2. Start the application: `python3 -m src.annotate_emotions` 
3. Using the GUI:
   - **Upload**: Click "Upload File" and select a text file (.txt) or media file (`.wav`, `.mp3`, `.m4a`, `.mp4`, `.mov`)
   - **Review segments**: View auto-segmented text/transcriptions; edit if needed using "Edit Segment"
   - **Get AI suggestions**: Click "Suggest Labels" for emotion/intent predictions
   - **View explanations**: Click "Visualize Suggestions" to see SHAP plots
   - **Annotate**: Select emotions and intents, then click "Save Annotation"
   - **Export**: Click "Export CSV" to save annotations as annotations_export.csv
   - **Undo**: Use "Undo Last Annotation" to revert changes

Note: NLTK punkt tokenizer downloads automatically on first run.
    
### Advanced Usage
Reset database (clears all data):
 - `mv emotions_intents.sqlite emotions_intents_backup_$(date +%F).sqlite`
 - `python3 src/setup_db.py`
    
### Sample Data
The repository includes an example text file for testing text segmentation and annotation:
- **`data/sample_text.txt`**: 
  ```text
  I’m thrilled about this project! Just kidding, it’s overwhelming.
  ```
  This file is used to demonstrate the GUI’s ability to segment text into sentences and annotate emotions and intents. You can also upload your own .txt files via the GUI.

### Project Structure
- annotation-classification-toolkit/
  - emotion_intent_annotator/
    - data/
      - sample_audio.m4a # Example audio file
      - sample_audio.wav # Example audio file
      - sample_text.txt # Example text file
      - sample_video.mp4 # Example video file 
    - screenshots/ (multiple image files)
    - src/
      - __init__.py
      - annotate_emotions.py # GUI for annotation
      - audio.py # Audio transcription and segmentation
      - process_text.py # Text segmentation and AI suggestions 
      - setup_db.py # Initializes SQLite database
    - .gitignore
    - README.md
    - requirements.txt
  - .gitignore
  - README.md

### Development Notes
- AI-assisted development tools (Claude and Grok) were used to accelerate prototyping, debugging, documentation, and implementation.
- As project lead, I directed system architecture, annotation workflow design, AI evaluation strategy, and technical implementation decisions.
- SHAP-based explainability workflows required iterative experimentation and refinement to improve interpretability of AI-generated recommendations.
