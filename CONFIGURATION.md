# Configuration (GitHub Pages / Static Hosting)

This app currently references:
- `__firebase_config`
- `__app_id`

Those are injected automatically in some hosted environments, but **not** on GitHub Pages.

## Quick fix for GitHub Pages

Edit `index.html` and replace:

```js
firebase: JSON.parse(__firebase_config),
appId: typeof __app_id !== 'undefined' ? __app_id : 'urban-forge-prod',
```

with your own Firebase config object:

```js
firebase: {
  apiKey: "YOUR_FIREBASE_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "SENDER_ID",
  appId: "FIREBASE_APP_ID"
},
appId: "urban-forge-prod",
```

If you **don't** want Firebase at all, remove the Firebase imports and usage (auth/db) and the app will still run as a pure local tool.

## Gemini API
Set `CONFIG.apiKey` to your Gemini API key if you want AI responses to work.
If `CONFIG.apiKey` is empty, AI calls will fail gracefully.
