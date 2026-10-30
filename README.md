# PT Tutor — Firebase edition

PT Tutor is a browser-based study platform for physical therapy students. This package is preconfigured with the Firebase Web App settings for project `pt-tutor-4b022`.

## Included
- Email/password registration, email verification, sign-in and password reset.
- Student profiles and saved lessons in Cloud Firestore.
- Gemini explanations and follow-up questions through Firebase AI Logic.
- Browser-side extraction of PDF, DOCX, PPTX, TXT, Markdown and CSV; image inputs are sent to Gemini.
- Text-to-speech.

## Important: no Firebase Storage
Firebase Storage has deliberately been removed. Uploaded files are processed in the browser for the current lesson and are not permanently stored online. This avoids requiring a billing account for Firebase Storage.

## Firebase console checklist
1. Authentication → Sign-in method → enable Email/Password.
2. Firestore Database → create the default database in production mode.
3. Firestore Rules should match the included `firestore.rules` file.
4. AI Logic → enable Firebase AI Logic and Gemini Developer API for this project. App Check is a separate abuse-protection feature; do not select a provider unless you are ready to configure it.
5. Add the final Hosting domain to Authentication → Settings → Authorized domains after deployment.

## Build and deploy
Requires Node.js 20+ and a terminal (computer or cloud development environment). In the project folder run:

```bash
npm install
npm run build
npx firebase-tools login
npx firebase-tools deploy --only hosting,firestore:rules
```

The Firebase project is already selected in `.firebaserc`. Deployment will publish the generated `dist` folder and Firestore rules.

## Android note
The Firebase Console cannot build this Vite project by itself. The source ZIP must be opened in a Node.js-capable environment, built into `dist`, then deployed with Firebase CLI. Do not upload the source ZIP as a single HTML file.

## Usage and validation
Gemini usage is subject to current quotas, model availability and pricing. A live end-to-end test still requires enabling the AI provider, installing dependencies, building, deploying, and testing sign-up, verification, saved lessons and AI responses in the user's Firebase project. This package is not yet live.
