# GMI Foundation – setup
1. Firebase Console → create project. Add a **Web app**; copy its config into `.env` (from `.env.example`). Set `VITE_WHATSAPP_NUMBER` (digits, country code).
2. Build → Authentication → Sign-in method → enable **Email/Password** (phone numbers are mapped to an internal ID; passwords are hashed by Firebase).
3. Build → Firestore Database → create (production mode). Build → Storage → get started.
4. Create your admin: Authentication → Add user (email + strong password). Copy its UID. In Firestore create collection `admins`, document ID = that UID, any field (e.g. `role: "admin"`). Admins can't be created from the app.
5. `npm install -g firebase-tools && firebase login && firebase use --add`
6. `npm install && npm run dev` (test locally; admin at `/admin.html`).
7. Deploy: `npm run build && firebase deploy` (hosting + rules). Authentication → Settings → Authorized domains: add your domain if custom.
Collections: `products`, `users/{uid}` (name, phone, addresses[]), `orders/{GMI-…}`, `admins/{uid}`.
