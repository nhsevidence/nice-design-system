# NICE Experience

Welcome to NICE Experience. Your source for creating beautiful, consistent experiences across NICE.

## What is it?

NICE experience is a replacement for [NICE.Bootstrap](https://github.com/nhsevidence/NICE.Bootstrap/). It's a front-end toolkit and guidelines for rapidly building modern, accessible web apps that are consistent with the NICE brand.

## Project structure

| Folder | Description |
| ---- | ----------- |
| .github | [Github templates folder](https://help.github.com/articles/helping-people-contribute-to-your-project/) |
| [.grunt-tasks](.grunt-tasks) | Grunt task configs loaded in from Gruntfile.js |
| [src](.src) | The main source of Experience |
| - src/assets | Common static assets |
| - src/javascripts | Main Experience JS + JSDoc config and ESLint config |
| - src/stylesheets | Main Experience SASS + SASS Lint config + SASS Doc custom theme |
| web | Web app for the style guide |
| - web/client | Client side assets required for the website itself |
| - web/server | Server scripts for the website itself. /web/server/index.js is the entry point. |

## Prerequisites

You can either run the app directly on your machine with Node OR via Docker if you prefer. So, pre-requisites are:

- [Node 6+](https://nodejs.org/en/download/) (with NPM 3.9)

OR

- [Docker](https://docs.docker.com/)

## Running tasks

You can either run the app through [Docker](#option-1-docker) or via [Grunt](#option-2-grunt) (via Node) directly on your machine.

### Option 1: Docker

If you have Docker installed, then running:

`./docker-dev.sh`

from a shell is enough to:

1. build our custom image (named 'experience') if it hasn't been built already
2. share a volume of the app's code for development
3. run the container (named 'experience'), exposing necessary ports
4. run `grunt watch` inside the container

This means you can run the solution without having to get the correct version Node, install global grunt etc. It will be slow the first time as it downloads the image and gets dependencies but Docker caches everything so will be quicker on subsequent runs.

### Option 2: Grunt

We use Grunt as a task runner to build assets etc so a dependency on Node. Once built, you can run the app itself via Node directly if you want, but the easiest thing is just simply running `grunt` from the command line.

If you want to run the app directly on your machine you can do so, but you'll need:

- Node 6+
- NPM 3.9+

Before you run any tasks, you'll have to run the following from the command line to install dependencies:

- `npm i -g grunt-cli`
- `npm i`

#### Grunt

| Task | Description |
| ---- | ----------- |
| `grunt`      | Default. Lints, builds everything and runs an express server and a watch task for dev changes. |
| `grunt build` | Builds a custom modernizr package, CSS and JS. Usually not used directly. |
| `grunt serve` | Runs an express app and watches for changes |
| `grunt lint` | Lints SASS (sasslint) and JS (eslint) |
| `grunt docs` | Generates documentation JSON files for SASS and JS |
| `grunt dist` | Builds documentation, modernizr, CSS and JS in production mode (minified etc). |

#### NPM

There are a set of NPM scripts within package.json, for convenience. However, it's recommended to just use [Grunt](#grunt).

| Task | Description |
| ---- | ----------- |
| `npm start`     | Simply runs `grunt` under the hood |
| `npm test`      | TODO |
| `npm run lint`  | Lints SASS and JS (uses `grunt lint` under the hood) |
| `npm run serve` | Spins up an express server through Node directly (NOT via Grunt) on port *54321* |

#### Node

Once the app (CSS/JS etc) has been built, the express app can be run via Node directly e.g. `node web/server`. This isn't recommended for development - use Grunt instead.
