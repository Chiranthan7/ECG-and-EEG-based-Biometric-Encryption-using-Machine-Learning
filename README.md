# ECG + EEG Based Biometric Encryption using Machine Learning

## Overview

This project implements a **multimodal biometric authentication and encryption system** using ECG (Electrocardiogram) and EEG (Electroencephalogram) signals.

It combines machine learning with cryptography to generate **unique biometric-based encryption keys**, enabling secure and spoof-resistant authentication.

---

## Problem Statement

Traditional authentication systems (passwords, OTPs) are vulnerable to:

* Theft
* Replay attacks
* Spoofing

This project aims to build a **biometric-based secure authentication system** that:

* Uses physiological signals (ECG + EEG)
* Generates dynamic encryption keys
* Enables secure, keyless encryption

---

## Key Features

* Multimodal biometric fusion (ECG + EEG)
* Advanced feature extraction:

  * Time-domain
  * Frequency-domain
  * Wavelet-domain
  * Non-linear features
* Machine learning-based identity classification
* Dynamic key generation using SHA-256
* AES-based secure encryption & decryption
* Real-time authentication system

---

## Dataset

* ECG signals (WFDB format)
* EEG signals (CSV format)
* Multi-person dataset (5 individuals)

 EEG data is fused with ECG features to create a combined biometric representation.

---

## System Architecture

```id="arch1"
ECG Signal → Feature Extraction
                         ↓
EEG Signal → Feature Extraction
                         ↓
        Feature Fusion (ECG + EEG)
                         ↓
        Machine Learning Model (Random Forest)
                         ↓
        Identity Prediction
                         ↓
   Biometric Template → SHA-256 → AES Key
                         ↓
     Secure Encryption / Decryption
```

---

## Feature Engineering

### ECG Features

* Time-domain (mean, variance, RMS, etc.)
* Frequency-domain (Welch PSD, spectral entropy)
* Wavelet features (multi-level decomposition)
* Non-linear features (entropy, fractal dimension)

###  EEG Features

* Preprocessed EEG feature vectors
* Matched and aligned with ECG beats

---

## Machine Learning Model

* Model: **Random Forest Classifier**
* Input: Fused ECG + EEG features
* Output: Person identification

### Performance

* Accuracy: **~100% on test set**
* Robust classification using multimodal signals

---

## Cryptography Module

### Key Generation

* Biometric template → normalized → hashed using **SHA-256**
* Generates **256-bit unique encryption key**

### Encryption

* Algorithm: **AES (CBC mode)**
* Input: Secret message
* Output: Encrypted ciphertext

### Decryption

* Only successful after correct biometric authentication

---

## Authentication Workflow

1. User provides ECG + EEG data
2. Features are extracted and fused
3. Model predicts identity
4. If verified:

   * Biometric key is generated
   * Encrypted data is decrypted

---

## Demo (Gradio UI)

* Input:

  * Claimed user ID
  * ZIP file containing ECG + EEG data
* Output:

  * Authentication result
  * Decrypted message (if valid)

---

## Applications

* Secure biometric authentication systems
* Military-grade identity verification
* Healthcare data security
* Banking & financial security
* Anti-spoofing systems

---

## Future Improvements

* Deep learning-based feature extraction
* Larger dataset (more subjects)
* Real-time wearable integration
* Cloud deployment
* Multi-factor biometric fusion

---

## Limitations

* Small dataset (5 users)
* Requires clean signal data
* Not yet production deployed

---

##  Contributing

Contributions are welcome!
