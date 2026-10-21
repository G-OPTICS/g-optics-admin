# G-Optics starter website (Firebase)

## What is included
- `index.html`: customer storefront branded **Gayatri Opticals**
- `admin.html`: admin panel branded **G-Optics**
- `firestore.rules`: starter rules for published products and enquiries
- `firebase.json`: Firebase Hosting setup with `/admin` rewrite
- `.github/workflows/firebase-hosting.yml`: GitHub Actions deployment workflow
- `DEPLOYMENT-ON-ANDROID.md`: phone-friendly setup steps

## Important status
This is a real starter codebase, not yet a production-ready optical e-commerce system. It supports public product listing, admin sign-in, product create/publish/hide/delete, and customer enquiries after Firebase is configured. It does NOT yet include online payments, OTP, prescription uploads/history, delivery PIN validation, or order fulfilment. Do not accept real payments or prescription data yet.

## Firebase setup
1. Open Firebase Console > Authentication > Sign-in method and enable **Email/Password**.
2. Create your own admin user in Authentication.
3. Open Firestore Database and create a document in collection `admins` with document ID exactly equal to that admin user's UID. The document may contain `role: "admin"`. Keep admin UIDs private.
4. Review and publish `firestore.rules` in Firestore > Rules.
5. This project uses the existing Firebase web app config provided by the owner.

## Hosting
The included `firebase.json` serves the customer site at `/` and admin at `/admin`.
For GitHub Actions deployment, create a Firebase service account secret named `FIREBASE_SERVICE_ACCOUNT_G_OPTICS` in your GitHub repository. Do not paste service account JSON into chat or commit it to the repository. Follow the deployment guide carefully.

## Notes
- Customer enquiry form collects name, phone and message. Add a privacy notice before public launch.
- Customer-facing images should use URLs you have permission to use.
- Verify the exact shop address and phone number before launch.
