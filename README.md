# ML Annotation & Classification Toolkit
This repository serves as a technical case study demonstrating human-in-the-loop AI data workflows, annotation system design, machine learning classification pipelines, and explainable AI evaluation.

As project lead, I designed the annotation workflows, defined data quality objectives, architected classification pipelines, and developed tooling to support structured data generation and AI model improvement across image, text, audio, and video modalities.

The toolkit provides annotation and classification capabilities across multimodal datasets, supporting both data preparation workflows and model evaluation processes.

## Annotation + Classification Workflows
- **Image Annotation and Classification Tool**: Designed an image data workflow integrating annotation, PyTorch-based classification, and GUI-driven data labeling.
- **Sarcasm Annotation and Classification Tool**: Developed a text annotation workflow with scikit-learn classification capabilities for labeled language datasets.
- **Emotion and Intent Annotation and Classification Tool**: Built a multimodal annotation and classification workflow using Hugging Face Transformers, supporting text, audio, and video analysis with AI-assisted suggestions and SHAP explainability.

## Annotation-Only Tools
- **Hypothesis Annotation Tool**: Supports text hypothesis labeling with optional image context using a Tkinter-based GUI.
- **Bounding Box Annotation Tool**: Supports image object labeling with bounding boxes and text labels using a Tkinter-based GUI.

## Technical Leadership
As project lead, I was responsible for:
- Designing human-in-the-loop annotation workflows for multimodal AI datasets.
- Establishing data quality objectives and annotation strategies.
- Integrating machine learning classifiers with annotation pipelines.
- Implementing explainability methods to improve model transparency.
- Evaluating tradeoffs between automated classification and human review workflows.
- Designing tooling to support AI training data generation and model improvement.

## Structure
### Annotation + Classification Workflows
- `image_annotator/`: Annotates and classifies images
- `sarcasm_annotator/`: Annotates and classifies text for sarcasm
- `emotion_intent_annotator/`: Annotates and classifies emotions and intents in text, audio, and video

### Annotation-Only 
- `bounding_box_annotator/`: Annotates objects in images with bounding boxes and text labels
- `hypothesis_annotator/`: Annotates text hypotheses with or without corresponding images

## Installation
Each tool has its own requirements. See individual subfolder READMEs for setup instructions.
