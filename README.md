# developer.gov.sg

[![Netlify Status](https://api.netlify.com/api/v1/badges/780ed541-5952-4726-9aa1-f3d1a58f36c0/deploy-status)](https://app.netlify.com/sites/developer-gov-sg/deploys)
[![Known Vulnerabilities](https://snyk.io//test/github/GovTechSG/developer.gov.sg/badge.svg?targetFile=package.json)](https://snyk.io//test/github/GovTechSG/developer.gov.sg?targetFile=package.json)
[![GuardRails badge](https://badges.guardrails.io/GovTechSG/developer.gov.sg.svg)](https://dashboard.guardrails.io/default/gh/GovTechSG/developer.gov.sg)

## Contribution and approval flow

Contribution suggestions made from https://developer.gov.sg are transformed into pull requests from automatically generated branches into the `dev` branch.

Reviewers should approve and merge or reject these pull requests.

The dev branch will be manually promoted to master for deployment periodically.

## Development

### Requirements

-   Node.js v10 / npm v6
-   rbenv\* with Ruby 2.5

\*npm commands detailed below assume the usage of [rbenv](https://github.com/rbenv/rbenv) to manage your Ruby environment. See `package.json`.

### Local development

#### Setup

```sh
# Jekyll only
gem install jekyll bundler

bundler install

bundle exec jekyll serve

# Webpack/static files
npm install
```

#### Run locally - frontend only

Recommended: run webpack and jekyll in separate terminal sessions, the access the site through localhost:4000. This is to allow for easy termination of both processes.

```sh
# Terminal 1
# jekyll dev server on localhost:4000; watches and builds site at _site/
npm run dev:jekyll
```

```sh
# Terminal 2
# webpack in watch mode; runs tasks like vue app compilation and image compression
npm run dev:static
```

### Local Netlify functions

Set up local development environment above first.
You will need to have access to a Netlify project of this repo.

```sh
npm install netlify-cli -g # Install Netlify cli globally

netlify link # Follow instructions to link to Netlify project
```

As before, it is recommended to run netlify dev and webpack in separate terminal sessions.

```sh
# Terminal 1
# This runs netlify dev, runs jekyll's development server and local lambda functions
npm run dev:netlify
```

```sh
# Terminal 2
npm run dev:static
```

The frontend will be available at **localhost:8888**. Netlify CLI will sync build settings such as environment variables for functions from the linked Netlify project, so they will be fully functional.
