# Dr. Preeti Samal — Patient Website

Published build of the patient app, served by GitHub Pages at
**https://buccikumari2158-coder.github.io/dr-preeti-patient-web/**

This repository holds **build output only**. The source code is private, in
`dr-preeti-patient-app`. Everything here is already public the moment anyone
loads the site — it contains no secrets, only the Firebase *client* config,
which is a public identifier. Access is enforced by Firestore security rules.

## Regenerating

From the private source repo:

```bash
cd artifacts/mobile
# app.json must set experiments.baseUrl to "/dr-preeti-patient-web" so asset
# URLs resolve under the GitHub Pages subpath.
npx expo export --platform web --output-dir pages-build
cp pages-build/index.html pages-build/404.html   # SPA deep links
touch pages-build/.nojekyll                       # keep the _expo/ folder
```

Then commit the contents of `pages-build/` to this repository's `main` branch.

`.nojekyll` is required: without it GitHub Pages runs Jekyll, which strips
directories beginning with an underscore, and `_expo/` holds the entire bundle.
