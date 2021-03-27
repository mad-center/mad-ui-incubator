# document
> Goal
- [x] Vue 3
- [x] TypeScript 4
- [x] Babel 7
- [x] Webpack 5
- [x] Hot Module Replacement
- [x] Lerna
- [ ] @types d.ts support
- [ ] ESLint
- [ ] Husky
- [ ] Lint-staged
- [ ] Commitizen + conventional log
- [ ] commitlint to check commit message syntax  
- [ ] Jest
- [ ] vuad for vue component auto document generation for API.
- [ ] semantic-release/ standard version

## dependencies
- webpack
```bash
yarn add -D webpack webpack-cli webpack-dev-server html-webpack-plugin
```
> clean-webpack-plugin or rimraf to remove dist folder

- vue
```bash
yarn add -D vue-loader@next vue@next @vue/compiler-sfc @vue/component-compiler-utils
```

- css/sass
```bash
yarn add -D style-loader css-loader postcss-loader postcss postcss-preset-env sass-loader sass
```
> mini-css-extract-plugin to replace style-loader

- babel
```bash
yarn add -D babel-loader @babel/cli @babel/core @babel/plugin-transform-runtime @babel/preset-env @babel/preset-typescript
```
> deprecate ts-loader: use babel7 @babel/preset-typescript to replace ts-loader

- auto generate template
```bash
yarn add -D yargs chalk ts-node
```

- typescript aupport
```bash
yarn add -D typescript
```

## sass module
`./typography/exports.scss`
```
@import './variables.scss';

:export {
    fontHeading: #{$font-heading};
}
```
> #{} 表示字符串插值
```
@use "./typography/exports.scss" as typography;

//font-family: typography.$font-heading;
```

## playground dependencies
```
"dependencies": {
  "@mad-ui/base": "file:../packages/base"
},
```

## button demo component principle
- use vue 3.0 composition API setup()/ref to define reactive data
- use css variant class to define variant style

## lerna packages management

- 给某个package安装依赖：yarn workspace packageB add packageA 将packageA作为packageB的依赖进行安装
- 给所有的package安装依赖: 使用yarn workspaces add lodash 给所有的package安装依赖
- 给root 安装依赖：使用yarn add -W -D typescript来给root安装依赖

## version bump

- 存在feat提交： 需要更新minor版本
- 存在fix提交： 需要更新patch版本
- 存在BREAKING CHANGE提交： 需要更新major版本

> lerna version --conventional-commits
> lerna version --conventional-commits --yes # auto

## release
```
lerna publish from-git
```