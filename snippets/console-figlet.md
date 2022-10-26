```js
const figlet = `
%c _____ _       _      _   
%c|  ___(_) __ _| | ___| |_ 
%c| |_  | |/ _` | |/ _ \ __|
%c|  _| | | (_| | |  __/ |_ 
%c|_|   |_|\__, |_|\___|\__|
%c         |___/
`

const HUE_STEP = -10
const HUE_OFFSET = 100

const styles = new Array(9)
.fill(0)
.map((_,i) => `color: hsl(${(i * HUE_STEP) + HUE_OFFSET}deg, 100%, 70%);`)

console.info(figlet, ...styles)
```