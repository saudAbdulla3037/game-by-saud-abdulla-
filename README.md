# SAUD ARCADE STUDIOS — Tic Tac Toe Online

A static, mobile-friendly Tic Tac Toe room game using Firebase Realtime Database. One player creates a 6-character room code; the other joins from another device. Moves sync live.

## Files
- `index.html` — game UI and multiplayer logic
- `firebase-config.js` — your Firebase web app configuration
- `database.rules.json` — starter Realtime Database security rules

## Part A — Create Firebase project
1. Open https://console.firebase.google.com/ and create a project.
2. In Project Overview, click **Add app** → Web (`</>`). Register the app.
3. Copy the Firebase config object shown by Firebase.
4. Open `firebase-config.js` and replace every `PASTE_...` value with the matching value from your config.
   - `databaseURL` must be the exact URL shown in Firebase Realtime Database.
   - `authDomain` is usually `YOUR_PROJECT_ID.firebaseapp.com`.
   - Do not publish service-account/private keys. The web config is intended to be used in browser apps.
5. In **Build → Authentication → Sign-in method**, enable **Anonymous**.
6. In **Build → Realtime Database**, click **Create Database**. You can choose a nearby region.
7. Open the **Rules** tab in Realtime Database. Replace the rules with the contents of `database.rules.json`, then click **Publish**.

These rules require anonymous sign-in and allow only signed-in room members to read a room or write its moves. This is a starter game implementation, not a cheat-proof competitive game server. Do not store personal or sensitive information in room data.

## Part B — Test locally
Because this uses JavaScript modules, don't open `index.html` by double-clicking it.
- Easiest: upload the files to GitHub and use GitHub Pages.
- Or use a local web server such as VS Code Live Server.

## Part C — Publish with GitHub Pages
1. Sign in at https://github.com/ and create a **new public repository**, e.g. `saud-tic-tac-toe`.
2. Upload `index.html`, `firebase-config.js`, and `database.rules.json` to the repository root (top level).
3. Open repository **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then Save.
6. Wait for the Pages deployment. Your website address will look like:
   `https://YOUR-GITHUB-USERNAME.github.io/saud-tic-tac-toe/`

## Play with a friend
1. Open the website on device 1 and press **Create Room**.
2. Press **Copy Room Code** and send the 6-character code to your friend.
3. Your friend opens the same website on device 2, enters the code, and presses **Join Room**.
4. Host is X; guest is O. Turns and board updates synchronize through Firebase.

## Troubleshooting
- **Firebase settings not configured:** check `firebase-config.js`; remove all `PASTE_...` placeholders.
- **auth/operation-not-allowed:** enable Anonymous sign-in in Firebase Authentication.
- **Permission denied:** publish the provided Realtime Database rules and ensure the database URL is correct.
- **Room not found:** check the six-character code and make sure the host has not closed the tab before the room was created.
- **Module/CORS error locally:** use GitHub Pages or a local web server, not `file://`.

## Important
GitHub Pages hosts the static website; Firebase provides the live multiplayer database and anonymous player identity. Both have free usage tiers/quotas and are subject to their provider terms and limits. Monitor Firebase usage. The client-side game is suitable for casual play; a production competitive game would need server-side validation to prevent cheating.
