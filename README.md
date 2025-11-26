
# API-INTEGRATION

A small JavaScript project demonstrating API integration (weather app demo included). Live demo: `weather-app-nine-rho-82.vercel.app`. ([GitHub][1])

---

## Table of contents

* [About](#about)
* [Live demo](#live-demo)
* [Features](#features)
* [Tech stack](#tech-stack)
* [Getting started](#getting-started)
* [Project structure](#project-structure)
* [Environment variables](#environment-variables)
* [Usage examples](#usage-examples)
* [Contributing](#contributing)
* [License](#license)

---

## About

This repository contains a simple frontend project that demonstrates how to integrate with external REST APIs (example: weather API). It includes a demo app, styles, and JavaScript code that fetches and displays API data.

> Note: repository metadata shows JavaScript, CSS and HTML as the primary languages. ([GitHub][1])

---

## Live demo

Open the deployed demo:
https://weather-app-nine-rho-82.vercel.app  

---

## Features

* Fetches data from external APIs (weather)
* Simple, responsive UI
* Clear separation of API logic and UI components
* Easy to extend for additional APIs or endpoints

---

## Tech stack

* JavaScript (vanilla or framework — adjust if repo uses React/Vue)
* HTML5 / CSS3
* Optional: Vercel for deployment (demo link suggests Vercel hosting). ([GitHub][1])

---

## Getting started

1. Clone the repo

```bash
git clone https://github.com/navaneeth91/API-INTEGRATION.git
cd API-INTEGRATION
```

2. Install dependencies (if there is a package.json)

```bash
npm install
# or
yarn install
```

3. Create a `.env` file (see next section), then run the dev server:

```bash
npm start
# or
npm run dev
```

If the project is purely static (no build tools), open `index.html` in your browser or serve with a simple static server:

```bash
npx serve .
```

---

## Project structure (suggested)

```
API-INTEGRATION/
├─ Weather_api/               # Weather-related code (seen in repo)
├─ public/                    # static assets
├─ src/
│  ├─ api/
│  │  └─ weather.js           # API wrapper / fetch functions
│  ├─ components/
│  ├─ styles/
│  └─ index.js
├─ .env.example
├─ package.json
└─ README.md
```

> Adjust the structure above to match the actual repository — I included `Weather_api` because it appears in the repo file list. ([GitHub][1])

---

## Environment variables

Put sensitive keys in a `.env` file (do **not** commit it).

Example `.env`:

```
# .env
REACT_APP_WEATHER_API_KEY=your_weather_api_key_here
WEATHER_API_BASE_URL=https://api.openweathermap.org/data/2.5
```

Add `.env` to `.gitignore`:

```
.env
```

---

## Usage examples

### Example: fetch current weather (pseudo-code)

```js
// src/api/weather.js
const baseUrl = process.env.WEATHER_API_BASE_URL;
const apiKey = process.env.REACT_APP_WEATHER_API_KEY;

export async function getCurrentWeather(city) {
  const url = `${baseUrl}/weather?q=${encodeURIComponent(city)}&appid=${apiKey}&units=metric`;
  const res = await fetch(url);
  if (!res.ok) throw new Error('Weather API request failed');
  return res.json();
}
```

### Example: render data in UI

```js
import { getCurrentWeather } from './api/weather';

async function showWeather(city) {
  try {
    const data = await getCurrentWeather(city);
    // Update DOM with data
  } catch (err) {
    console.error(err);
  }
}
```

Adapt the code for the framework or plain JS used in your repo.

---

## Contributing

Contributions are welcome!

* Open an issue to discuss larger changes.
* Make a branch for your feature: `git checkout -b feat/my-feature`
* Raise a pull request with a clear description of the change.
---

