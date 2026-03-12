# CityLens AI

Montgomery, Alabama's AI-powered civic permit navigator.

**Live demo:** Tell it your business idea in plain English → get your exact permit roadmap in under 60 seconds.

## Quick Deploy to Vercel

### 1. Clone and install

```bash
git clone https://github.com/yourname/citylens-ai
cd citylens-ai
npm install
```

### 2. Set up environment

```bash
cp .env.example .env
# Edit .env — add your ANTHROPIC_API_KEY
# Get your key at: https://console.anthropic.com
```

### 3. Test locally

```bash
npm run dev
# Opens at http://localhost:3000
```

### 4. Deploy to Vercel

```bash
# Install Vercel CLI if needed
npm i -g vercel

# Deploy
vercel

# Set your API key in Vercel
vercel env add ANTHROPIC_API_KEY
# Paste your key when prompted

# Deploy to production
vercel --prod
```

That's it. Your app is live.

## Project Structure

```
/citylens-ai
├── /src
│   ├── App.jsx                    # Root — header, routing, demo mode
│   ├── main.jsx                   # Vite entry point
│   ├── index.css                  # Tailwind + design tokens
│   ├── /pages
│   │   ├── InputPage.jsx          # Landing page + tutorial modal
│   │   └── ResultsPage.jsx        # Full results output page
│   ├── /components
│   │   └── PermitCard.jsx         # Expandable permit step card
│   └── /data
│       └── knowledgeBase.json     # All business type data (verified)
├── /api
│   ├── generate.js                # Vercel serverless — Claude API call
│   └── translate.js               # Vercel serverless — Spanish translation
├── vercel.json                    # Deployment config
├── .env.example                   # API key template
└── README.md
```

## Features

- **Plain-English Input** — no forms, no dropdowns
- **AI Classification** — Claude maps your description to 1 of 9 business types
- **Permit Checklist** — legally-sequenced steps with real fees + contacts
- **First Action Box** — specific next step with department phone
- **Risk Warnings** — common mistakes that delay approvals
- **PDF Export** — downloadable full roadmap (client-side, no backend)
- **Spanish Toggle** — full translation with one click
- **Demo Mode** — Ctrl+Shift+D for cached responses (hackathon use)

## Adding Business Types

Edit `src/data/knowledgeBase.json` and add a new object to the `business_types` array. Follow the exact same schema as existing entries. The AI will automatically classify user inputs to your new type using the `classification_keywords` array.

## Security Notes

- `ANTHROPIC_API_KEY` is only in Vercel env vars — never in the browser bundle
- The `/api/` routes are server-side Vercel functions
- No user data is stored — session state only
- All inputs are validated (length, type) before API calls

## License

MIT
