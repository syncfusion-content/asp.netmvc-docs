---
layout: post
title: Keyboard-interaction
description: keyboard interaction
platform: ejmvc
control: Rotator
documentation: ug
---

## Keyboard interaction

The AllowKeyboardNavigation property turns on keyboardinteraction with the Rotator items. You must set this property to ‘true’ to access the keyboard shortcuts. The default value is ‘true’. The value set to this property is Boolean.

The entire Rotator commands are accessed through the keyboard by specifying the KeyboardShortcut in the following table.

<table>
<tr>
<td>
Keyboard Shortcut</td><td>
Function</td></tr>
<tr>
<td>
Alt + j</td><td>
Focuses the control</td></tr>
<tr>
<td>
Up/ Right</td><td>
Move to next slide</td></tr>
<tr>
<td>
Down/Left</td><td>
Move to previous slide.</td></tr>
<tr>
<td>
Space</td><td>
Move to Play/Pause slide.</td></tr>
<tr>
<td>
Alt + Right</td><td>
Move thumbnail item to right and select item.</td></tr>
<tr>
<td>
Alt + Left</td><td>
Move thumbnail item to left and select item.</td></tr>
<tr>
<td>
Enter</td><td>
Selected the thumbnail item</td></tr>
</table>


You can refer the following code example for keyboard navigation.



<table>
<tr>
<td>
[CSHTML]/ / Add this code in your CSHTML page and refer local data section for binding Rotator items.&lt;ul id="slide" style="display: none"&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/green.jpg")" title="Green" /&gt;&lt;/li&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/snow.jpg")" title="Snow" /&gt;&lt;/li&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/wheat.jpg")" title="Wheat" /&gt;&lt;/li&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/tablet.jpg")" title="Tablet" /&gt;&lt;/li&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/sea.jpg")" title="Sea" /&gt;&lt;/li&gt;    &lt;li&gt;        &lt;img src="@Url.Content("~/Images/rotator/bread.jpg")" title="Bread" /&gt;&lt;/li&gt;&lt;/ul&gt;@Html.EJ().Rotator("slidercontent").Items(itemElement =>                       {                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/green.jpg")" /&gt;                           &lt;/div&gt;);                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/snow.jpg")"/&gt;                           &lt;/div&gt;);                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/wheat.jpg")" /&gt;                           &lt;/div&gt;);                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/tablet.jpg")" /&gt;                           &lt;/div&gt;);                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/sea.jpg")" /&gt;                           &lt;/div&gt;);                           itemElement.Add().ContentTemplate(@&lt;div&gt;                               &lt;img class="image" src="@Url.Content("~/Images/rotator/bread.jpg")" /&gt;                           &lt;/div&gt;);                       }).SlideWidth("600px").SlideHeight("350px").ShowThumbnail(true).ThumbnailSourceID("slide").AllowKeyboardNavigation(true).ShowPlayButton(true)          </td></tr>
<tr>
<td>
[JS]&lt;script type="text/JavaScript"&gt;    $(function () {        //Control focus key        $(document).on("keydown", function (e) {            if (e.altKey && e.keyCode === 74) { // j- key code.                $("#slidercontent")[0].focus();            }        });    });&lt;/script&gt;</td></tr>
</table>


Run the above sample, we get the output like this,





{ ![](Keyboard-interaction_images/Keyboard-interaction_img1.png) | markdownify }
{:.image }










