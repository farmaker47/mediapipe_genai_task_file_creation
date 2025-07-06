# MediaPipe GenAI `.task` File Creation Notebooks

## On-Device Model Preparation Summary

These notebooks outline the workflow for converting a pre-trained language model from the Hugging Face Hub into a deployable `.task` file for on-device inference with MediaPipe.

The process consists of four main stages:

---

### 1. Environment Setup

- **Clone Tools Repository**: The necessary conversion scripts are cloned from the [ai-edge-torch](https://github.com/google/ai-edge-torch) GitHub repository.
- **Install Dependencies**: Key libraries are installed, including:
  - `tensorflow`
  - `ai-edge-torch` tools
  - `huggingface_hub`
  - `mediapipe`

---

### 2. Download the Language Model

- **Authenticate & Download**: Using a Hugging Face token, the script downloads the target model files to a local directory.

---

### 3. Convert to TFLite Format

- **Model Conversion**: The core conversion script is run to transform the downloaded model checkpoint into a TensorFlow Lite (`.tflite`) file. This step includes quantization (e.g., to `dynamic_int8`) to optimize the model for size and performance on mobile devices.
- **Tokenizer Preparation**: The model's tokenizer is converted into the SentencePiece format required for the final bundle.

---

### 4. Create the MediaPipe Task Bundle

- **Bundling**: The generated `.tflite` model and the `tokenizer.model` are packaged together into a single `.task` file using the MediaPipe bundler.
- This process involves defining crucial metadata, such as:
  - Start/stop tokens
  - Prompt structure  
  to ensure correct behavior during inference.

---

## Final Output

The result is a self-contained `.task` file, ready to be integrated into an application for on-device generative AI tasks such as:

- https://github.com/google-ai-edge/gallery
- https://github.com/farmaker47/Jetson_App/tree/whisper_gemma3n_tts

---

## Disclaimer: Colab units were provided for this project
