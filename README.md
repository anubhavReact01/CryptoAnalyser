# CryptoAnalyser - Explore the World of Cryptocurrency

**CryptoAnalyser** is a React-based project designed to provide real-time information on cryptocurrencies using powerful APIs from [RapidAPI](https://rapidapi.com). This application is suitable for developers looking to master React.js and API integration while exploring the world of digital currencies.

## Demo
Check out the video tutorial on **Dev. Shivansh Vasu** channel:
- [YouTube Channel](https://www.youtube.com/@shivanshvasu/videos)

## Table of Contents
1. [Introduction](#introduction)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Setup Instructions](#setup-instructions)
5. [Project Structure](#project-structure)
6. [Scripts](#scripts)
7. [API Integration](#api-integration)

## Introduction
This project allows users to:
- Track live cryptocurrency prices.
- View historical trends with interactive charts.
- Analyze global crypto market trends and statistics.

## Features
- **Real-Time Data:** Stay updated with live crypto data.
- **Interactive Charts:** Visualize market trends with Chart.js.
- **Responsive Design:** Built using Ant Design for an intuitive UI.
- **API Integration:** Leverages multiple APIs via RapidAPI.
- **State Management:** Efficiently managed with Redux Toolkit.

## Technologies Used
- **Frontend Framework:** React.js
- **UI Library:** Ant Design
- **State Management:** Redux Toolkit
- **HTTP Requests:** Axios
- **Charting Library:** Chart.js and React-Chartjs-2
- **Utility Libraries:** Moment.js, Millify

## Setup Instructions
### Prerequisites
Make sure you have the following installed:
- Node.js (v14 or later)
- npm (v6 or later) or Yarn

### Steps
0. Copy .env.example to .env and paste your credentials.
1. Clone the repository:
   ```bash
   git clone https://github.com/ShivaMani02/CrytoAnalyser-Project-react
   ```

2. Navigate to the project directory:
   ```bash
   cd CryptoAnalyser
   ```

3. Install dependencies:
   ```bash
   npm install
   ```

4. Start the development server:
   ```bash
   npm start
   ```

5. Open the app in your browser at `http://localhost:3000`.

## Project Structure
```
CryptoAnalyser/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── Navbar.jsx
│   │   ├── CryptoList.jsx
│   │   ├── CryptoDetails.jsx
│   │   └── Chart.jsx
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── Cryptocurrencies.jsx
│   │   ├── News.jsx
│   │   └── Details.jsx
│   ├── app/
│   │   ├── store.js
│   │   └── api.js
│   ├── assets/
│   ├── App.js
│   ├── index.js
│   └── styles.css
├── .eslintrc.js
├── package.json
└── README.md
```

## Scripts
- **Start Development Server:**
  ```bash
  npm install
  npm start
  ```

- **Build for Production:**
  ```bash
  npm run build
  ```

- **Run Tests:**
  ```bash
  npm test
  ```

## API Integration
This project uses APIs from RapidAPI for fetching cryptocurrency data. Replace placeholders in `api.js` with your RapidAPI key.

Example:
```javascript
const options = {
  method: 'GET',
  url: 'https://api.rapidapi.com/endpoint',
  headers: {
    'X-RapidAPI-Key': 'YOUR_RAPIDAPI_KEY',
    'X-RapidAPI-Host': 'api.rapidapi.com'
  }
};
```

## Contributing
We welcome contributions! To contribute:
1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m 'Add some feature'
   ```
4. Push to the branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---
**Happy Coding!** 🎉

<!-- 

The Netlify deploy errored, with the following guidance provided:

Diagnosis
- Relevant log lines show the build failed during the production build with an OpenSSL/crypto error: [line 93](#L93)-[line 100](#L100) and the detailed stack + OpenSSL error codes at [line 113](#L113)-[line 131](#L131).
- The logs also show Netlify installed Node v22.22.3 for the build: [line 132](#L132).
- The build command run was npm run build using react-scripts (create-react-app): [line 88](#L88)-[line 90](#L90) and the failure bubbled out from react-scripts: [line 110](#L110)-[line 114](#L114).

Error type and cause
- Error: ERR_OSSL_EVP_UNSUPPORTED (OpenSSL digital envelope routines unsupported).
- Cause: Newer Node.js (v17+) ships with OpenSSL 3 which disables legacy crypto providers by default. Older webpack/react-scripts or crypto usages expect legacy OpenSSL algorithms; calling createHash fails. Netlify is using Node v22 in your build environment, which triggers this error.

Solution — two options (pick one)

Option A — Quick fix (recommended)
- Set the environment variable NODE_OPTIONS=--openssl-legacy-provider for the Netlify build so Node will allow the legacy OpenSSL provider during the build.
- How to apply:
  - In Netlify UI: Site settings → Build & deploy → Environment → Add variable
    - Key: NODE_OPTIONS
    - Value: --openssl-legacy-provider
  - Or change your build command in Netlify to prepend the var (Linux build environment), e.g.:
```bash
NODE_OPTIONS=--openssl-legacy-provider npm run build
```
- Trigger a new deploy after adding the env var.

Option B — Preferred/longer-term: pin to a Node LTS that works (e.g. Node 18)
- Ensure you have either an .nvmrc file with "18" or add an engines field to package.json to tell Netlify which Node version to use. Before doing that, verify your package.json is committed to the repository.
- Example: add to package.json:
```json
{
  "engines": {
    "node": "18.x"
  }
}
```
- Or create a .nvmrc file at repo root with:
```
18
```
- Commit and push, then trigger a new deploy. See Netlify docs for changing Node versions: https://docs.netlify.com/configure-builds/manage-dependencies/#node-js-and-javascript

Notes and additional options
- Upgrading react-scripts/webpack to versions compatible with OpenSSL 3 (if available for your project) is the longer-term fix so you don't rely on the legacy provider.
- If you choose Option B (pin Node), Netlify will use that Node version during install/build. If you choose Option A, no code changes are needed — just the environment variable or updated build command.

Follow-up
- After applying one of the above solutions, redeploy. If you still see the same error, attach the updated build log lines around the same error lines for a re-check.

The relevant error logs are:

Line 0: build-image version: ac6eb13fbf000e5c09ad677efd8b7c3c2d0142b6 (noble-new-builds)
Line 1: buildbot version: de14d13d022c18f089944497bd804e269fc4f82f
Line 2: Fetching cached dependencies
Line 3: Failed to fetch cache, continuing with build
Line 4: Starting to prepare the repo for build
Line 5: No cached dependencies found. Cloning fresh repo
Line 6: git clone --filter=blob:none https://github.com/anubhavReact01/CryptoAnalyser
Line 7: Preparing Git Reference refs/heads/main
Line 8: Installing dependencies
Line 9: mise ~/.config/mise/config.toml tools: python@3.14.3
Line 10: mise ~/.config/mise/config.toml tools: ruby@3.4.8
Line 11: mise ~/.config/mise/config.toml tools: go@1.26.2
Line 12: Downloading and installing node v22.22.3...
Line 13: Downloading https://nodejs.org/dist/v22.22.3/node-v22.22.3-linux-x64.tar.xz...
Line 81: ​
Line 82: ❯ Context
Line 83:   production
Line 84: ​
Line 85: Build command from Netlify app                                
Line 86: ────────────────────────────────────────────────────────────────
Line 87: ​
Line 88: $ npm run build
Line 89: > CrytoAnalyser@0.1.0 build
Line 90: > react-scripts build
Line 91: Failed during stage 'building site': Build script returned non-zero exit code: 2
Line 92: Creating an optimized production build...
Line 93: Error: error:0308010C:digital envelope routines::unsupported
Line 94:     at new Hash (node:internal/crypto/hash:101:19)
Line 95:     at Object.createHash (node:crypto:139:10)
Line 96:     at module.exports (/opt/build/repo/node_modules/webpack/lib/util/createHash.js:135:53)
Line 97:     at NormalModule._initBuildHash (/opt/build/repo/node_modules/webpack/lib/NormalModule.js:417:16)
Line 98:     at handleParseError (/opt/build/repo/node_modules/webpack/lib/NormalModule.js:471:10)
Line 99:     at /opt/build/repo/node_modules/webpack/lib/NormalModule.js:503:5
Line 100:     at /opt/build/repo/node_modules/webpack/lib/NormalModule.js:358:12
Line 101:     at /opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:373:3
Line 102:     at iterateNormalLoaders (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:214:10)
Line 103:     at iterateNormalLoaders (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:221:10)
Line 104:     at /opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:236:3
Line 105:     at runSyncOrAsync (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:130:11)
Line 106:     at iterateNormalLoaders (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:232:2)
Line 107:     at Array.<anonymous> (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:205:4)
Line 108:     at Storage.finished (/opt/build/repo/node_modules/enhanced-resolve/lib/CachedInputFileSystem.js:55:16)
Line 109:     at /opt/build/repo/node_modules/enhanced-resolve/lib/CachedInputFileSystem.js:91:9
Line 110: /opt/build/repo/node_modules/react-scripts/scripts/build.js:19
Line 111:   throw err;
Line 112:   ^
Line 113: Error: error:0308010C:digital envelope routines::unsupported
Line 114:     at new Hash (node:internal/crypto/hash:101:19)
Line 115:     at Object.createHash (node:crypto:139:10)
Line 116:     at module.exports (/opt/build/repo/node_modules/webpack/lib/util/createHash.js:135:53)
Line 117:     at NormalModule._initBuildHash (/opt/build/repo/node_modules/webpack/lib/NormalModule.js:417:16)
Line 118:     at /opt/build/repo/node_modules/webpack/lib/NormalModule.js:452:10
Line 119:     at /opt/build/repo/node_modules/webpack/lib/NormalModule.js:323:13
Line 120:     at /opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:367:11
Line 121:     at /opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:233:18
Line 122:     at context.callback (/opt/build/repo/node_modules/loader-runner/lib/LoaderRunner.js:111:13)
Line 123:     at /opt/build/repo/node_modules/babel-loader/lib/index.js:59:103 {
Line 124:   opensslErrorStack: [
Line 125:     'error:03000086:digital envelope routines::initialization error',
Line 126:     'error:0308010C:digital envelope routines::unsupported'
Line 127:   ],
Line 128:   library: 'digital envelope routines',
Line 129:   reason: 'unsupported',
Line 130:   code: 'ERR_OSSL_EVP_UNSUPPORTED'
Line 131: }
Line 132: Node.js v22.22.3
Line 133: ​
Line 134: "build.command" failed                                        
Line 135: ────────────────────────────────────────────────────────────────
Line 136: ​
Line 137:   Error message
Line 138:   Command failed with exit code 1: npm run build
Line 139: ​
Line 140:   Error location
Line 141:   In Build command from Netlify app:
Line 142:   npm run build
Line 143: ​
Line 144:   Resolved config
Line 145:   build:
Line 146:     command: npm run build
Line 147:     commandOrigin: ui
Line 148:     publish: /opt/build/repo/build
Line 149:     publishOrigin: ui
Line 150: Build failed due to a user error: Build script returned non-zero exit code: 2
Line 151: Failing build: Failed to build site
Line 152: Finished processing build request in 23.712s

 -->