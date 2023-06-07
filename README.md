# double_css_finder

Finds obsolete CSS rules on the current page.

Just copy and paste the code into the console and execute it.

Alternatively, make it a bookmarklet here: https://www.gibney.org/bookmarklet_editor

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
