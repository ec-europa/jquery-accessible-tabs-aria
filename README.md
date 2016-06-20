# jQuery accessible tabs using ARIA
===========================

This fork serves bootstrap installs, by adding active class to the tab and to the tab-content.

This simple script transforms this simple list of anchors to contents:

```
<div class="js-tabs">
  <ul class="js-tablist">
   <li class="js-tablist__item">
    <a href="#id_first" id="label_id_first" class="js-tablist__link">1st tab</a>
   </li>
   <li class="js-tablist__item">
    <a href="#id_second" id="label_id_second" class="js-tablist__link">2nd tab</a>
   </li>
   <li class="js-tablist__item">
    <a href="#id_third" id="label_id_third" class="js-tablist__link">3rd tab</a>
   </li>
   <li class="js-tablist__item">
    <a href="#id_fourth" id="label_id_fourth" class="js-tablist__link">4th tab</a>
   </li>
  </ul>
 <div id="id_first" class="js-tabcontent">
   here the content of 1st tab
 </div>
 <div id="id_second" class="js-tabcontent">
   here the content of 2nd tab
 </div>
 <div id="id_third" class="js-tabcontent">
   here the content of 3rd tab
 </div>
 <div id="id_fourth" class="js-tabcontent">
   here the content of 4th tab
 </div>
</div>
```

into shiny accessible tabs by adding ARIA attributes. 

Keyboard navigation is supported, based on ARIA DP (http://www.w3.org/TR/2013/WD-wai-aria-practices-20130307/#tabpanel && http://www.oaa-accessibility.org/examplep/tabpanel1/):

__If you focus in the tabs "buttons"__
- use Up/Left to see previous tab, 
- use Down/Right to see next tab
- Use "Home" to see first tab (wherever you are in tab buttons)
- Use "End" to see last tab (wherever you are in tab buttons)

__If you focus in a tab content__
- use Ctrl Up/left to Set focus on the tab button for the currently displayed tab
- use Ctrl PageUp to Set focus on the previous tab button for the currently displayed tab
- use Ctrl PageDown to Set focus on the next tab button for the currently displayed tab
 
__Warning__: Ctrl+PageUp/PageDown combination could activate for some browsers a switch of browser tabs. Nothing to do for this, as far as I know (if you have a solution, let me know).

## Features

If there is a fragment in URL, the script detects if it is **on** or **in** a tab content, and select the tab automatically.

You can make a link to a tab (which opens it). ```<a href="#link-to-tab-content" class="js-link-to-tab">link to tab</a>```

Fragment is added to URL if you select a tab.

## Requirements

- jQuery (others smaller libraries should be ok, but didn't test for the moment)
- a small piece of CSS `` .js-tabcontent[aria-hidden=true] { display: none; } ``
- respect the classes given above, and the convention a href="#**id_fourth**" id="label&#95;**id_fourth**" (will improve later)
- Use attribute data-hx="hx" (ex data-hx="h2" if your tab system is after a h1) to specify Hx structure in your tabs if they don't have one in tab content (will be added, and can be hidden throught a class invisible) OR
- Indicate the hx structure contained in your tab contents, using the attribute data-existing-hx="h2"
 
This jQuery plugin __doesn't style tabs__ (except ``.js-tabcontent[aria-hidden=true]`` of course), styles can be added using other classes.

It can be included for one, two tab systems or more in a page.

Enjoy.
