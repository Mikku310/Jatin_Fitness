FITNESS COMMAND CENTER V2

WHAT IS INCLUDED
- Email/password account creation and sign-in
- Cloud synchronization through Firebase Cloud Firestore
- Password reset
- Per-user Firestore security rules
- Responsive Dashboard, Daily Check-In, Routine, History and Backup
- Tuesday and Wednesday: morning workout, then Kriya + Meditation, no run, dinner at the part-time job, mandatory evening HIIT, freshen up and sleep
- Updated day scoring: Tuesday and Wednesday require Strength, Kriya and HIIT; Run is automatically treated as not required

SETUP
1. Create a Firebase project in Firebase Console.
2. Add a Web App to the project and copy its configuration values into firebase-config.js.
3. In Authentication, enable Email/Password.
4. Create a Cloud Firestore database.
5. Publish the contents of firestore.rules as the database security rules.
6. Upload index.html and firebase-config.js to a static host. Both files must be in the same folder.

FIREBASE HOSTING OPTION
- Install Firebase CLI, sign in, initialize Hosting, choose this folder as the public folder, and deploy.
- Do not select index.html replacement when prompted.

GITHUB PAGES OPTION
- Upload index.html and firebase-config.js to the repository root.
- Publish the repository through GitHub Pages.
- In Firebase Authentication Settings, add the GitHub Pages domain to Authorized domains.

DATA MODEL
users/{firebase-auth-uid}
  settings: startWeight, goalWeight, weeklyRun, waterGoal
  logs: object keyed by YYYY-MM-DD

SCORING LOGIC
Six equally weighted checks are used:
1. Kriya completed
2. Strength completed, required Monday-Saturday including Tuesday and Wednesday; Sunday is exempt
3. HIIT completed
4. Run completed when scheduled; Tuesday and Wednesday are automatically exempt
5. Water goal reached
6. At least seven hours of sleep

Score = completed applicable checks / 6 x 100.

SECURITY NOTE
Before real use, deploy firestore.rules. Those rules restrict each signed-in user to the record whose ID matches their authentication UID.
