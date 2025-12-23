# ₿Proof (MVP)

## Tamper-Evident Digital Certificate Issuance & Verification

₿Proof is a Minimum Viable Product (MVP) for issuing and verifying digital certificates for Bitcoin Dada & Dada Devs.

⚠️ IMPORTANT  
This system provides tamper-evidence, not immutability.  
Certificates are currently stored using browser localStorage, which is suitable for prototyping but NOT production use.

Full trust-minimized verification requires anchoring certificate hashes to public, external systems (e.g. Bitcoin via OpenTimestamps or decentralized networks like Nostr). These are planned upgrades.

---

## 🎯 Overview

₿Proof enables certificate issuance and verification using:

- Unique Certificate IDs  
  Format: DD-YYYY-XXXXXX (e.g. DD-2025-8F32C1)
- SHA-256 hashing for integrity checking
- QR code verification for quick access
- PDF export for downloadable certificates
- Modern minimalist UI (black, gold, white)

---

## ✨ Features

### MVP Features
- Generate unique certificate IDs
- Compute SHA-256 hashes from certificate fields
- Store certificate data + hash together (MVP storage)
- QR codes linking to verification pages
- PDF certificate download

### Admin & UX
- Dashboard listing issued certificates
- Public certificate verification page
- Clean, modern interface

---

## 🚀 Getting Started

### Prerequisites
- Node.js 16+
- npm or yarn

### Installation
npm install

### Run Development Server
npm run dev

Open your browser at:  
http://localhost:5173

### Production Build
npm run build

The production build will be located in the dist/ directory.

---

## 📖 How It Works (MVP)

### 1. Issuing a Certificate

1. Navigate to "Issue Certificate"
2. Fill in:
   - Student Name
   - Cohort
   - Course Type
   - Issue Date
3. Click "Generate Certificate"

The system will:
- Generate a unique Certificate ID
- Compute a SHA-256 hash from certificate data
- Store the data and hash together
- Generate a QR code for verification
- Display a certificate preview

You may then download the certificate as a PDF.

---

### 2. Verifying a Certificate

Method 1: Certificate ID
- Navigate to "Verify"
- Enter the Certificate ID
- View verification results

Method 2: QR Code
- Scan the QR code on the certificate
- Automatically open the verification page

---

## ✅ Verification Logic

During verification, the system:

1. Recomputes the SHA-256 hash from displayed certificate fields
2. Compares it to the stored hash
3. Displays the result:

- Valid – Hash matches stored record
- Modified – Certificate data differs from stored record

NOTE: Because certificates are stored locally in this MVP, verification is strongest when performed against the issuer’s dataset.

---

## 🔒 Security Notes (Honest)

### What This MVP Does
- Detects changes to certificate fields relative to a stored record
- Makes casual forgery more difficult
- Demonstrates cryptographic integrity checks

### What This MVP Does NOT Do (Yet)
- Provide immutability or global consensus
- Prevent malicious re-issuance of altered certificates
- Enable independent verification without trusting issuer storage
- Anchor data to Bitcoin or any blockchain

---

## 🛠️ Technology Stack

- React 18
- React Router
- Vite
- crypto-js (SHA-256)
- qrcode.react
- jsPDF
- html2canvas

---

## 📁 Project Structure

dadadigital/
├── src/
│   ├── components/
│   ├── pages/
│   ├── utils/
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── package.json
├── vite.config.js
└── README.md

---

## 🔮 Future Enhancements (Production Roadmap)

- Database storage (PostgreSQL / MongoDB)
- Admin authentication and audit logs
- Certificate revocation system
- Canonical certificate schemas
- Bitcoin timestamp anchoring (OpenTimestamps)
- Decentralized publication (Nostr)
- Merkle batching for scalable anchoring
- API endpoints for programmatic access
- Bulk certificate issuance
- Email delivery

---

## 📄 License

Built for Bitcoin Dada, Dada Devs, and the wider community.

This project is an MVP intended for learning and experimentation.  
Production deployment requires proper storage, authentication, auditability, and external anchoring.
