# double_css_finder

Finds obsolete CSS rules on the current page.

Copy and paste the following into the console and execute it:

```
function main() {
    let sheets = [...document.styleSheets];
    for (let sheet of sheets) {
        console.log(sheet.ownerNode);
        for (let rule of sheet.rules) {
          addRule(rule);
        }
    }
}

function addRule(rule) {
    let selector = rule.selectorText;
    if (!selector) return; // @font-face
    for (let key of rule.style) {
        value = rule.style[key];
        entry = selector + ' {' + key +": " + value + '}';
            if (found.includes(entry)) {
                console.log("Double entry: " + entry)
            } else {
                found.push(entry);
            }
        }
}

var found = [];
main();
```
