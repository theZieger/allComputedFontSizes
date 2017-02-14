#Get all computed font-sizes of the current web-page you are looking at.

Just use this small bookmarklet or adopt the code for your own purposes.

```
javascript:(function(){
    'use strict'

    var aComputedFontSizes = [],
        aFontSizeList = [];

    document.querySelectorAll('*').forEach(function(oElement) {
        var sFontSize = window.getComputedStyle(oElement, null).getPropertyValue('font-size'),
            nIndex = aFontSizeList.indexOf(sFontSize);

        if (nIndex == -1) {
            aFontSizeList.push(sFontSize);
            aComputedFontSizes.push([sFontSize, 1]);
        } else {
            aComputedFontSizes[nIndex] = [sFontSize, ++aComputedFontSizes[nIndex][1]];
        }
    });

    console.log('All computed FontSizes on each and every DOM-ELement:');
    console.table(aComputedFontSizes);

}());
```