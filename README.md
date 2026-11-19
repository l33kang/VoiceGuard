# VoiceGuard

**AI Generated Voice Detection Prototype**

VoiceGuard is an audio classification prototype developed to distinguish between **AI generated voice** and **human voice** using an Edge Impulse trained machine learning model and microphone audio.

> **Project status:** Archived prototype / model evidence. The original embedded hardware is no longer available, but the exported inference model and configuration are preserved in this repository.

## Model performance

The preserved Edge Impulse training results report the following validation-set performance:

| Metric | Result |
|---|---:|
| Validation accuracy | **91.3%** |
| Loss | **0.62** |
| AI voice correctly classified | **90.9%** |
| Human voice correctly classified | **91.7%** |
| AI voice F1 score | **0.91** |
| Human voice F1 score | **0.92** |
| ROC AUC | **0.91** |
| Weighted average precision | **0.91** |
| Weighted average recall | **0.91** |
| Weighted average F1 | **0.91** |

The screenshot supporting these results is preserved at [`docs/training-results.png`](docs/training-results.png).

## Model configuration

The exported inference library preserves the configuration used by the trained model:

- **Classes:** `ai_voice`, `human`
- **Sensor:** Microphone
- **Sampling frequency:** 16,000 Hz
- **Raw sample count:** 16,000 samples
- **Audio window:** 1 second
- **DSP:** Mel Filterbank Energy (MFE)
- **MFE filters:** 40
- **Frame length:** 20 ms
- **Frame stride:** 10 ms
- **FFT length:** 256
- **Neural-network input size:** 3,960
- **Model type:** TensorFlow Lite
- **Quantization:** INT8
- **Model arena requirement:** approximately 209 KB
- **Slices per model window:** 4

These values are taken from the exported Edge Impulse model configuration rather than reconstructed from the screenshot.

## Repository contents

```text
VoiceGuard/
├── README.md
├── docs/
│   └── training-results.png
└── model/
    └── edge-impulse-export/
        ├── src/
        │   ├── model-parameters/
        │   ├── tflite-model/
        │   ├── edge-impulse-sdk/
        │   └── ...
        └── library.properties
```

### `model/edge-impulse-export/`

This is the **actual exported Edge Impulse inference package** from the project, including the generated model representation, model parameters, DSP configuration, and inference SDK.

The trained model is preserved in:

```text
model/edge-impulse-export/src/tflite-model/
```

The model metadata and preprocessing configuration are preserved in:

```text
model/edge-impulse-export/src/model-parameters/
```

## Original deployment

The exported project identifies the Edge Impulse project as:

- Project ID: `985496`
- Project name: `5dollapony-project-1`
- Deployment version: `2`
- Inference engine: TensorFlow Lite
- Quantization: enabled
- Compiled model: enabled

## What was built

The original project used embedded audio inference to classify one-second microphone audio into two classes:

```text
Microphone audio
      ↓
16 kHz audio window
      ↓
MFE feature extraction
      ↓
Quantized INT8 neural network
      ↓
┌───────────────┐
│   ai_voice    │
│     human     │
└───────────────┘
```

The repository is intended to preserve the original AI component and its evidence so the project can be inspected and rebuilt even though the original Arduino hardware is no longer available.

## Limitations

This repository preserves the **AI voice-classification component**. It should not be interpreted as evidence that the original prototype implemented a production telephone-call interception system, telecom integration, or a complete real-time consumer application.

The next development step would be to connect the preserved model to a desktop microphone or a web/backend application and evaluate it on new audio samples.

## License and third party components

The generated Edge Impulse SDK contains its own license files and third-party licenses. **Do not remove or replace those license files.**

The relevant license information is preserved inside:

```text
model/edge-impulse-export/src/edge-impulse-sdk/LICENSE
model/edge-impulse-export/src/edge-impulse-sdk/LICENSE.3-clause-bsd-clear
```

Third-party components included in the generated SDK have their own licenses as documented by the original export, including Apache 2.0, BSD-3-Clause, and public-domain components where applicable.

This repository therefore preserves the original generated package and its license notices rather than claiming a new license over those third-party files.

## Evidence

The repository contains two kinds of evidence:

1. **Model artifact:** the exported Edge Impulse inference package containing the compiled model and configuration.
2. **Training evidence:** the original validation-results screenshot showing the reported model performance.

---

Built as a student AI/cybersecurity prototype and preserved for future reconstruction and development.
