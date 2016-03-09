#Get all computed font-sizes of the current web-page you are looking at.

Just use this small bookmarklet or adopt the code for your own purposes.

```
javascript:(function(){

    var aComputedFontSizes = [];
    var aFontSizeList = [];
    var aElements = document.querySelectorAll('*'), nIterator;

    var buildTable = function() {

    };

    for (nIterator = 0; nIterator < aElements.length; ++nIterator) {
        var sFontSize = window.getComputedStyle(aElements[nIterator], null).getPropertyValue('font-size');
        var nIndex = aFontSizeList.indexOf(sFontSize);
        if (nIndex == -1) {
            aFontSizeList.push(sFontSize);
            aComputedFontSizes.push([sFontSize, 1]);
        } else {
            aComputedFontSizes[nIndex] = [sFontSize, aComputedFontSizes[nIndex][1] + 1];
        }
    }

    if (console.table) {
        console.log('All computed FontSizes on each and every DOM-ELement:');
        console.table(aComputedFontSizes);
    } else {
        console.log('All computed FontSizes on each and every DOM-ELement: ', aComputedFontSizes);
    }

}());
```

Want to save it right away as bookmarklet. Save this link: <a href="javascript:!function(){var e,o=[],l=[],n=document.querySelectorAll("*");for(e=0;e<n.length;++e){var t=window.getComputedStyle(n[e],null).getPropertyValue("font-size"),c=l.indexOf(t);-1==c?(l.push(t),o.push([t,1])):o[c]=[t,o[c][1]+1]}console.table?(console.log("All computed FontSizes on each and every DOM-ELement:"),console.table(o)):console.log("All computed FontSizes on each and every DOM-ELement: ",o)}();">allComputedFontSizes</a>