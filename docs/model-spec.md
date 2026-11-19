# VoiceGuard Model Specification

This document records the configuration found in the preserved Edge Impulse export.

## Classification

- `ai_voice`
- `human`

## Audio input

- Sensor: Microphone
- Sampling frequency: 16,000 Hz
- Raw samples: 16,000
- Raw audio duration: 1 second

## Feature extraction

- DSP block: MFE (Mel Filterbank Energy)
- Frame length: 0.02 seconds (20 ms)
- Frame stride: 0.01 seconds (10 ms)
- Number of filters: 40
- FFT length: 256

## Neural network

- Input size: 3,960
- Inference engine: TensorFlow Lite
- Input datatype: INT8
- Output datatype: INT8
- Quantization: enabled
- Compiled model: enabled
- Largest TensorFlow Lite arena: 209,478 bytes
- Slices per model window: 4

## Deployment

- Edge Impulse project ID: 985496
- Project name: 5dollapony-project-1
- Deployment version: 2
