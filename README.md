₿Proof

# Digital Certificate Signature System

A tamper-proof digital certificate issuance and verification system for Bitcoin Dada & Dada Devs.

## 🎯 Overview

This system provides a secure way to issue and verify digital certificates with:
- **Unique Certificate IDs** - Format: DD-YYYY-XXXXXX (e.g., DD-2025-8F32C1)
- **Digital Signatures** - SHA-256 hash-based signatures for tamper detection
- **QR Code Verification** - Scan QR codes to instantly verify certificate authenticity
- **PDF Export** - Download certificates as PDF files
- **Beautiful UI** - Tech Minimalist design (Black, Gold, White)

## ✨ Features

### MVP Requirements ✅
- ✅ Generate unique certificate ID
- ✅ Create tamper-proof digital signature (SHA-256)
- ✅ Attach signature to certificate
- ✅ QR Code for verification
- ✅ Simple admin issuance flow

### Bonus Features
- ✅ Dashboard to view issued certificates
- ✅ Certificate verification page
- ✅ Beautiful, modern UI
- ✅ PDF download functionality

## 🚀 Getting Started

### Prerequisites
- Node.js 16+ and npm/yarn

### Installation

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Start development server:**
   ```bash
   npm run dev
   ```

3. **Open your browser:**
   Navigate to `http://localhost:5173`

### Build for Production

```bash
npm run build
```

The production build will be in the `dist` folder.

## 📖 How It Works

### 1. Issuing a Certificate

1. Navigate to **"Issue Certificate"** from the sidebar
2. Fill in the form:
   - Student Name
   - Cohort
   - Course Type
   - Issue Date
3. Click **"Generate Certificate"**
4. The system will:
   - Generate a unique Certificate ID (e.g., DD-2025-8F32C1)
   - Create a SHA-256 digital signature from the certificate data
   - Generate a QR code linking to the verification page
   - Display the certificate preview
5. Click **"Download PDF"** to save the certificate

### 2. Verifying a Certificate

**Method 1: Using Certificate ID**
1. Navigate to **"Verify"** from the sidebar
2. Enter the Certificate ID
3. Click **"Verify Certificate"**
4. View the verification results

**Method 2: Using QR Code**
1. Scan the QR code on the certificate
2. You'll be redirected to the verification page
3. View the verification results automatically

### Verification Results

The system checks:
- ✅ **Signature Valid** - Digital signature matches expected hash
- ✅ **Hash Matches** - Certificate data hasn't been altered
- ✅ **Tampered** - Shows if certificate has been modified

## 🔒 Security

### How It Prevents Forgery

1. **Digital Signature (SHA-256 Hash)**
   - Each certificate's data (ID, student name, cohort, course, date) is hashed using SHA-256
   - The hash is stored with the certificate
   - Any modification to the certificate data will produce a different hash

2. **Verification Process**
   - When verifying, the system recalculates the hash from the stored certificate data
   - Compares it with the stored signature
   - If they don't match, the certificate has been tampered with

3. **Certificate Storage**
   - Currently uses browser localStorage (for MVP)
   - In production, certificates should be stored in a secure database
   - Consider using blockchain (OpenTimestamps) or Nostr for additional immutability

### Why This Solution is Secure

- **Cryptographic Hashing**: SHA-256 is a one-way function - you cannot reverse-engineer the original data from the hash
- **Tamper Detection**: Any change to certificate data results in a completely different hash
- **Unique IDs**: Each certificate has a unique identifier that cannot be duplicated
- **QR Code Verification**: Provides instant access to verification without manual entry

## 📁 Project Structure

```
dadadigital/
├── src/
│   ├── components/
│   │   ├── Layout.jsx          # Main layout with sidebar
│   │   ├── Layout.css
│   │   ├── CertificatePreview.jsx  # Certificate display component
│   │   └── CertificatePreview.css
│   ├── pages/
│   │   ├── Dashboard.jsx       # Dashboard with stats
│   │   ├── Dashboard.css
│   │   ├── IssueCertificate.jsx    # Certificate issuance form
│   │   ├── IssueCertificate.css
│   │   ├── PublicVerification.jsx  # Public verification page
│   │   ├── PublicVerification.css
│   │   ├── Settings.jsx        # Settings page
│   │   └── Settings.css
│   ├── utils/
│   │   └── certificateUtils.js # Certificate generation & verification logic
│   ├── App.jsx                 # Main app component with routing
│   ├── main.jsx               # Entry point
│   └── index.css              # Global styles
├── package.json
├── vite.config.js
└── README.md
```

## 🛠️ Technology Stack

- **React 18** - UI framework
- **React Router** - Navigation
- **Vite** - Build tool
- **crypto-js** - SHA-256 hashing
- **qrcode.react** - QR code generation
- **jsPDF** - PDF generation
- **html2canvas** - Canvas rendering for PDF

## 📝 Certificate Format

Each certificate includes:
- **Header**: Bitcoin Dada × Dada Devs seal and branding
- **Title**: "Certificate of Completion"
- **Student Information**: Name, Course, Cohort
- **Issue Date**: Formatted date
- **QR Code**: Links to verification page
- **Certificate ID**: Unique identifier
- **Digital Signature**: SHA-256 hash (truncated for display)

## 🔮 Future Enhancements

For production deployment, consider:
- [ ] Database storage (PostgreSQL, MongoDB)
- [ ] Blockchain integration (OpenTimestamps, Bitcoin)
- [ ] Nostr integration for decentralized verification
- [ ] Bulk certificate generation
- [ ] Certificate revocation system
- [ ] Email delivery
- [ ] Admin authentication
- [ ] Certificate templates
- [ ] API endpoints for programmatic access

## 📄 License

This project is built for Bitcoin Dada, Dada Devs & the larger community.


**Note**: This is an MVP. For production use, implement proper database storage, authentication, and consider blockchain integration for additional immutability.
