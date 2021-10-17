<div align="center">

![download](https://user-images.githubusercontent.com/55017307/137621881-8ecde9c1-7a91-42e5-8429-ece4b5bcc81d.png)

</div>

---

### Post CSS is a tool for transforming styles with javascript plugins

when you build a website the css code you write is rarely the code that you actually want to ship to the browser. The developer wants to write code with modern features that maximize productivity, but end users want fast minified code that supports legacy browsers.

---

Post css is a build tool that makes everybody happy since it can take a css file and convert it to an abstract syntax tree then provides an api where plugins written in javascript can produce a different output

**for example:**

- with the `autoprefixer` plugin you'll never have to worry about writing vendor prefixes on your styles ever again

- with the `postcss-preset-env` plugin you can write modern css while postcss will automatically add the polyfills needed to support your targeted browsers

- with the `stylelint` tool you can detect issues before they break your ui

---

you probably already use postcss without even realizing it as it generates more npm downloads than `typescript` and `webpack` combined.

it's used under the hood by frameworks like `veed` and `nextjs` to provide a streamlined developer experience and it's also used by some of the world's most popular websites like `wikipedia` and `twitter` 

---
### Installation


```sh
npm install postcss autoprefixer postcss-nested
```

---

### PostCSS Config File

```sh
touch postcss.config.js
```

in `postcss.config.js`\:

```javascript
module.exports = {
	plugins: [
		require("postcss-nested")
		require("postcss-mixins")
		require("postcss-preset-env")
		require("postcss-reporter")
		require("stylelint")
		require("autoprefixer")
		require("cssnano")
	]

}
```
___

### Package  Config

```sh
npm init -y
```

in `package.json`:

```json
{
	...

	"scripts": {
		"build" : "postcss in.css -o out.css"
	}
}
```


