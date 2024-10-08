<p><img alt="LessPass" src="LessPassword.png" width="210px"/></p>

🔑 **In browser password generator** inspired by _« [lesspass](https://github.com/lesspass/lesspass), a stateless password manager »_.

# Installation

## computer

- download `LessPass.html` HTML file to your computer
- check the code
- create a shortcut that opens your favorite browser to the HTML file (the URL will look like `file:///home/me/path/to/LessPass.html`)


## smartphone



## translation

- open the HTML file with your favorite code editor
- in the `language` section of the `script` section, copy and paste the existing `fr(){…}` function
- rename the new function with the two letters of the desired language
- translate the few character strings present in the new function
- save changes
- reload the HTML file from your favorite browser

```js
// french
function fr() {
	document.documentElement.lang = "fr";
	document.head.querySelector('meta[name="description"]').content = "Générateur de mot de passe";
	…}
// Deutsch
function de() {
	document.documentElement.lang = "de";
	document.head.querySelector('meta[name="description"]').content = "Passwortgenerator";
	…}
```

> _your translation is welcome ;-)_
