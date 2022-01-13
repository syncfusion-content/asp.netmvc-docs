---
layout: post
title: Icons | Button | ASP.NET MVC | Syncfusion
description: Learn here all about Icons support in Syncfusion Essential Studio ASP.NET MVC Button Control, its elements, and more.
platform: ejmvc
control: Button
documentation: ug
---

# Icons in ASP.NET MVC Button

The Essential Studio for ASP.NET MVC provide icons library that contains the number of in-built icons that can be applied for CSS class names to elements and refer “ej.widgets.all.core.min.css” file. Use the following syntax to apply class names.

Syntax: .e-icon .e-[icon description]

.e-icon .e-search

## Adding icon in Button

For example, you can render the desired icon in the button by using the following table that contains the listed icons’ CSS class names in the “PrefixIcon” property of button component. Also, use “ContentType” property to display the icon in the button. In the following code example, specify the “ContentType” of the button as ImageOnly.    

Refer to the following link to know what are the values passed in the “ContentType” property

<http://help.syncfusion.com/aspnetmvc/button/icons>

Also in the button sample, you can use the icon class names as follows,

{% highlight CSHTML %}


@Html.EJ().Button("button").Size(ButtonSize.Small).ContentType(ContentType.ImageOnly).PrefixIcon("e-icon e-handup")



@Html.EJ().SplitButton("splitbutton").ContentType(ContentType.ImageOnly).PrefixIcon("e-icon e-calender")



@Html.EJ().ToggleButton("toggleButton").Size(ButtonSize.Small).ContentType(ContentType.ImageOnly).DefaultPrefixIcon("e-icon e-mediaplay").ActivePrefixIcon("e-icon e-mediapause")


{% endhighlight %}



Execute the above code to render the following output.

![ASPNETMVC Button Icons](Icons_images/Icons_img1.png)

 
## List of Icons

The complete list of icons is listed in the following table.

_List of icons_

