# Peer Tutoring Network — secure Firebase edition

This is a rebuilt, functional starter, not a drop-in replacement for the old localStorage demo. It includes Firebase email/password accounts, server-enforced coordinator permissions, approved tutor directory, booking requests, tutor acceptance/decline, and coordinator-verified volunteer hours.

## One-time setup (required)
1. Create a free Firebase project at https://console.firebase.google.com/ (free quotas apply).
2. In **Authentication > Sign-in method**, enable **Email/Password**.
3. In **Firestore Database**, create a database in production mode.
4. In **Project settings > Your apps**, register a Web app and copy its Firebase config into `firebase-config.js`.
5. In **Authentication > Settings > Authorized domains**, add `seifkesseba.github.io` (and your custom domain if any).
6. Create the coordinator's Firebase Authentication account through the website. In Firebase Console > Authentication > Users, copy that account's **UID**.
7. Replace `REPLACE_WITH_COORDINATOR_FIREBASE_AUTH_UID` with the UID in BOTH `app.js` and `firestore.rules`.
8. In Firestore > Rules, paste `firestore.rules` and click **Publish**. Rules are essential: without them, this application is NOT secure.
9. Upload `index.html`, `app.js`, `firebase-config.js` to the root of your PUBLIC GitHub repository, with GitHub Pages set to main / root. Do NOT upload the rules file expecting GitHub to enforce it: publish rules in Firebase Console.
10. Test with three separate browser profiles: student, tutor, coordinator. Sign up a tutor, approve it as coordinator, book as student, accept as tutor, log hours, verify as coordinator.

## Important limitations
- This rebuild simplifies the original visual design and replaces the original username login with email/password.
- No email notifications, payment processing, calendar synchronization, identity verification, or automatic teacher endorsements.
- Coordinator interview verification must actually happen offline; clicking Approve alone does not prove qualifications.
- Email verification and abuse/rate controls are recommended before public launch.
- Booking times are requests, not calendar availability guarantees.
- Firestore free quotas may be sufficient for a small pilot, but are not unlimited.
- Never store student passwords in Firestore. Firebase Authentication handles password storage.
- Do not publish personal student phone numbers, private grades, or public activity logs without explicit permissions.
- Review your school's privacy, parental consent, and safeguarding policies before allowing minors to use the site.
