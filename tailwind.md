## tailwind is a postcss plugin

let's walk through setting up tailwind in a completely vanilla plain empty HTML project so you can see just how simple it really is

---

### Setting up the Environment

create a basic empty package.json file

```sh
npm init -y
```
```sh
npm i tailwindcss postcss-cli autoprefixer
```

---

`postcss-cli`: incredibly lightweight way to introduce post CSS into your project.

`tailwind` doesn't include any vendor prefixes like - WebKit or - MS in any of the CSS it generates so let's also install `autoprefixer` which is a post CSS plugin for automatically vendor prefixes to your CSS 

---

### Create Config Files

- create a `tailwind.config.js` file

(where you would go if you ever wanted to customize tailwind in any way for your project)

```sh
npx tailwind init
```
<br>

- create `postcss.config.js` file

here we specify which css plugins we want to use

```javascript
module.exports = {
	plugins: [
		require("autoprefixer")
		require("tailwindcss")
	]

}
```

---

### create a css file

in `tailwind.css`

```css
@tailwind base;
@tailwind components;
@tailwind utility;
```

the way tailwind  works is by looking through your CSS for these sort of custom markers and replacing them with tailwind generated code 


with the `@tailwind base` directive we compile our CSS through post CSS.
tailwind is going to find this `@tailwind base` marker and replace it with all of tailwind's generated base


simple script that process css tough our list of post CSS plugins



in  `package.json`

```json
{
	...

	"scripts": {
		"css-build" : "postcss css/tailwind.css -o public/puild/tailwind.css"
	}
}
```

---

postcss refers to `postcss-cli` tool we installed before

if we run npm run build in our terminal this should generate a new CSS file for us that's been processed through post CSS

```sh
npm run css-build
```

---

### Linking to HTML

```HTML
<link rel="stylesheet" href="/build/tailwind.css">
```
```sh
npm i /g live-server
```