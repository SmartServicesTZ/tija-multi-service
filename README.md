# TIJA MULTI SERVICE

Static GitHub Pages frontend using Firebase Authentication (phone + password through an internal email alias) and Cloud Firestore.

## Setup required before real accounts work
1. Create a **separate Firebase project for TIJA** (do not reuse another product's Firebase project).
2. In Firebase Authentication, enable **Email/Password**.
3. Create a Cloud Firestore database.
4. Copy the Firebase Web App config into `firebase-config.js`. The web config is public; never put service-account keys or private API secrets in this repository.
5. Publish `firestore.rules` in Firebase Console.
6. Create the first admin user through the registration screen as a CUSTOMER, then in Firestore create document `admins/{that-user-uid}` (any fields, e.g. `createdAt`). Then change `users/{uid}` role to `ADMIN` and status to `ACTIVE`. Never expose public ADMIN registration.
7. In GitHub repository Settings → Pages, set source to Deploy from a branch, branch `main`, folder `/ (root)`.

## Current first milestone
- Public landing page and essential services catalogue.
- Customer and agent registration with first name, last name, Tanzania phone number and password.
- Phone + password login (Firebase Email/Password with internal alias `<digits>@accounts.tija.local`; users only enter phone).
- Agent accounts start as PENDING_APPROVAL.
- User dashboard and service request submission to Firestore.
- Admin access is controlled by a separate `admins/{uid}` allowlist document.

## Important limits
- This is not connected to NIDA, TRA, RITA, government systems, mobile-money payments or external service APIs.
- Service requests are requests for assistance, not official submissions.
- The Firebase project setup is required before authentication and database actions can run.
