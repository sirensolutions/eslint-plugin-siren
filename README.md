# Siren ESLint Configuration and Rules

This repo consists of a standard rule configuration that can be extended, as well as custom rules created in-house.

## Config

To use the config:

1. Install the repo:
   ```shell
   npm install --save-dev eslint-plugin-siren@sirensolutions/eslint-plugin#<tag>
   ```
   Where `<tag>` is the [latest tag available](https://github.com/sirensolutions/eslint-plugin/tags). 

1. Install the peer dependencies
   ```shell
   npm install --save-dev \
      eslint \
      eslint-plugin-jest \
      eslint-plugin-react \
      eslint-plugin-react-hooks \
      eslint-plugin-import \
      eslint-plugin-mocha \
      eslint-plugin-prefer-object-spread \
      eslint-plugin-babel \
      eslint-plugin-ban \
      eslint-plugin-jsx-a11y \
      eslint-plugin-no-unsanitized \
      eslint-import-resolver-node \
      babel-eslint \
      sync-request \
      typescript \
      @typescript-eslint/eslint-plugin \
      @typescript-eslint/parser
   ```
   When [eslint/eslint#13481](https://github.com/eslint/eslint/issues/13481) is complete, you will no longer have to install peer dependencies for ESLint configs, but for now it's a necessary evil.

1. Update your `.eslintrc.yml` (or whatever you've called it) to extend from `plugin:siren/recommended`
   ```yaml
   extends: ['plugin:siren/recommended']
   ```

1. Ensure that your NPM script or Gulp task includes your `package.json` file so the `same-core-dependency-version` rule can check it. We recommend the following entry in your `package.json`:
   ```json5
   "lint": "eslint '**/*.{js,ts,jsx,tsx}' package.json",
   ```

## Rules

Check the [`rules`](./rules) directory to see documentation about each rule.

## Contributing
 - All the new PRs merge into master and should increment the version.
 - Once merged, tag the new commit in master and update [all Siren repos that use it](https://github.com/search?q=org%3Asirensolutions+filename%3Apackage.json+fork%3Atrue+eslint-plugin&type=Code) with the latest tag.
 - If changed/added rules cause lint failures, they can be manually disabled with a ticket created on the appropriate team to update their code.
