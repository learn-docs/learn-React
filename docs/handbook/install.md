> 点击勘误[issues](https://github.com/webVueBlog/learn-React/issues)，哪吒感谢大家的阅读

## React 安装

引入了三个库： react.development.min.js 、react-dom.development.min.js 和 babel.min.js：

- react.min.js - React 的核心库
- react-dom.min.js - 提供与 DOM 相关的功能
- babel.min.js - Babel 可以将 ES6 代码转为 ES5 代码，这样我们就能在目前不支持 ES6 浏览器上执行 React 代码。Babel 内嵌了对 JSX 的支持。通过将 Babel 和 babel-sublime 包（package）一同使用可以让源码的语法渲染上升到一个全新的水平。

:::tip
注意: 在浏览器中使用 Babel 来编译 JSX 效率是非常低的。
:::

```js
ReactDOM.render(
    <h1>Hello, world!</h1>,
    document.getElementById('example')
);
```

以上代码将一个 h1 标题，插入 `id="example"` 节点中。

注意：

如果我们需要使用 `JSX`，则 `<script>` 标签的 `type` 属性需要设置为 `text/babel`。

淘宝定制的 cnpm (gzip 压缩支持) 命令行工具代替默认的 npm:

```js
$ npm install -g cnpm --registry=https://registry.npmmirror.com
$ npm config set registry https://registry.npmmirror.com
```

这样就可以使用 `cnpm` 命令来安装模块了：

```js
$ cnpm install [name]
```

## 使用 create-react-app 快速构建 React 开发环境

`create-react-app` 自动创建的项目是基于 `Webpack + ES6` 。

执行以下命令创建项目：

```js
$ cnpm install -g create-react-app
$ create-react-app my-app
$ cd my-app/
$ npm start
```

项目的目录结构如下：

```js
my-app/
  README.md
  node_modules/
  package.json
  .gitignore
  public/
    favicon.ico
    index.html
    manifest.json
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

manifest.json 指定了开始页面 index.html，一切的开始都从这里开始，所以这个是代码执行的源头。

尝试修改 src/App.js 文件代码：

```js
src/App.js

import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
 
class App extends Component {
  render() {
    return (
      <div className="App">
        <div className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h2>欢迎</h2>
        </div>
        <p className="App-intro">
          你可以在 <code>src/App.js</code> 文件中修改。
        </p>
      </div>
    );
  }
}
 
export default App;
```

`src/index.js` 是一个入口文件，我们可以尝试直接修改 `src/index.js` 文件代码：

实例

```js
import React from 'react';
import ReactDOM from 'react-dom';

function Hello(props) {
  return <h1>Hello World!</h1>;
}

ReactDOM.render(<Hello />, document.getElementById('root'));
```

使用了 `npmjs.org`，解决方法是换成淘宝的资源：

```js
$ npm config set registry https://registry.npm.taobao.org
-- 配置后可通过下面方式来验证是否成功
$ npm config get registry
-- 或 npm info express
```

`ReactDOM.render(...)` 是渲染方法，所有的 js,html 都可通过它进行渲染绘制

内容就是要在渲染目标中显示的东西，可以是一个 React 部件，也可以是一段HTML或TEXT文本。渲染目标JS对象，就是一个DIV或TABEL,或TD 等HTML的节点对象。

```js
ReactDOM.render(<App />, div);
```

`unmountComponentAtNode()` 这个方法是解除渲染挂载，作用和 render 刚好相反，也就清空一个渲染目标中的 React 部件或 html 内容。

```js
ReactDOM.unmountComponentAtNode(div);
```