<table>
<tr>
<td>
e-unpin</td><td>
{{'![ASPNETMVC Button unpinIcons](Icons_images/Icons_img2.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-pin</td><td>
{{'![ASPNETMVC Button pin Icons](Icons_images/Icons_img3.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-upload</td><td>
{{'![ASPNETMVC Button upload Icons](Icons_images/Icons_img4.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-reload</td><td>
{{'![ASPNETMVC Button reload Icons](Icons_images/Icons_img5.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-collapse</td><td>
{{'![ASPNETMVC Button collapse Icons](Icons_images/Icons_img6.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-cancel</td><td>
{{'![ASPNETMVC Button cancel Icons](Icons_images/Icons_img7.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-expand</td><td>
{{'![ASPNETMVC Button expand Icons](Icons_images/Icons_img8.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-minimize</td><td>
{{'![ASPNETMVC Button minimize Icons](Icons_images/Icons_img9.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-login</td><td>
{{'![ASPNETMVC Button login Icons](Icons_images/Icons_img10.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-orientationlanscape</td><td>
{{'![ASPNETMVC Button orientationlanscape Icons](Icons_images/Icons_img11.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignleft</td><td>
{{'![ASPNETMVC Button alignleft Icons](Icons_images/Icons_img12.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-aligncenter</td><td>
{{'![ASPNETMVC Button aligncenter Icons](Icons_images/Icons_img13.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignright</td><td>
{{'![ASPNETMVC Button alignright Icons](Icons_images/Icons_img14.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignjustify</td><td>
{{'![ASPNETMVC Button alignjustify Icons](Icons_images/Icons_img15.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignnone</td><td>
{{'![ASPNETMVC Button alignnone Icons](Icons_images/Icons_img16.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filterset</td><td>
{{'![ASPNETMVC Button filterset Icons](Icons_images/Icons_img17.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filternone</td><td>
{{'![ASPNETMVC Button filternone Icons](Icons_images/Icons_img18.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadup-2x</td><td>
{{'![ASPNETMVC Button arrowheadup Icons](Icons_images/Icons_img19.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheaddown-2x</td><td>
{{'![ASPNETMVC Button arrowheaddown Icons](Icons_images/Icons_img20.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadleft-2x</td><td>
{{'![ASPNETMVC Button arrowheadleft Icons](Icons_images/Icons_img21.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadright-2x</td><td>
{{'![ASPNETMVC Button arrowheadright Icons](Icons_images/Icons_img22.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-numbering</td><td>
{{'![ASPNETMVC Button numbering Icons](Icons_images/Icons_img23.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-bullets</td><td>
{{'![ASPNETMVC Button bullets Icons](Icons_images/Icons_img24.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-maximize</td><td>
{{'![ASPNETMVC Button maximize Icons](Icons_images/Icons_img25.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-delete</td><td>
{{'![ASPNETMVC Button delete Icons](Icons_images/Icons_img26.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-scroll</td><td>
{{'![ASPNETMVC Button scroll Icons](Icons_images/Icons_img27.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-right-scroll</td><td>
{{'![ASPNETMVC Button right Icons](Icons_images/Icons_img28.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-search</td><td>
{{'![ASPNETMVC Button search Icons](Icons_images/Icons_img29.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaback</td><td>
{{'![ASPNETMVC Button mediaback Icons](Icons_images/Icons_img30.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaforward</td><td>
{{'![ASPNETMVC Button mediaforward Icons](Icons_images/Icons_img31.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-medianext</td><td>
{{'![ASPNETMVC Button medianext Icons](Icons_images/Icons_img32.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaprev</td><td>
{{'![ASPNETMVC Button mediaprev Icons](Icons_images/Icons_img33.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaeject</td><td>
{{'![ASPNETMVC Button mediaeject Icons](Icons_images/Icons_img34.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaclose</td><td>
{{'![ASPNETMVC Button mediaclose Icons](Icons_images/Icons_img35.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediapause</td><td>
{{'![ASPNETMVC Button mediapause Icons](Icons_images/Icons_img36.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaplay</td><td>
{{'![ASPNETMVC Button mediaplay Icons](Icons_images/Icons_img37.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-righttick</td><td>
{{'![ASPNETMVC Button righttick Icons](Icons_images/Icons_img38.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-smile</td><td>
{{'![ASPNETMVC Button smile Icons](Icons_images/Icons_img39.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-information</td><td>
{{'![ASPNETMVC Button information Icons](Icons_images/Icons_img40.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-left-arrow</td><td>
{{'![ASPNETMVC Button left Icons](Icons_images/Icons_img41.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-right-arrow</td><td>
{{'![ASPNETMVC Button right Icons](Icons_images/Icons_img42.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-delete</td><td>
{{'![ASPNETMVC Button delete Icons](Icons_images/Icons_img43.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-success</td><td>
{{'![ASPNETMVC Button percentage Icons](Icons_images/Icons_img44.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-cancel</td><td>
{{'![ASPNETMVC Button file cancel Icons](Icons_images/Icons_img45.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-failed</td><td>
{{'![ASPNETMVC Button file percentage Icons](Icons_images/Icons_img46.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-retry</td><td>
{{'![ASPNETMVC Button file retry Icons](Icons_images/Icons_img47.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-resize-handle</td><td>
{{'![ASPNETMVC Button resize Icons](Icons_images/Icons_img48.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-down-arrow</td><td>
{{'![ASPNETMVC Button down arrow Icons](Icons_images/Icons_img49.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-time</td><td>
{{'![ASPNETMVC Button time Icons](Icons_images/Icons_img50.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-up-arrow</td><td>
{{'![ASPNETMVC Button up arrow Icons](Icons_images/Icons_img51.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-date</td><td>
{{'![ASPNETMVC Button date Icons](Icons_images/Icons_img52.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-datetime</td><td>
{{'![ASPNETMVC Button datetime Icons](Icons_images/Icons_img53.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-collapse-arrow</td><td>
{{'![ASPNETMVC Button collapse Icons](Icons_images/Icons_img54.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-expand-arrow</td><td>
{{'![ASPNETMVC Button expand Icons](Icons_images/Icons_img55.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-restore</td><td>
{{'![ASPNETMVC Button restore Icons](Icons_images/Icons_img56.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-plus</td><td>
{{'![ASPNETMVC Button plus Icons](Icons_images/Icons_img57.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-minus</td><td>
{{'![ASPNETMVC Button minus Icons](Icons_images/Icons_img58.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-handup</td><td>
{{'![ASPNETMVC Button handup Icons](Icons_images/Icons_img59.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clock</td><td>
{{'![ASPNETMVC Button clock Icons](Icons_images/Icons_img60.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cursor</td><td>
{{'![ASPNETMVC Button cursor Icons](Icons_images/Icons_img61.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlink</td><td>
{{'![ASPNETMVC Button hyperlink Icons](Icons_images/Icons_img62.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlinkbreak</td><td>
{{'![ASPNETMVC Button hyperlinkbreak Icons](Icons_images/Icons_img63.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-settings</td><td>
{{'![ASPNETMVC Button settings Icons](Icons_images/Icons_img64.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-shoppingcart</td><td>
{{'![ASPNETMVC Button shoppingcart Icons](Icons_images/Icons_img65.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-palette</td><td>
{{'![ASPNETMVC Button palette Icons](Icons_images/Icons_img66.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-warningmessage</td><td>
{{'![ASPNETMVC Button warningmessage Icons](Icons_images/Icons_img67.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cut</td><td>
{{'![ASPNETMVC Button cut Icons](Icons_images/Icons_img68.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-copy</td><td>
{{'![ASPNETMVC Button copy Icons](Icons_images/Icons_img69.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-paste</td><td>
{{'![ASPNETMVC Button paste Icons](Icons_images/Icons_img70.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-edit</td><td>
{{'![ASPNETMVC Button edit Icons](Icons_images/Icons_img71.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapleft</td><td>
{{'![ASPNETMVC Button swapleft Icons](Icons_images/Icons_img72.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapright</td><td>
{{'![ASPNETMVC Button swapright Icons](Icons_images/Icons_img73.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapup</td><td>
{{'![ASPNETMVC Button swapup Icons](Icons_images/Icons_img74.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapdown</td><td>
{{'![ASPNETMVC Button swapdown Icons](Icons_images/Icons_img75.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomin</td><td>
{{'![ASPNETMVC Button zoomin Icons](Icons_images/Icons_img76.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomout</td><td>
{{'![ASPNETMVC Button zoomout Icons](Icons_images/Icons_img77.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-star</td><td>
{{'![ASPNETMVC Button star Icons](Icons_images/Icons_img78.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-home</td><td>
{{'![ASPNETMVC Button home Icons](Icons_images/Icons_img79.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clipboard</td><td>
{{'![ASPNETMVC Button clipboard Icons](Icons_images/Icons_img80.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-userlogin</td><td>
{{'![ASPNETMVC Button userlogin Icons](Icons_images/Icons_img81.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-dataexport</td><td>
{{'![ASPNETMVC Button dataexport Icons](Icons_images/Icons_img82.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheadright</td><td>
{{'![ASPNETMVC Button arrowheadright Icons](Icons_images/Icons_img83.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheaddown</td><td>
{{'![ASPNETMVC Button arrowheaddown Icons](Icons_images/Icons_img84.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-undo</td><td>
{{'![ASPNETMVC Button undo Icons](Icons_images/Icons_img85.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-redo</td><td>
{{'![ASPNETMVC Button redo Icons](Icons_images/Icons_img86.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-bold</td><td>
{{'![ASPNETMVC Button bold Icons](Icons_images/Icons_img87.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-italic</td><td>
{{'![ASPNETMVC Button italic Icons](Icons_images/Icons_img88.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-underline</td><td>
{{'![ASPNETMVC Button underline Icons](Icons_images/Icons_img89.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-strikethrough</td><td>
{{'![ASPNETMVC Button strikethrough Icons](Icons_images/Icons_img90.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-font</td><td>
{{'![ASPNETMVC Button font Icons](Icons_images/Icons_img91.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowdown</td><td>
{{'![ASPNETMVC Button arrowdown Icons](Icons_images/Icons_img92.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowleft</td><td>
{{'![ASPNETMVC Button arrowleft Icons](Icons_images/Icons_img93.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowup</td><td>
{{'![ASPNETMVC Button arrowup Icons](Icons_images/Icons_img94.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowright</td><td>
{{'![ASPNETMVC Button erarrowright Icons](Icons_images/Icons_img95.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-calender</td><td>
{{'![ASPNETMVC Button calender Icons](Icons_images/Icons_img96.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-save</td><td>
{{'![ASPNETMVC Button save Icons](Icons_images/Icons_img97.png)'| markdownify }}

</td></tr>
</table>


