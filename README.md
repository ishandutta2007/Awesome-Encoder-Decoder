# Awesome-Encoder-Decoder
## Encoder-Decoder Architectures in AI

The **Encoder-Decoder architecture** is a foundational blueprint in AI designed to map variable-length inputs to variable-length outputs. It processes input data into a dense bottleneck representation (the Encoder) and then unpacks that representation into a new format (the Decoder).

---

## Architectural Overview

| Model Category | Key Examples | Primary Modality & Input/Output | Core Mechanism |
| :--- | :--- | :--- | :--- |
| **Sequence-to-Sequence (NLP)** | **T5**, **BART** | Text → Text (Translation, Summarization) | **Transformers**: Full self-attention in encoder; causal masked self-attention + cross-attention in decoder. |
| **Computer Vision / Segmentation** | **U-Net**, **SegNet** | Image → Image (Pixel-level Segmentation Mask) | **CNNs with Skip Connections**: Encoder downsamples to extract features; decoder upsamples to restore spatial resolution. |
| **Multimodal / Vision-Language** | **BLIP-2**, **Flamingo**, **Whisper** | Image/Video/Audio → Text (Captioning, VQA, Audio Transcription) | **Cross-Attention Bottlenecks**: Modality-specific encoder extracts features; a Transformer decoder generates text conditioned on those features. |
| **Generative Modeling** | **VAEs** (Variational Autoencoders) | Data → Continuous Latent Vector → Reconstructed Data | **Probabilistic Latents**: Encoder maps inputs to a probability distribution; decoder samples from it to generate new data variants. |

---

## Key Architectures & Implementations

### 1. Sequence-to-Sequence NLP (The Transformer Pioneers)

#### T5 (Text-to-Text Transfer Transformer) by Google
* **Mechanism:** T5 treats every NLP task as a text-to-text problem. The encoder processes the input text prompt (e.g., `"translate English to German: The cat sat on the mat"`), and the decoder autoregressively generates the text target token-by-token.
* **Impact:** It unified disparate tasks (classification, regression, translation) into a single encoder-decoder framework.

#### BART by Meta
* **Mechanism:** BART uses a bidirectional encoder (like BERT) to analyze corrupted or masked text, and a left-to-right autoregressive decoder (like GPT) to reconstruct the original text.
* **Impact:** It excels at text generation tasks where the model needs a deep, holistic understanding of the source text, such as abstractive summarization.

### 2. Computer Vision (The Spatial Mappers)

#### U-Net
* **Mechanism:** The encoder uses a series of convolutional layers to aggressively downsample the image, capturing high-level semantic features. The decoder mirrors this process by upsampling the features back to the original image dimensions.
* **The "Skip Connections" Innovation:** U-Net passes precise spatial information directly from encoder layers to corresponding decoder layers. This prevents fine details (like boundaries) from being lost in the bottleneck.
* **Impact:** It revolutionized medical image segmentation and forms the backbone of modern Diffusion models (like DDPM and Stable Diffusion) to predict and remove image noise.

### 3. Multimodal & Audio (The Cross-Modality Translators)

#### OpenAI Whisper
* **Mechanism:** The encoder takes an audio spectrogram and extracts rich acoustic features using standard convolutional and transformer layers. The decoder acts as a language model, processing these features via cross-attention to output text transcripts.
* **Impact:** It is the industry benchmark for robust, multilingual speech-to-text and translation.

#### BLIP-2 / Vision-Language Models
* **Mechanism:** A frozen image encoder extracts visual tokens. A specialized bottleneck layer (the Q-Former) bridges the gap by mapping those visual features into a text-aligned latent space. A frozen Large Language Model (LLM) decoder then reads these features to output text.
* **Impact:** It allows AI to reason about images, enabling production-grade visual question answering (VQA) and image captioning.

### 4. Generative AI (The Latent Space Explorers)

#### Variational Autoencoders (VAEs)
* **Mechanism:** Unlike standard autoencoders that compress data into a single point, a VAE encoder compresses an input image into a continuous probability distribution (mean and variance). The decoder then samples a point from this distribution to reconstruct or generate new, highly realistic variations of the data.
* **Impact:** Essential for anomaly detection and acts as the critical "Latent VAE" component in Latent Diffusion Models (e.g., Stable Diffusion) to compress images before processing.
