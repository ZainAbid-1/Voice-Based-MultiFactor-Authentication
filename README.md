AI-Driven Voice-Based MFA

A secure, AI-powered authentication system built with React and FastAPI. It combines voice biometrics ("something you are") and PIN verification ("something you know") to eliminate identity fraud, buddy punching, and deepfake-based attacks.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
📦 Stack

React (Frontend)

FastAPI (Python Backend)

MySQL (AES-256-GCM encrypted storage)

SpeechBrain (Voice biometrics & Sepformer noise cancellation)

Transformers (Deepfake detection models)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
✨ Quick start
code
Bash
download
content_copy
expand_less
# Install dependencies and start the backend
pip install -r requirements.txt
uvicorn main:app --reload

# Install dependencies and start the frontend
npm install
npm run dev

Enroll your voice with 3 samples to generate a secure biometric voiceprint.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
🔐 Security Features

MFA Orchestration — Combined verbal PIN entry and voiceprint matching.

Anti-Spoofing — Dedicated detection for replay attacks and AI-generated clones.

Brute Force Protection — Exponential backoff algorithm with tiered lockout (10m, 30m, 24h).

Zero-Trust Design — No raw biometric data is stored; only encrypted embeddings.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
🎹 Controls

Enrollment — Record 3 voice samples for identity anchoring.

Verification — State your PIN to initiate biometric comparison.

Audit Logs — Every attempt is timestamped and recorded in the LoginAttempt table.

High-integrity enrollment is enforced; any single failed sample halts the entire registration.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
🤖 How it works

The system processes authentication requests through a 4-gate AI security pipeline:

Gate 0 & 1 — Audio is normalized to -3dB and cleaned via the Sepformer noise cancellation model.

Gate 2 (Liveness) — Frequency domain analysis detects "rumble" or high-frequency loss typical of replay attacks.

Gate 2 (Deepfake) — A Melody Machine transformer model identifies synthetic generative artifacts.

Gate 3 (Biometric) — ECAPA-TDNN extracts embeddings for Cosine Similarity matching against the encrypted database.


--------------------------------------------------------------------------------------------------------------------------------------------------------------------
📁 Project structure
code
Code
download
content_copy
expand_less
src/
  frontend/            # React UI for audio capture and status
  backend/
    api/               # FastAPI endpoints and rate limiting
    ai_pipeline/       # SpeechBrain, ECAPA-TDNN, and Anti-spoofing logic
    security/          # AES-256-GCM encryption and BCrypt hashing
  database/            # MySQL schema for user profiles and audit logs
👤 Authors

Developed by Shayan Maqsood  & Zain Abid  — Information Security End Semester Project
