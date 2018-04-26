# Linting

Có thể bạn băn khoăn làm thế nào để lint code trong file `*.vue`,khi mà chúng không phải javaScript. Ta sẽ giả định rằng bạn đang dùng [ESLint](https://eslint.org/) (nếu bạn không dùng,bạn nên dùng!).

Đồng thời bạn cũng cần phiên bản chính thức của [eslint-plugin-vue](https://github.com/vuejs/eslint-plugin-vue) để hỗ trợ lint cho cả phần khung và script của file Vue.

Đảm bảo việc sử dụng các config của plugin trong phần config của ESLint :

``` json
{
  "extends": [
    "plugin:vue/essential"
  ]
}
```

Sau đó từ command line :

``` bash
eslint --ext js,vue MyComponent.vue
```

Một cách khác là sử dụng [eslint-loader](https://github.com/MoOx/eslint-loader) và file `*.vue` sẽ tự động lint khi bấm save trong quá trình phát triển.

``` bash
npm install eslint eslint-loader --save-dev
```

Chắc chắn nó được áp dụng như một pre-loader :

``` js
// webpack.config.js
module.exports = {
  // ... other options
  module: {
    rules: [
      {
        enforce: 'pre',
        test: /\.(js|vue)$/,
        loader: 'eslint-loader',
        exclude: /node_modules/
      }
    ]
  }
}
```
