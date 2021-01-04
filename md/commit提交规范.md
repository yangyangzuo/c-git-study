

# git commit 提交规范

为了保证提交代码的质量和格式统一，还有commit message的规范。在提交时会利用git hooks 中的 pre-commit 和 commit-msg 的钩子对提交的 代码和commit message进行检查，如果不符合统一规范，则禁止提交。

## 1. 代码的检查

​	利用pre-commit 钩子  则需安装插件

- ​      [husky](https://github.com/typicode/husky)    Git hooks made easy

- ​      [lint-staged](https://github.com/okonet/lint-staged)   Run linters on git staged files

- ​      [eslint](https://eslint.org/)    Find and fix problems in your JavaScript code

- ​      [prettier](https://prettier.io/)     An opinionated code formatter

  ```bash
  yarn add -D husky lint-staged  
  npm i -g eslint prettier 
  ```

  ```json
  //在package.json中添加如下配置
    "husky": {
      "hooks": {
        "pre-commit": [
          "lint-staged"
        ]
      }
    },
  ```

  在项目根目录  创建  .lintstagedrc.json

  ```json
  // lint-staged的配置文件
  {
      "*.(js|vue)": [
          "eslint --fix",
          "prettier -c -w"
      ],
      "*.(css|less|scss)": [
          "prettier -c -w"
      ]
  }
  ```

  创建.eslintrc.js 

  ```js
  //eslint的配置文件
  module.exports = {
  	env: {
  		browser: true,
  		node: true,
  		es2021: true,
  	},
  	extends: ['standard', 'eslint:recommended', 'plugin:vue/essential'],
  	parser: 'vue-eslint-parser',
  	parserOptions: {
  		parser: 'babel-eslint',
  		ecmaVersion: 2021,
  		sourceType: 'module',
  	},
  	plugins: ['vue'],
  	rules: {
  		indent: ['error', 'tab'],
  		'no-tabs': 'off',
  		'linebreak-style': ['error', 'unix'],
  		quotes: ['error', 'single'],
  		semi: ['error', 'always'],
  	},
  }
  
  ```

  创建.prettierrc.json

  ```json
  //prettier的配置文件
  {
      "trailingComma": "all",
      "tabWidth": 4,
      "semi": false,
      "singleQuote": true,
      "endOfLine": "lf"
  }
  ```

## 2. commit msg的规范 检测

- ​	[AngularJS Git Commit Message Conventions](https://docs.google.com/document/d/1QrDFcIiPjSLDn3EL15IJygNPiHORgU1_OOAqWjiDU5Y/edit#)
- ​    [如何规范commit](https://zhuanlan.zhihu.com/p/182553920?utm_source=org.mozilla.firefox)

​		利用commit -msg钩子  则需安装插件

- [commitlint](https://commitlint.js.org/)  

  ```bash
  yarn add -D @commitlint/config-conventional @commitlint/cli
  ```

  在package.json中添加如下代码

  ```json
  "husky": {
      "hooks": {
        "pre-commit": [
          "lint-staged"
        ],
        "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
      }
  },
  ```

  在项目根目录 创建  commitlint.config.js

  ```js
  module.exports = {
      extends: ['@commitlint/config-conventional'],
  }
  ```



## #附

####   [commitizen](http://commitizen.github.io/cz-cli/)  git commit 的代替者  可以自动帮你生产符合规范的commit msg 

```bash
npm i -g commitizen
#使用  
cz
```



