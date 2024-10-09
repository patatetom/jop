<img alt="LessPass" src="LessPassword.png" width="210px"/>

🔑 **In browser password generator** inspired by _« [lesspass](https://github.com/lesspass/lesspass), a stateless password manager »_.

LessPass is an extremely simple offline solution based on a small HTML-CSS-JS file played in a recent web browser for the user interface and password génération.


# Why LessPass ?

Managing a multitude of unique, long and complex passwords has never been easy, even with an internal or external password manager, especially when switching from one browser to another, from one computer to another and from one smartphone to another !

> As an astronaut friend of mine used to say : _“Don't wait for this kind of mishap to happen before getting into LessPass”_.


# How is the password generated ?

The service and the secret provided are combined and mixed using the PBKDF2 cryptographic function to produce a very large number.
This number is then used to select characters from a set set of 26 lower-case letters of the Latin alphabet (`abcdefghijklmnopqrstuvwxyz`), the 26 uppercase letters of the Latin alphabet (`ABCDEFGHIJKLMNOPQRSTUVWXYZ`), the 10 Arabic-Indian numerals (`0123456789`) and 25 special characters (`(.,;:!?)[=+-*/&|]{#$%@_~}`).


# Installation

## Computer

- Download `LessPass.html` HTML file to your computer
- Check the code
- Create a desktop shortcut that opens your favorite browser to the HTML file (the URL will look like `file:///home/me/path/to/LessPass.html`)

<img alt="Chromium" src="computer.chromium.png" width="310px"/><br/><img alt="Firefox" src="computer.firefox.png" width="310px"/>


## Smartphone

### Android

> _Direct use of the `file` schema (eg. `file:///sdcard/path/to/LessPass.html`) in the URL is made difficult by Android : it is therefore simpler to install a small web server._

- Install [Simple HTTP Server](https://play.google.com/store/apps/details?id=com.phlox.simpleserver)
- Set an empty folder as the `Root folder`
- Restrict network interfaces to `lo` (eg. `127.0.0.1`)
- Set `Autostart at boot`
- Download `LessPass.html` HTML file to the empty folder defined as `Root folder`
- Check the code
- Create a desktop shortcut that opens your favorite browser to the HTML file with `http://localhost:8080/LessPass.html` URL

<img alt="Android" src="android.simpleHTTPserver.png" height="390px"/> <img alt="Android" src="android.firefox.png" height="390px"/>

### iOS

> _TODO..._<br/>
> _no iOS system yet : help would be appreciated._


## Translation

- Open the HTML file with your favorite code editor
- In the `language` section of the `script` section, copy/paste or rename the existing `fr(){…}` function
- Rename the new function with the two letters of the desired language
- Translate the few `"character strings"` present in the new function
- Save changes
- Reload the HTML file from your favorite browser

```js
// language (use fr template to create a new language) ------------------------
// french
function fr() {
	document.documentElement.lang = "fr";
	document.head.querySelector('meta[name="description"]').content = "Générateur de mot de passe";
	…}
// deutsch
function de() {
	document.documentElement.lang = "de";
	document.head.querySelector('meta[name="description"]').content = "Passwortgenerator";
	…}
```

> _Your translation is welcome ;-)_
