# 安装

> npm i lyb-project-config -D



# .eslintrc.cjs

```js
module.exports = {
  extends: [
    "lyb-project-config/eslint",
  ],
};
```

# tsconfig.json

```json
{
  "extends": "lyb-project-config/tsconfig",
  "compilerOptions": {
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["./src/**/*.ts", "./src/**/*.d.ts", "./test/*.ts", "test/index.ts"],
  "exclude": ["node_modules", "dist", "**/*.js"]
}
```

# .stylelintrc.cjs

```js
module.exports = {
  extends: ["lyb-project-config/stylelint"],
};
```

# postcss.config.cjs

```js
module.exports = {
  plugins: {
    autoprefixer: {
      overrideBrowserslist: ["iOS 7.1", "last 2 versions"]
    }
  }
};
```



# 插件推荐

```json
"devDependencies": {
  "@rushstack/eslint-patch": "^1.10.3",
  "@tsconfig/node18": "^18.2.4",
  "@types/nprogress": "^0.2.3",
  "@typescript-eslint/eslint-plugin": "^7.12.0",
  "@typescript-eslint/parser": "^7.12.0",
  "@vitejs/plugin-vue": "^5.0.4",
  "@vue/eslint-config-prettier": "^9.0.0",
  "@vue/eslint-config-typescript": "^13.0.0",
  "autoprefixer": "^10.4.23",
  "eslint-config-prettier": "^9.1.0",
  "eslint-plugin-import": "^2.29.1",
  "eslint-plugin-prettier": "^5.1.3",
  "eslint-plugin-vue": "^9.26.0",
  "eslint": "^8.56.0",
  "less-loader": "12.2.0",
  "less": "4.2.0",
  "lyb-project-config": "^1.1.2",
  "postcss-html": "^1.7.0",
  "postcss-less": "^6.0.0",
  "postcss": "^8.4.38",
  "prettier": "^3.3.2",
  "stylelint-config-recess-order": "^7.3.0",
  "stylelint-config-standard": "^39.0.0",
  "stylelint-order": "^7.0.0",
  "stylelint": "^16.24.0",
  "typescript": "^5.5.2",
  "unplugin-auto-import": "^19.3.0",
  "unplugin-element-plus": "^0.10.0",
  "unplugin-vue-components": "^28.8.0",
  "vite": "^5.3.2",
  "vue-tsc": "^2.0.22"
}
```

