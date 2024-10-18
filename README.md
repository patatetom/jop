# JOP***_

**In browser password generator** inspired by _« [lesspass](https://github.com/lesspass/lesspass), a stateless password manager »_.

**JOP** - **J**ust **O**ne **P**assword - is an extremely simple offline solution based on a small HTML-CSS-JS file played in a recent web browser for the user interface and password génération.

_Managing a multitude of unique, long and complex passwords has never been easy, even with an internal or external password manager, especially when switching from one browser to another, from one computer to another and from one smartphone to another !_



## Password composition

The service and the secret provided are combined and mixed using the PBKDF2 cryptographic function to produce a very large number.
This number is then used to select characters from a set set of 26 lower-case letters of the Latin alphabet (`abcdefghijklmnopqrstuvwxyz`), the 26 upper-case letters of the Latin alphabet (`ABCDEFGHIJKLMNOPQRSTUVWXYZ`), the 10 Arabic-Indian numerals (`0123456789`) and 25 special characters (`(.,;:!?)[=+-*/&|]{#$%@_~}`).

> _Some services do not allow the use of special characters in password : the service prefix `-` prevents their use._



## Service, prefix and secret

### Service

Service (and its possible prefix) is one of the two pieces of information to be provided and therefore remembered.
The service must be at least 3 characters long.

> _For best recall, it's best to choose simple, easy-to-remember forms : `gmail` and `yahoo`, for example, for the respective e-mail services, `pseudo1@gmail` and `pseudo2@gmail` to distinguish two Gmail accounts, etc…_


### Prefix

The prefix, which is optional and precedes the service, is used to influence password generation.
It must be separated from the service by at least one space and have the following form `^((\+|-)?[1-9]? +)?` (eg. at the beginning, possibly a plus or a minus, possibly followed by a digit between 1 and 9, the whole necessarily followed by at least one space).

A few commented examples of prefixed services are sometimes better than a long speech :
- `myservice`, `+ myservice`, `1 myservice` and `+1 myservice` (eg. no prefix, `+`, `1` and `+1`) target the same service `myservice` and will generate for this last one a _first full password_
- `- myservice` and `-1 myservice` (eg. `-` and `-1`) target the same service `myservice` and will generate for this last one a _first downgraded password_ without special characters (for example, in case this one doesn't allow their use)
- `2 myservice` or `+2 myservice` (eg. `2` or `+2`) target the same service `myservice` and will generate for this last one a _second full password_ (for example, if the previous first full password had to be changed for security reasons)
- `-3 myservice` (eg. `-3`) target the service `myservice` and will generate for this last one a _third downgraded password_ without special characters

> _The prefix must be separated from the service to distinguish `2 myservice` (second full password for the service `myservice`) from `2myservice` (first full password for the service `2myservice`)._


### Secret

Secret is one of the two pieces of information to be provided and therefore retained.
No complexity is required for the secret, which must be at least 3 characters long.

> _However, it is preferable to use a robust secret._



## Installation

### Computer

- [Download](https://github.com/patatetom/jop/raw/refs/heads/main/jop.html) raw `jop.html` HTML file to your computer
- Check the code
- Create a desktop shortcut that opens your favorite browser to the HTML file (the URL will look like `file:///home/me/path/to/jop.html`)

<img alt="JOP on computer" src="jop.computer.png" width="310px"/>


### Smartphone / Tablet

> _Direct use of the `file` schema (eg. `file:///path/to/jop.html`) in the URL is made difficult on smartphone/tablet : it is therefore necessary to install a web server on the smartphone/tablet to use JOP in offline mode._
> <br/>
> _If you don't want to install a web server on your smartphone/tablet, you need to use an online version of JOP, either by hosting the HTML file yourself (prefered), or by using the [version provided by GitHub](https://patatetom.github.io/jop/jop.html)._


#### Android

- Install [Simple HTTP Server](https://play.google.com/store/apps/details?id=com.phlox.simpleserver)
- Set an empty folder as the `Root folder`
- Restrict network interfaces to `lo` (eg. `127.0.0.1`)
- Set `Autostart at boot`
- [Download](https://github.com/patatetom/jop/raw/refs/heads/main/jop.html) raw `jop.html` HTML file to the empty folder defined as `Root folder`
- Check the code
- Create a desktop shortcut that opens your favorite browser to the HTML file with `http://localhost:8080/jop.html` URL

<img alt="Simple HTTP Server on Android" src="simpleHTTPserver.android.png" height="390px"/> <img alt="JOP on Android" src="jop.android.png" height="390px"/>


#### iOS

> _TODO…_<br/>
>  &nbsp;- _see [WorldWideWeb](https://apps.apple.com/fr/app/worldwideweb-mobile/id1623006812)_<br/>
>  &nbsp;- _see [iSH/Python](https://beebom.com/run-simple-web-server-iphone/)_<br/>
> _no iOS system yet : help would be appreciated._



## Usage

### Password generation

Using JOP is relatively simple : enter the service (possibly prefixed), enter the secret, trigger password generation and then copy to the clipboard (for a later pasting) the generated password.

**It is important to note that the password copied to the clipboard is freely accessible.**

> For confidentiality, the informations entered are erased when the generated password is copied to the clipboard, the secret is hidden after 5 seconds of observation and the secret is automatically erased after 30 seconds of inactivity.


### Exporting, importing and cleaning services

Services memorized by the browser can be exported from the JOP interface using the dedicated icon : exporting involves copying a character string (eg. `?services=["myservice","-2 otherservice"]` for example) to the clipboard, which will then be used for an importation.

> _This character string can easily be edited (corrected, expanded, etc...) using a simple text editor (such as `notepad` for example) before being transmitted for import._

Services can be imported into JOP by adding to the URL used the string previously exported from another instance of JOP : services present there will be incorporated into the existing list of services memorized by the browser.

> _`file:///path/to/jop.html?services=["myservice","-2 otherservice"]` will import `myservice` and `-2 otherservice` services into the existing list._

Services memorized by the browser can be deleted by adding `?resetServices` to the URL used (e.g. `file:///path/to/jop.html?resetServices`) : confirmation will be requested before deletion.

> _The list of stored services can easily be « cleaned » by exporting the list, correcting the exportation, resetting the list and importing the corrected exportation._



## Translation

> _Your translation is welcome ;-)_

- Open the HTML file with your favorite code editor
- In the `language` section of the `script` section, copy/paste or rename the existing `fr(){…}` function
- Rename the new function with the two letters of the desired language
- Translate the few `"character strings"` present in the new function
- Save changes
- Reload the HTML file from your favorite browser

```js
// language -------------------------------------------------------------------
// (use fr function as template to create a new language)
function fr() { //french
	document.documentElement.lang = "fr";
	document.head.querySelector('meta[name="description"]').content = "Générateur de mot de passe";
	…}
function de() { // deutsch
	document.documentElement.lang = "de";
	document.head.querySelector('meta[name="description"]').content = "Passwortgenerator";
	…}
```
