# Phone-friendly deployment guide

## A. Upload these files to GitHub from Android
1. Download and extract `g-optics-starter.zip` on your phone.
2. Open GitHub in Chrome and sign in.
3. Create a **private** repository named `g-optics-website` (recommended while configuring).
4. Upload the extracted files and folders from this ZIP to the repository root. Keep `.github/workflows/firebase-hosting.yml` in its folder structure. GitHub mobile upload may hide dotfiles; if so, upload `.github/workflows/firebase-hosting.yml` using GitHub's browser desktop mode or create the workflow file directly on GitHub.
5. Commit to the `main` branch.

## B. Set up Firebase Authentication
1. Firebase Console > Authentication > Get started (if needed).
2. Sign-in method > enable Email/Password.
3. Add your own admin user. Do not create a public sign-up screen.

## C. Add the admin UID
1. Authentication > Users > tap your admin user and copy its UID.
2. Firestore Database > create collection `admins`.
3. Document ID must be that exact UID. Add field `role` (string) = `admin`.
4. Publish `firestore.rules` in Firestore > Rules. Do not leave Firestore in test mode.

## D. Set up automatic Hosting deploy
This workflow deploys on every push to `main`.
1. In Google Cloud Console for project `g-optics`, create a dedicated service account for deployment with only the permissions needed to deploy Firebase Hosting. Do not use an Owner account key.
2. Create a key only if required by the chosen GitHub deployment method. Treat the JSON as a secret.
3. In GitHub repository > Settings > Secrets and variables > Actions > New repository secret, name it exactly `FIREBASE_SERVICE_ACCOUNT_G_OPTICS`, and paste the full service-account JSON there. Never commit it or send it in chat.
4. GitHub > Actions tab > enable workflows if prompted. Check the latest workflow run.
5. Once deployment succeeds, open Firebase Console > Hosting to find the live `web.app` URL. The admin page is at `/admin`.

## Important
- Do not click Upgrade or enable billing just to follow this guide. If Firebase asks for a billing plan, stop and tell me what message it shows.
- If the GitHub action fails, send the error screenshot with secrets hidden.
- This is a starter, not a complete production store. Payments, OTP, prescription records/uploads, customer order tracking, privacy notice and full security review still need implementation before real launch.
