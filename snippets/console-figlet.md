This snippets prints a pretty ASCII text with gradient colors to the console which can be viewed in the developer tools of your browser. It's a great way for some bonus information or an easter egg. [Generate a font style here](https://www.askapache.com/online-tools/figlet-ascii/).

> _**NOTE:**  Depending on what text is generated you might need to escape certain character using the `\`. You should also edit the lines in the array according to how many lines you use for the text snippet._

## Snippet

```js
const figlet = `
%c _____ _       _      _   
%c|  ___(_) __ _| | ___| |_ 
%c| |_  | |/ _\\ | |/ _ \\ __|
%c|  _| | | (_| | |  __/ |_ 
%c|_|   |_|\\__, |_|\___|\\__|
%c         |___/
`

const HUE_STEP = -10
const HUE_OFFSET = 100

const styles = new Array(6)
	.fill(0)
	.map((_,i) => `color: hsl(${(i * HUE_STEP) + HUE_OFFSET}deg, 100%, 70%);`)

console.info(figlet, ...styles)
```

## Personal Figlet

```js
const figlet = `
%c __  __            _    _____         _                          
%c|  \\/  | __ _ _ __| | _|_   _|__  ___| | ___ __ ___   __ _ _ __  
%c| |\\/| |/ _\\ | '__| |/ / | |/ _ \\/ _ \\ |/ / '_ \\ _ \\ / _\\ | '_ \\ 
%c| |  | | (_| | |  |   <  | |  __/  __/   <| | | | | | \(_| | | | |
%c|_|  |_|\\__,_|_|  |_|\\_\\ |_|\\___|\\___|_|\\_\\_| |_| |_|\\__,_|_| |_|
%c
`

const HUE_STEP = -30
const HUE_OFFSET = 10

const styles = new Array(6)
	.fill(0)
	.map((_,i) => `color: hsl(${(i * HUE_STEP) + HUE_OFFSET}deg, 100%, 70%);`)

console.info(figlet, ...styles)
console.info("%cHey there explorer! Why not checkout my GitHub profile while you're here 🚀 https://github.com/markteekman/",`color: hsl(${(5 * HUE_STEP) + HUE_OFFSET}deg, 100%, 70%); font-size: 14px`);
```