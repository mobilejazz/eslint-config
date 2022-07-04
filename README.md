# Mobile Jazz ESLint Config

Shared ESLint config used in Mobile Jazz projects.

This is meant to be used alongside Prettier (with [`@mobilejazz/prettier-config`](https://github.com/mobilejazz/prettier-config)).

## Usage

1. Remove existing `.eslintrc.*` file, if present.
2. Install `eslint` and the config.

    ```sh
    npm install -D eslint @mobilejazz/eslint-config
    ```
3. Install all the needed dependencies from this library

    ```sh
    npx install-peerdeps --dev @mobilejazz/eslint-config
   ```
4. Add the lint configuration that you need to your`package.json`, `javascipt`, `typescript` or `angular`:

    ```json
    "eslintConfig": {
      "extends": "@mobilejazz/eslint-config/angular"
    }
    ```

### With Prettier and `@mobilejazz/prettier-config`

1. Set up Prettier and [`@mobilejazz/prettier-config`](https://github.com/mobilejazz/prettier-config/).
1. When using with Prettier and `@mobilejazz/prettier-config`, ESLint should run first. Set up your scripts in `package.json` something like this:

    ```json
    "scripts": {
      "lint": "npm run eslint && npm run prettier -- --check",
      "format": "npm run eslint -- --fix && npm run prettier -- --write",
      "prettier": "prettier \"src/**/*.ts\" \"src/**/*.js\" \"src/**/*.html\"",
      "eslint": "eslint \"src/**/*.ts\" \"src/**/*.js\" \"src/**/*.html\"",
    }
    ```

    - `npm run lint`: for checking if ESLint and Prettier complain
    - `npm run format`: attempt to autofix lint issues and autoformat code

    :memo: Not every rule in this configuration is autofixable, so `npm run format` may continue failing until lint issues are addressed manually.

### With Husky

> ⚠️ REVIEW THIS SECTION
> - Follow the same strategy as [Ionic `eslint-config`](https://github.com/ionic-team/eslint-config#with-husky)
> - Or, [use `lint-staged` as suggested by Prettier](https://prettier.io/docs/en/precommit.html#option-1-lint-stagedhttpsgithubcomokonetlint-staged)
>
> Probably we should use `lint-staged` as we're already using that in other projects.
