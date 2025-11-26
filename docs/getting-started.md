---
id: getting-started
title: Getting started
sidebar_position: 2
---

# Getting started

Follow these steps to run Solution Base locally and contribute to the documentation site.

## Prerequisites

- [Node.js](https://nodejs.org/) (see `package.json` for the supported version)
- [npm](https://www.npmjs.com/)

## Install dependencies

From the project root, install required packages:

```bash
npm install
```

## Start the local dev server

Launch the Docusaurus development server:

```bash
npm run start
```

The site will be available at the URL printed in your terminal. Changes to docs and pages are hot-reloaded.

## Build for production

Generate the static site output to ensure docs and configuration are valid:

```bash
npm run build
```

Use this command before shipping changes to verify the documentation builds successfully.
