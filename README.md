# Indonesia Holiday Creative Studio — Phase 3

## What is included
- `index.html`: Phase 2 library plus Phase 3 AI Image Generator UI.
- `api/generate.js`: Vercel serverless API. OpenAI API key stays on the server.
- `package.json`: OpenAI SDK dependency.
- `.env.example`: environment variable names only; never put a real key here or commit it.
- `vercel.json`: Vercel function configuration.

## Important: back up Phase 2 data before moving to Vercel
The GitHub Pages URL and Vercel URL have different browser origins, so existing `localStorage` data does not automatically appear on Vercel. Before switching, open the current GitHub Pages app, go to Dashboard, click **Export library backup**, and keep the downloaded JSON file. After deploying to Vercel, open the Vercel app, go to Dashboard, click **Import backup**, and select that JSON file.

## Deploy with GitHub + Vercel
1. Replace the repository's root `index.html` with this project's `index.html`.
2. Add the `api` folder and upload `api/generate.js`.
3. Add `package.json`, `vercel.json`, `.gitignore`, and `.env.example` to the repository root.
4. Push/commit all files to the `main` branch.
5. Sign in to Vercel and import the GitHub repository.
6. In Vercel → Project → Settings → Environment Variables, add:
   - `OPENAI_API_KEY` = your secret OpenAI API key
   - `OPENAI_IMAGE_MODEL` = `gpt-image-2.6-sunburst` (optional; this is the default)
7. Redeploy the project from Vercel.
8. Open the Vercel deployment URL and test Design Setup → Generate AI Image.

## Important
- Do not put a real API key in `index.html`, GitHub, or `.env.example`.
- GitHub Pages cannot execute `/api/generate`; use the Vercel deployment URL for Phase 3.
- The browser sends up to five selected visual images plus one optional face reference to the Vercel API when the user clicks Generate.
- References are compressed in the browser before upload. Vercel request size is limited by this starter implementation.
- Image generation is paid API usage. Check your OpenAI API billing, usage limits, and model access.
- `localStorage` is still browser-local. It is not cloud storage or a cross-device backup.
- This starter does not yet save generated images to cloud storage or create a permanent generation history.
- Face reference is best-effort visual guidance, not a guarantee of exact likeness. Only upload images you have permission to use.
