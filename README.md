# Eslint Import Groups
An ESLint Rule for Improved Import Grouping


📏 ESLint is an excellent tool for managing code style and controlling code flow.



👗 Code styling has become an inseparable part of coding. Sorting imports can improve code appearance.



📢 In this ESlint config, I try to make import statements look better. So I divided imports into three groups, builtin (such as React), external and third-party libraries  (such as Mui), and internal libraries (such as local code).



At this config, I focus on clean separation by adding a new line between each group and adding extra config to ordering code by alphabetic order.



This is just an example configuration. Feel free to customize your own.


## Install import plugin

```shell
npm install eslint-plugin-import --save-dev

```

## ESlint config
The following code contains the original ESLint config that comes from a project created by Vite for React.

```javascript
module.exports = {
  root: true,
  env: { browser: true, es2020: true },
  extends: [
    "eslint:recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:react-hooks/recommended",
  ],
  ignorePatterns: ["dist", ".eslintrc.cjs"],
  parser: "@typescript-eslint/parser",
  plugins: ["react-refresh", "import"],
  rules: {
    "react-refresh/only-export-components": [
      "warn",
      { allowConstantExport: true },
    ],
    "import/order": [
      "error",
      {
        groups: ["builtin", "external", "internal"],
        pathGroups: [
          {
            pattern: "react",
            group: "external",
            position: "before",
          },
        ],
        pathGroupsExcludedImportTypes: ["react"],
        "newlines-between": "always",
        alphabetize: {
          order: "asc",
          caseInsensitive: true,
        },
      },
    ],
  },
};

```

