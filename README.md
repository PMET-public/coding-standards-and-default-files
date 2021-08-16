# Guidelines for our repos
Below are some guidelines, default files/templates, recommended tools, etc. for our team projects.
It's meant to help jumpstart repos with modern dev practices.

Keep in mind:

- These tips/notes are **not** exhaustive. They're designed to jump to revelant sections, pull out what you need, and go code.

- These tips/notes are *suggestions*. Use your best judgement but be prepared to explain when you stray from them.

- Please contribute per your expertise. Be brief and link samples when possible. Focus on the "what" here then refer to online resources/docs for the "why".

- Remember you're developing for a team, and teammates need to be able to use & develop your code, too. Using these guidelines consistently will improve our projects for everyone.

# Common files for all projects

`.gitignore`
```
.DS_Store

# node projects
node_modules

# php projects
vendor
auth.json
```

`README.md`
```markdown
# Title of project
Description of the project, what it does, and why its useful/needed.

# Installation and execution
Steps for the end user to install and run the main program. List prerequisites and any assumptions.

# Developer Setup
How developers can quickly setup their dev environment, setup debugging, run tests, etc.
```

`.vscode/launch.json` - configuration needed for debugging in VSC
- php: [sample](https://github.dev/PMET-public/magento-cloud/blob/pmet-2.4.3-ref/.vscode/launch.json)
- node: [sample](https://github.dev/PMET-public/magento-cloud-manager/blob/master/.vscode/launch.json)
- python: [sample](https://github.dev/marketolive/verticals/blob/master/.vscode/launch.json)
- bash: [sample](https://github.dev/PMET-public/mdm/blob/develop/.vscode/launch.json)

`Dockerfile` - a platform independent way to demo the minimum dependencies for your project ([python ex.](https://github.com/marketolive/verticals/blob/master/Dockerfile), [node ex.](https://github.com/PMET-public/storystore-pwa/blob/master/Dockerfile))

`docker-compose.yml` - the necessary services and conf to run the project typically with a single cmd ([python ex.](https://github.com/marketolive/verticals/blob/master/docker-compose.yml), [node x.](https://github.com/PMET-public/storystore-pwa/blob/master/docker-compose.test.yml))

`.github/workflows/test-workflow.yml` - a Github CI/CD configuration to prove operability and ensure code quality ([ex. #1](https://github.com/PMET-public/action-tmate/blob/master/.github/workflows/ci-test.yml), [ex. #2](https://github.com/PMET-public/storystore-pwa/blob/master/.github/workflows/docker-publish.yml))

# Tools For All Projects

## Why Visual Studio Code (VSC) as the team's preferred IDE?
* vast language support - supports all your and your teams projects with 1 tool
* extensive plugin ecosystem
* amazing Github integration
* completely free
* [becoming the de facto standard among devs](https://insights.stackoverflow.com/survey/2021#section-most-popular-technologies-integrated-development-environment)


## Recommended VSC extensions for any project
- [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)
- [Git Tree Compare](https://marketplace.visualstudio.com/items?itemName=letmaik.git-tree-compare)
- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [indent-rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)
- [Bracket Pair Colorizer 2](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2)
- [Rainbow CSV](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv)
- [Edit csv](https://marketplace.visualstudio.com/items?itemName=janisdd.vscode-edit-csv)

# Node & JS projects

## Recommended VSC extensions

- [Eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
## [prettier](https://prettier.io/docs/en/) for formatting

Install:

`npm install --save-dev prettier`

Derfault config:

`.prettierrc.json`
```json
{
  "printWidth": 140,
  "parser": "flow",
  "semi": false,
  "bracketSpacing": false,
  "arrowParens":  "avoid",
  "singleQuote": true,
  "trailingComma": "none",
  "jsxBracketSameLine": true,
  "useTabs": false,
  "overrides": [],
  "tabWidth": 2
}
```

Run in terminal:

`./node_modules/prettier/bin-prettier.js --config .prettierrc.json --write .`

Run via `scripts` attribute of `package.json`:
```json
  "scripts": {
    "prettier": "./node_modules/prettier/bin-prettier.js --config .prettierrc.json --write ."
  }
```

`npm run prettier`

## 2. [eslint](https://eslint.org/docs/user-guide/getting-started) for linting

Install:

`npm install --save-dev eslint`

`.eslintrc.json`
```json
{
  "env": {
    "browser": true,
    "es6": true,
    "node": true
  },
  "parser": "babel-eslint",
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended"
  ],
  "parserOptions": {
    "sourceType": "module",
    "ecmaFeatures": {
      "experimentalObjectRestSpread": true,
      "jsx": true
    }
  },
  "plugins": [
    "react"
  ],
  "rules": {
    "react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
    "indent": [
      "error",
      2,
      {"SwitchCase": 1,
      "MemberExpression": "off"}
    ],
    "linebreak-style": [
      "error",
      "unix"
    ],
    "quotes": [
      "error",
      "single"
    ],
    "no-unused-vars": [
      "warn",
      {
        "args": "none",
        "ignoreRestSiblings": true,
        "varsIgnorePattern": "[Ii]gnoreMe"
      }
    ],
    "no-var": "error",
    "no-console": "off",
    "prefer-destructuring": ["error", {
      "array": true,
      "object": true
    }, {
      "enforceForRenamedProperties": false
    }]
  }
}
```

Run in the terminal:
`eslint . --ext .js,.jsx`

Run via `scripts` attribute of `package.json`:
```json
  "scripts": {
    "eslint": "./node_modules/prettier/bin-prettier.js --config .prettierrc.json --write ."
  }
```

`npm run eslint`

# PHP Projects
## Recommended VSC extensions
# Bash projects
## Recommended VSC extensions

- [Bash IDE](https://marketplace.visualstudio.com/items?itemName=mads-hartmann.bash-ide-vscode)
- [Bash Debug](https://marketplace.visualstudio.com/items?itemName=rogalmic.bash-debug)
- [Bats](https://marketplace.visualstudio.com/items?itemName=jetmartin.bats)
- [shell-format](https://marketplace.visualstudio.com/items?itemName=foxundermoon.shell-format)

# Python Projects
## Recommended VSC extensions
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
