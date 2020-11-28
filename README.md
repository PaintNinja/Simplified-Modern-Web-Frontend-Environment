# Simplified-Modern-Web-Frontend-Environment

Yarn v2 + LitElements + Snowpack + TypeScript

## Introduction

Front-end web development projects have become increasingly complex, to the point where it feels more like it's intended for Linux tinkerers rather than for actual development.

A huge node_modules folder for each project, manual configuration of Webpack or Rollup, lots of framework boilerplate and setup to show an element on the page, various different incompatible frameworks, libs and tools that all attempt to accomplish the same goal in their own way, having a routing library just to navigate between different pages... the list goes on and on.

Some people have come to accept that this is the way it is and deal with it, **but it doesn't have to be this way** - modern web browsers implement all the things you need to create complex webapps natively, node-compatible package managers exist that don't dump every single file of a dependency in a folder and lightweight frameworks exist that helps you write stuff in a standards-compliant way without repeating yourself too often.

I'm not saying that we should dump everything and go back to writing just plain HTML+CSS+JS, but we can do better.

The existing popular tools aren't necessarily bad either - they still have many cases where they make sense - but we shouldn't be applying them to everything. Most frontends can be accomplished purely with standardised web technologies, but I still recognise the benefit of lightweight frameworks and tools that help you write less code and get things done faster without deviating too much from the standard.

This template is a proposed solution for most frontend needs, minus the complexity.

## How to use

### To install

_DON'T `npm install`!_

#### 1. Grab and extract the repo zip

- You can download it here: https://github.com/PaintNinja/Simplified-Modern-Web-Frontend-Environment/archive/main.zip
- Extract it to a new empty folder.
- Enter the folder in a terminal. On Windows you can go to the folder in File Explorer then shift + right click -> open in command prompt/powershell/windows terminal

#### 2. `yarn set version berry`

This sets the yarn version to v2 (aka "berry") rather than the legacy "Yarn Classic" v1 branch.

You should run this once before proceeding with any of the below steps to avoid node_modules bloat.

#### 3. `yarn install`

This sets up the dev environment, grabbing any missing dependencies.

#### 3. IDE setup

`yarn pnpify --sdk vscode`

If using VS Code, run this and then restart VS Code to fix IDE "module not found" errors.

Once VS Code has restarted, make sure you install the workspace recommended extensions and allow the TypeScript version to use the workspace version.

- For VIM, replace `vscode` in the command above with `vim`
- For Emacs, see this guide: https://next.yarnpkg.com/getting-started/editor-sdks#emacs

Now you can open the project folder in your preferred IDE.

#### 4. Opening in your IDE

Right click on the same folder this readme is in, click "Open folder in VS Code" or the IDE of your choice.

- Your source code goes in the `src` and `public` folders, depending on what you're doing.

### To develop

`yarn snowpack dev` or `yarn start`

Runs the app in the development mode.
Open http://localhost:8080 to view it in the browser.

The page will reload if you make edits.
You will also see any lint errors in the console.

### To build

`yarn build`

Builds the app for production to the `dist` folder.
It correctly bundles the app in production mode and optimizes the build for the best performance.

## What each thing does

If, like me, you want to know what you're getting yourself into but don't want to spend ages figuring it out for yourself, I've provided a list of folders and relevent files and explained in short informal terms what each thing does. :)

```
│   .npmignore # avoids packaging unnecessary stuff
|
│   .pnp.js # what Yarn v2 uses as a more efficient node_modules alternative, things in here are extracted to a
|           # proper node_modules folder when necessary in a transparent manner, basically meaning you don't have
|           # to worry about it
|
│   .prettierrc # Config file for the prettier. The prettier formats your source code for you so that the code style is as
|               # described in this file. You might want to change this according to your personal preferences, so edit this
|               # accordingly. The docs for each option can be found here: https://prettier.io/docs/en/options.html
|
│   .yarnrc.yml # Tells the yarn command to use Yarn v2/Berry instead of Yarn v1/Classic
|
│   babel.config.json # Adds support for TypeScript and the JS decorators proposal to Babel, which is used by Snowpack and
|                     # Lit-Elements.
│
|   LICENSE # Change this according to your preferred license. The default is this repo's permissive MIT license
│
|   package.json # This template is based on @snowpack/app-template-lit-element-typescript, the package.json is what yarn uses
|                # to determine what packages are needed and some metadata for publishing on npm later on, as well as some
|                # script definitions (for example, you can type yarn lint instead of prettier --check \"src/**/*.ts\")
│
|   README.md # this readme file
│
|   snowpack.config.js # Tells snowpack where the source files are and what plugins to use to work properly with Lit-Elements
|                      # Also sets up basic release build optimisation, including minification and link rel="modulepreload"
|                      # without needing a bundler
│
|   tsconfig.json # TypeScript compiler settings, adds support for the JS decorators proposal
│
|   yarn.lock # yarn makes this after a yarn install command, it needs it to work properly
│
├───.vscode # makes VS Code work with the Yarn v2 pnp.js and prettier formatter (.prettierrc), fixes "node module not found"
│       extensions.json
│       settings.json
│
├───.yarn # similar to yarn.lock, yarn needs this to work properly
│   |
|   └───unplugged # sometimes stuff won't work inside Yarn's pnp.js, so it may get "unplugged" (extracted) here
│
├───node_modules # things in pnp may be extracted here when necessary
│
├───public # put your source code in the ./public and ./src folders.
|          # stuff currently in here is some minimal example code to get you started
│       favicon.ico
│       index.css
│       index.html
│       robots.txt
│
├───src # put your source code in the ./public and ./src folders
|       # stuff currently in here is some minimal example code to get you started
│       app-root.ts
│       index.ts
```
