**Integrating linting on react project**

Integrating linting to any project is important to keep it clean.

Let's see how to integrate linting into a react project. So on a higher level, these are the things to do -

1. Get the linting packages installed.
2. Configure/Customize the rules for linting you need.
3. Install plugins on your IDE to work with the linting rules. Now you get linting errors when there is something not right.
4. Specify commit hooks to run on every commit events. Now only clean code will be commited.

1. You need to install the linting plugins first using yarn or npm as dev dependencies

`yarn add yarn add eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react --dev`

or 

`npm i -D eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react`

Now prettier for code formatting 

`yarn add prettier eslint-config-prettier eslint-plugin-prettier --dev`

Husky for some commit hooks 

`npm i -D husky lint-staged pretty-quick`

2. To customize the rules for your app create `.eslintrc` and `.prettierrc`.

A sample `.eslintrc`

`{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "plugins": [
    "react",
    "react-hooks",
    "@typescript-eslint",
    "prettier",
    "import"
  ],
  "env": {
    "browser": true,
    "jasmine": true,
    "jest": true,
    "node": true,
    "es6": true
  },
  "rules": {
    "prettier/prettier": [
      "error",
      {
        "singleQuote": true
      }
    ],
    "react-hooks/rules-of-hooks": "error",
    "react-hooks/exhaustive-deps": "warn",
    "@typescript-eslint/no-unused-vars": [
      "off",
      {
        "argsIgnorePattern": "^_"
      }
    ],
    "import/first": "error",
    "import/order": [
      "warn",
      {
        "groups": [
          ["builtin", "external"],
          "internal",
          ["parent", "sibling", "index"]
        ],
        "newlines-between": "ignore"
      }
    ]
  },
  "settings": {
    "react": {
      "pragma": "React",
      "version": "detect"
    }
  },
  "parser": "@typescript-eslint/parser"
}
`
A sample `.eslintrc`

`{
  "printWidth": 120,
  "trailingComma": "all",
  "singleQuote": true
}
`

3. Now you have install the linting plugins. We can install ESlint and Prettier on VSCode for example.

4. Now write some pre-commit hooks so all staged changes are checked for linting

`"precommit": "lint-staged"`.

If you want to fine tune it furthur, you can do it by specifying the script.

Note: You can turn on format on type, format on save options in VSCode by changing the settings. See them by filtering the 
settings after opening it by `cmd + ,`
