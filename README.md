AI-Driven Voice-Based Multi-Factor Authentication

A secure, AI-powered authentication system designed for corporate environments (e.g., attendance systems). This project combines voice biometrics ("something you are") with PIN verification ("something you know") to eliminate identity fraud, buddy punching, and deepfake-based attacks.

🚀 Overview

Traditional security measures like PINs or simple biometrics are vulnerable to theft, replay attacks, and AI-generated deepfakes. This system implements a high-integrity AI Security Pipeline to ensure that the user is both physically present and authentically verified.

Key Use Case

Corporate Attendance Systems: Replaces traditional badge-in or fingerprint systems to prevent "buddy punching" and ensure contactless, secure clock-ins.

🛠️ Tech Stack

Frontend: React

Backend: FastAPI (Python)

Database: MySQL (with AES-256-GCM encryption)

AI/ML Frameworks: SpeechBrain, Transformers (Hugging Face)

Audio Processing: Pydub, Wav2Vec2

Security: BCrypt (PIN hashing), JWT (Session management)

🔐 The AI Security Pipeline

Authentication is processed through a 4-gate verification flow:

Gate 0: Pre-Processing: Audio normalization (-3dB) and conversion to 16kHz WAV.

Gate 1: Noise Cancellation: Utilizes SpeechBrain Sepformer to isolate voice from background office noise.

Gate 2: Anti-Spoofing & Liveness:

Deepfake Detection: Uses a Melody Machine transformer model to detect synthetic voices.

Acoustic Artifact Analysis: Detects replay attacks by identifying low-frequency rumbles or high-frequency loss typical of speakers.

Gate 3: Biometric Verification: Uses ECAPA-TDNN to extract voice embeddings and compare them against stored voiceprints using Cosine Similarity.

✨ Security Features

Multi-Factor Orchestration: Combines verbal PIN entry with voiceprint matching.

Zero-Trust Architecture: Raw biometric data is never accessible to administrators; voiceprints are stored as encrypted embeddings.

Brute Force Protection: Implements an Exponential Backoff Algorithm (10-min, 30-min, and 24-hour lockout tiers).

High-Integrity Enrollment: Strict 3-sample enrollment process; if any sample fails the anti-spoofing check, registration is rejected.

Database Encryption: Military-grade AES-256-GCM for data at rest and BCrypt with unique salting for PINs.

📊 System Architecture

The system follows a modern web architecture:

React Frontend captures audio via the browser microphone.

FastAPI Backend handles the logic and orchestrates the AI models.

MySQL Database stores encrypted voiceprints and audit logs (LoginAttempt tables) for accountability.


Developed by myself and https://github.com/Shayan-Maqsood as an Information Security End-Semester Project.
