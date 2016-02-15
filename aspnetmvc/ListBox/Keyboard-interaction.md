---
layout: post
title: Keyboard interaction | ListBox | ASP.NET MVC | Syncfusion
description: keyboard interaction
platform: ejmvc
control: ListBox
documentation: ug
---

# Keyboard interaction

You can use Keyboard shortcut keys as an alternative for mouse actions to interact with the ListBox widget. Please refer the below table for details about short cut keys and its corresponding usage.

<table>
<tr>
<td>
<b>Shortcut Key</b></td><td>
<b>Usage</b></td></tr>
<tr>
<td>
<kbd>Enter</kbd></td><td>
Selects the focused item</td></tr>
<tr>
<td>
<kbd>Up</kbd></td><td>
Moves to previous item</td></tr>
<tr>
<td>
<kbd>Down</kbd></td><td>
Moves to next item</td></tr>
<tr>
<td>
<kbd>Left</kbd></td><td>
Moves to previous item</td></tr>
<tr>
<td>
<kbd>Right</kbd></td><td>
Moves to next item</td></tr>
<tr>
<td>
<kbd>Home</kbd></td><td>
Moves to first item</td></tr>
<tr>
<td>
<kbd>End</kbd></td><td>
Moves to last item</td></tr>
</table>

N> Initial focus can be done by pressing tab key multiple times until it is focused.

## Incremental Search

The [Incremental search](https://en.wikipedia.org/wiki/Incremental_search) helps in finding the specific item in the ListBox,as the user types the text one or more possible matches for the text are found and the first matched item will be selected.It can be enabled in the ListBox widget using “EnableIncrementalSearch” property. The search can be case sensitive or case insensitive.

{% highlight razor %}

@{Html.EJ().ListBox("listbox")
      .TargetID("listdata")
      .EnableIncrementalSearch(true)
      .CaseSensitiveSearch(true)
      .Render();}

<ul id="listdata">
    <li>Audi A4</li>
    <li>Audi A5</li>
    <li>Audi A6</li>
    <li>Audi A7</li>
    <li>Audi A8</li>
    <li>BMW 501</li>
    <li>BMW 502</li>
    <li>BMW 503</li>
    <li>Batch</li>
    <li>BMW 507</li>
    <li>BMW 3200</li>
    <li>Cut</li>
    <li>Copy</li>
    <li>Paste</li>
    <li>Add</li>
    <li>Delete</li>
    <li>D5ishCover</li>
    <li>Di5shCover</li>
    <li>Dis5hCover</li>
    <li>Dish5Cover</li>
    <li>DishC5over</li>
    <li>DishCo5ver</li>
    <li>DishCov5er</li>
    <li>DishCove5r</li>
    <li>Comments</li>
    <li>Links</li>
    <li>Clear Formatting</li>
</ul>


{% endhighlight %}



![](Keyboard-interaction_images\Keyboard-interaction_img1.png)

Press <kbd> tab </kbd> key to get ListBox focus and press <kbd>“A”</kbd> (enable caps lock or press <kbd>shift</kbd> +<kbd> “A”</kbd> since case sensitive search is enabled) to get the below output.

![](Keyboard-interaction_images\Keyboard-interaction_img1.png)