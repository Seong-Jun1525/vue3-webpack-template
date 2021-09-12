# Vue.js

## Vue3 Webpack Template
```terminal
npx degit https://github.com/Seong-Jun1525/Part8-Webpack.git 폴더이름
```
- 폴더로 이동 후
```terminal
code . -r
```
- 최신의 vue 설치 (개발할 때만 사용하는 것이 아니고 실제로 브라우저에서 동작할 때 사용하는 것이니 개발의존성(-D)으로 설치하면 x)
```terminal
npm i vue@next
```
- 기본적인 vue의 문법 해석 용도로 사용.
- vue 파일을 관리하려면 추가로 다른 패키지도 설치해야함.
```terminal
npm i -D vue-loader@next vue-style-loader @vue/compiler-sfc
```

- webpack.config.js에 다음을 추가
```js
const { VueLoaderPlugin } = require('vue-loader')

module: {
    rules: [
                {
                    test: /\.vue$/,
                    use: ['vue-loader'] 
                },
                {
                test: /\.s?css$/,
                    use: [
                        // 순서 중요
                        'vue-style-loader', // 가장 마지막에 해석
                        'style-loader', // 해석된 로더가 실제로 어디선가 사용되어야 하는데 그때 style-loader가 html부분에 style tag부분에 해석된 내용을 삽입시켜줌. 
                        'css-loader', // 먼저 해석되는 loader. js파일에서 css파일을 해석하는 용도로 사용.
                        'postcss-loader',
                        'sass-loader'
                    ]
                },
                ...
    ]
    plugins: [
        ...,
        new VueLoaderPlugin()
    ]
}
```