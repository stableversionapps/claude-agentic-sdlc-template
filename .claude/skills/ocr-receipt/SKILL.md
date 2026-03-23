---
name: ocr-receipt
description: Implements document scanning and OCR pipeline using on-device OCR + Claude API for structured data extraction. Use when building document scanning or receipt processing features.
---

# OCR / Document Scanning Skill

Builds an on-device document scanning pipeline with AI-powered data extraction.

## Pipeline Architecture

```
Camera/Upload -> Image Preprocessing -> On-Device OCR -> Text Extraction -> Claude Parse -> Structured Data
```

### Step 1: Image Capture
- Support camera capture and gallery/file selection
- Auto-crop to document bounds if possible
- Support batch scanning (multiple pages/documents)

### Step 2: Image Preprocessing
- Convert to grayscale for better OCR
- Adjust contrast/brightness
- Deskew rotated images
- Compress for processing efficiency

### Step 3: On-Device OCR
- Use platform-appropriate on-device OCR (ML Kit, Vision framework, Tesseract)
- Fully on-device, no cloud API calls for OCR
- Extract text blocks with position information
- Handle multi-language documents

### Step 4: Claude API Structured Extraction
Send extracted text to Claude for parsing:
```
Extract from this document text:
- Key fields relevant to your domain
- Dates, amounts, names
- Categorization
- Confidence scores
```

Response format: structured JSON for reliable parsing.

### Step 5: Auto-Create Record
- Map extracted data to domain model
- Pre-fill form with extracted values
- Let user review and confirm before saving
- Link original document/image to record

## Privacy Notes
- OCR is 100% on-device (no cloud for text extraction)
- Document text sent to Claude only for structured parsing (no storage on server)
- Document images stored locally, encrypted
- User controls whether to keep or delete document images

## Checklist
- [ ] On-device OCR working (no cloud dependency)
- [ ] Claude prompt extracts structured data reliably
- [ ] User review step before saving
- [ ] Original document linked to created record
- [ ] Offline fallback (manual entry if OCR unavailable)
- [ ] Privacy-safe data handling
