# sanjana_leafproject

# 🌿 Leafwise — AI Plant Health Companion

Leafwise is a responsive plant-health website developed by **Sanjana**. Users can upload or capture a leaf photo, receive a Groq-powered visual assessment, and get practical plant-care guidance.

## Features

- **Photo Upload:** Browse and upload JPG, PNG, or WEBP leaf photos.
- **Live Camera:** Open the camera and capture a leaf photo.
- **Leaf Validation:** Check that the image contains a clear plant leaf before analysis.
- **AI Assessment:** Identify possible conditions or report no visible disease signs.
- **Plant Identification:** Suggest the plant type when identifiable.
- **Model Certainty:** Display qualitative certainty without inventing percentage accuracy.
- **Visual Severity:** Show healthy, mild, moderate, severe, or uncertain results.
- **Affected Areas:** Display approximate AI-suggested areas to inspect when available.
- **Visible Evidence:** Explain the observations supporting the assessment.
- **Care Guidance:** Provide immediate actions and prevention suggestions.
- **Seven-Day Checklist:** Follow a daily care and monitoring plan.
- **My Plants:** Save plants and their scan history in the browser.
- **Scan Comparison:** Compare two saved leaf photos using Groq.
- **Care Reminders:** Manage reminders while the website is open.
- **LeafBuddy:** Use a floating Groq-powered plant-care chatbot.
- **Weather Guidance:** View local weather and request AI care suggestions.
- **Disease Library:** Browse educational disease information.
- **Expert Review:** Recommend specialist consultation for uncertain or severe cases.
- **PDF Reports:** Download assessment and care-plan reports.
- **Language Selection:** Request AI responses in English, Telugu, Hindi, or Kannada.
- **Separate About Page:** Learn about the project and its developer.

## Technology Stack

- HTML, CSS, and JavaScript
- Node.js 20 or newer
- Groq API for all AI features
- Open-Meteo for weather measurements
- Browser localStorage for plant records and reminders

No external npm dependencies are required.

## Project Structure

```text
Leafwise/
├── dist/
│   ├── index.html
│   ├── about.html
│   ├── styles.css
│   ├── app.js
│   ├── features.js
│   ├── camera.js
│   ├── leafbuddy.js
│   ├── about.js
│   ├── assets/
│   └── server/
├── server/
│   ├── local.mjs
│   └── ai.mjs
├── scripts/
│   └── build.mjs
├── tests/
│   └── ai.test.mjs
├── .env
├── .env.example
├── package.json
└── README.md
```

## Getting Started

### 1. Install Node.js

Install **Node.js 20 or newer**.

### 2. Open the Project Folder

Extract the ZIP and open a terminal inside the `Leafwise` folder.

```bash
cd Leafwise
```

### 3. Configure Your Groq API Key

Open `.env` and replace the dummy key with your real Groq API key.

```env
GROQ_API_KEY=gsk_REPLACE_WITH_YOUR_REAL_GROQ_API_KEY
GROQ_VISION_MODEL=qwen/qwen3.8-27b
GROQ_TEXT_MODEL=openai/gpt-oss-20b
PORT=8000
```

If `.env` is missing, copy `.env.example` and rename the copy to `.env`.

Keep the API key on the server. Never place it in browser JavaScript or upload it to a public repository.

### 4. Start the Application

```bash
npm start
```

Open:

```text
http://localhost:8000
```

Restart the server after changing `.env`.

**Do not open `index.html` directly.** AI features require the Node.js server.

## How to Analyze a Leaf

1. Click **Browse Photo** or **Take Photo**.
2. Select or capture a clear, close-up leaf photo.
3. Click **Analyze Leaf**.
4. Groq first checks whether the photo is suitable for leaf analysis.
5. Accepted photos receive a separate visual assessment.
6. Review the observations, possible condition, care suggestions, and monitoring checklist.
7. Ask **LeafBuddy** follow-up questions or download a PDF report.

## Image Validation

The application asks Groq to reject:

- Unrelated objects, people, or animals
- Fruit-only and food images
- Screenshots, documents, drawings, or artwork
- Distant garden scenes
- Blurry, poorly exposed, or ambiguous photos
- Images without a clearly visible plant-leaf subject

A second inspection occurs during assessment. Rejected images do not receive a disease result.

These checks are AI-based and cannot guarantee perfect acceptance or rejection.

## Groq Integration

All AI features use server-side Groq requests:

- Leaf-image validation
- Plant and possible disease identification
- Visual severity and certainty
- Observation explanations
- Care plans and prevention suggestions
- Seven-day monitoring plans
- Photo comparison
- Weather-related care guidance
- LeafBuddy conversations

The server uses:

```text
https://api.groq.com/openai/v1/chat/completions
```

The default vision model is a preview model. Model availability may change; update the environment variables to compatible models supported by your Groq account when needed.

Missing keys, provider errors, and incomplete responses produce clear errors. The application does not substitute a fabricated diagnosis.

## Camera Requirements

Live camera access requires:

- Camera permission
- HTTPS or `localhost`
- An available camera

If live capture is unavailable, use the device-camera fallback or upload an existing photo.

## Data and Privacy

- Selected photos, questions, and relevant assessment context are sent through the server to Groq for AI processing.
- The API key stays on the server.
- Plant records, scan previews, checklists, and reminders are stored in this browser.
- Clearing browser data removes these saved records.
- Records do not automatically sync between devices.
- Location access is optional and used to request weather measurements.

## Important Limitations

- AI assessments cannot guarantee **100% accuracy**.
- A photo assessment is not a confirmed plant-disease diagnosis.
- Model certainty is a qualitative judgment, not a calibrated probability.
- Severity describes visible symptoms in the photographed leaf.
- Highlighted boxes are approximate suggestions, not a validated diagnostic heatmap.
- Lighting, image quality, and similar symptoms can affect results.
- Seven-day plans support care and monitoring; they do not guarantee recovery.
- Saved thumbnails have lower resolution and may fail strict comparison validation.
- Reminders notify only while the application is open.
- Language selection translates key controls and requests AI descriptions in the selected language.
- PDF reports use an ASCII font, so regional-language text may show replacement characters.

Consult a local plant specialist or agronomist when symptoms are severe, spreading, or uncertain.

## Testing

Run the automated checks:

```bash
npm test
```

Tests use mocked provider responses to check validation, error handling, assessment formatting, chatbot requests, and application routes.

Real Groq responses require a valid API key and were not verified with the included dummy key.

## Build

```bash
npm run build
```

This creates a self-contained Worker at:

```text
dist/server/index.js
```

For hosted deployment, configure the Groq API key as a server secret. The local `.env` file is not embedded in the build.

## Troubleshooting

### AI is not configured

Replace the dummy `GROQ_API_KEY` in `.env` and restart the server.

### Groq rejects the request

Check your API key, model permissions, selected model, and account usage limits.

### Camera does not open

Allow camera permission, use HTTPS or localhost, and close other applications using the camera.

### Photo is rejected

Use a sharp photo with one leaf filling most of the frame, even daylight, and a simple background.

### Saved records disappear

Records are stored in the current browser. Clearing browser storage or switching browsers removes access to them.

## Developer

**Project developed by Sanjana.**
