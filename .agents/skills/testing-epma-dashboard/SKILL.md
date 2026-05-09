---
name: testing-epma-dashboard
description: Test the ePMA Dashboard app end-to-end. Use when verifying patient list UI, symbol badge system, or icon/tooltip changes.
---

# Testing the ePMA Dashboard

## Local Setup

This is a static HTML single-file app (`index.html`). No build step or dependencies required.

```bash
cd /home/ubuntu/repos/Assignment-symbols
python3 -m http.server 8080 &
```

Then open `http://localhost:8080` in Chrome.

## Key Features to Test

### Patient List
- 5 patients: John Smith, Sarah Johnson, Michael Brown, Emily Davies, Daniel Wilson
- Each has: name, "+ Symbol" button, hospital ID, DOB, age, allergies, "View Medication Chart" button

### Symbol Badge System
1. **Add**: Click "+ Symbol" → select predefined icon or enter custom symbol/emoji → optionally add extra info → "Add Symbol"
2. **Extra Info Popup**: Click a badge with extra info → shows popup with "Extra Information" label, text, Edit and Delete buttons
3. **Edit**: Click Edit in popup → modal pre-fills current text → update and Save
4. **Delete**: Click Delete in popup → extra info removed, badge persists

### Predefined Icons
The Add Symbol modal has an icon selector with: End of Life, Learning Disability, Cytotoxic, Dementia, Oncology. These use .png images from the repo root.

### Settings Icon
A settings icon (settings.png) appears at the bottom of the page.

## Testing Tips
- Data is stored in localStorage — clear it between test runs if needed
- The app uses `textContent` (not `innerHTML`) for user-supplied data to prevent XSS
- When testing icon removal, check for broken image placeholders (missing img src)
- Maximize the browser window before recording to capture full patient list

## Devin Secrets Needed
None — this is a fully static app with no authentication or API calls.
