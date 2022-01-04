---
layout: post
title: Icons | Button | ASP.NET MVC | Syncfusion
description: Learn here all about Icons support in Syncfusion ASP.NET MVC Button control, its elements and more
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

![Adding icon Button in ASP.NET MVC Button](Icons_images/Icons_img1.png)

 
## List of Icons

The complete list of icons is listed in the following table.

_List of icons_

<table>
<tr>
<td>
e-unpin</td><td>
{{'![e unpin in ASP.NET MVC Button](Icons_images/Icons_img2.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-pin</td><td>
{{'![e pin  in ASP.NET MVC Button](Icons_images/Icons_img3.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-upload</td><td>
{{'![e upload in ASP.NET MVC Button](Icons_images/Icons_img4.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-reload</td><td>
{{'![e reload in ASP.NET MVC Button](Icons_images/Icons_img5.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-collapse</td><td>
{{'![e collapse in ASP.NET MVC Button](Icons_images/Icons_img6.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-cancel</td><td>
{{'![e cancel in ASP.NET MVC Button](Icons_images/Icons_img7.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-expand</td><td>
{{'![e expand in ASP.NET MVC Button](Icons_images/Icons_img8.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-minimize</td><td>
{{'![e minimize in ASP.NET MVC Button](Icons_images/Icons_img9.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-login</td><td>
{{'![e login in ASP.NET MVC Button](Icons_images/Icons_img10.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-orientationlanscape</td><td>
{{'![e orientationlanscape in ASP.NET MVC Button](Icons_images/Icons_img11.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignleft</td><td>
{{'![e alignleft in ASP.NET MVC Button](Icons_images/Icons_img12.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-aligncenter</td><td>
{{'![e aligncenter in ASP.NET MVC Button](Icons_images/Icons_img13.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignright</td><td>
{{'![e alignright in ASP.NET MVC Button](Icons_images/Icons_img14.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignjustify</td><td>
{{'![e alignjustify in ASP.NET MVC Button](Icons_images/Icons_img15.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignnone</td><td>
{{'![e alignnone in ASP.NET MVC Button](Icons_images/Icons_img16.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filterset</td><td>
{{'![e filterset in ASP.NET MVC Button](Icons_images/Icons_img17.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filternone</td><td>
{{'![e filternone in ASP.NET MVC Button](Icons_images/Icons_img18.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadup-2x</td><td>
{{'![e arrowheadup 2x in ASP.NET MVC Button](Icons_images/Icons_img19.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheaddown-2x</td><td>
{{'![e arrowheaddown 2x in ASP.NET MVC Button](Icons_images/Icons_img20.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadleft-2x</td><td>
{{'![e arrowheadleft 2x in ASP.NET MVC Button](Icons_images/Icons_img21.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadright-2x</td><td>
{{'![e arrowheadright 2x in ASP.NET MVC Button](Icons_images/Icons_img22.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-numbering</td><td>
{{'![e numbering in ASP.NET MVC Button](Icons_images/Icons_img23.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-bullets</td><td>
{{'![e bullets in ASP.NET MVC Button](Icons_images/Icons_img24.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-maximize</td><td>
{{'![e maximize in ASP.NET MVC Button](Icons_images/Icons_img25.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-delete</td><td>
{{'![e delete in ASP.NET MVC Button](Icons_images/Icons_img26.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-scroll</td><td>
{{'![e scroll in ASP.NET MVC Button](Icons_images/Icons_img27.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-right-scroll</td><td>
{{'![e right scroll in ASP.NET MVC Button](Icons_images/Icons_img28.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-search</td><td>
{{'![e search in ASP.NET MVC Button](Icons_images/Icons_img29.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaback</td><td>
{{'![e mediaback in ASP.NET MVC Button](Icons_images/Icons_img30.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaforward</td><td>
{{'![e mediaforward in ASP.NET MVC Button](Icons_images/Icons_img31.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-medianext</td><td>
{{'![e medianext in ASP.NET MVC Button](Icons_images/Icons_img32.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaprev</td><td>
{{'![e mediaprev in ASP.NET MVC Button](Icons_images/Icons_img33.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaeject</td><td>
{{'![e mediaeject in ASP.NET MVC Button](Icons_images/Icons_img34.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaclose</td><td>
{{'![e mediaclose in ASP.NET MVC Button](Icons_images/Icons_img35.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediapause</td><td>
{{'![e mediapause in ASP.NET MVC Button](Icons_images/Icons_img36.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaplay</td><td>
{{'![e mediaplay in ASP.NET MVC Button](Icons_images/Icons_img37.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-righttick</td><td>
{{'![e righttick in ASP.NET MVC Button](Icons_images/Icons_img38.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-smile</td><td>
{{'![e smile in ASP.NET MVC Button](Icons_images/Icons_img39.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-information</td><td>
{{'![e information in ASP.NET MVC Button](Icons_images/Icons_img40.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-left-arrow</td><td>
{{'![e left arrow in ASP.NET MVC Button](Icons_images/Icons_img41.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-right-arrow</td><td>
{{'![e right arrow in ASP.NET MVC Button](Icons_images/Icons_img42.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-delete</td><td>
{{'![e file delete in ASP.NET MVC Button](Icons_images/Icons_img43.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-success</td><td>
{{'![e file percentage in ASP.NET MVC Button](Icons_images/Icons_img44.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-cancel</td><td>
{{'![e file cancel in ASP.NET MVC Button](Icons_images/Icons_img45.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-failed</td><td>
{{'![e file percentage failed in ASP.NET MVC Button](Icons_images/Icons_img46.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-retry</td><td>
{{'![e file retry in ASP.NET MVC Button](Icons_images/Icons_img47.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-resize-handle</td><td>
{{'![e resize handle in ASP.NET MVC Button](Icons_images/Icons_img48.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-down-arrow</td><td>
{{'![e down arrow in ASP.NET MVC Button](Icons_images/Icons_img49.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-time</td><td>
{{'![e time in ASP.NET MVC Button](Icons_images/Icons_img50.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-up-arrow</td><td>
{{'![e up arrow in ASP.NET MVC Button](Icons_images/Icons_img51.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-date</td><td>
{{'![e date in ASP.NET MVC Button](Icons_images/Icons_img52.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-datetime</td><td>
{{'![e datetime in ASP.NET MVC Button](Icons_images/Icons_img53.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-collapse-arrow</td><td>
{{'![e collapse arrow in ASP.NET MVC Button](Icons_images/Icons_img54.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-expand-arrow</td><td>
{{'![e expand arrow in ASP.NET MVC Button](Icons_images/Icons_img55.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-restore</td><td>
{{'![e restore in ASP.NET MVC Button](Icons_images/Icons_img56.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-plus</td><td>
{{'![e plus in ASP.NET MVC Button](Icons_images/Icons_img57.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-minus</td><td>
{{'![e minus in ASP.NET MVC Button](Icons_images/Icons_img58.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-handup</td><td>
{{'![e handup in ASP.NET MVC Button](Icons_images/Icons_img59.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clock</td><td>
{{'![e clock in ASP.NET MVC Button](Icons_images/Icons_img60.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cursor</td><td>
{{'![e cursor in ASP.NET MVC Button](Icons_images/Icons_img61.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlink</td><td>
{{'![e hyperlink in ASP.NET MVC Button](Icons_images/Icons_img62.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlinkbreak</td><td>
{{'![e hyperlinkbreak in ASP.NET MVC Button](Icons_images/Icons_img63.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-settings</td><td>
{{'![e settings in ASP.NET MVC Button](Icons_images/Icons_img64.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-shoppingcart</td><td>
{{'![e shoppingcart in ASP.NET MVC Button](Icons_images/Icons_img65.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-palette</td><td>
{{'![e palette in ASP.NET MVC Button](Icons_images/Icons_img66.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-warningmessage</td><td>
{{'!e warningmessage in ASP.NET MVC Button[](Icons_images/Icons_img67.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cut</td><td>
{{'![e cut in ASP.NET MVC Button](Icons_images/Icons_img68.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-copy</td><td>
{{'![e copy in ASP.NET MVC Button](Icons_images/Icons_img69.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-paste</td><td>
{{'![e paste in ASP.NET MVC Button](Icons_images/Icons_img70.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-edit</td><td>
{{'![e edit in ASP.NET MVC Button](Icons_images/Icons_img71.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapleft</td><td>
{{'![e swapleft in ASP.NET MVC Button](Icons_images/Icons_img72.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapright</td><td>
{{'![e swapright in ASP.NET MVC Button](Icons_images/Icons_img73.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapup</td><td>
{{'![e swapup in ASP.NET MVC Button](Icons_images/Icons_img74.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapdown</td><td>
{{'![e swapdown in ASP.NET MVC Button](Icons_images/Icons_img75.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomin</td><td>
{{'![e zoomin in ASP.NET MVC Button](Icons_images/Icons_img76.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomout</td><td>
{{'![e zoomout in ASP.NET MVC Button](Icons_images/Icons_img77.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-star</td><td>
{{'![e star in ASP.NET MVC Button](Icons_images/Icons_img78.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-home</td><td>
{{'![e home in ASP.NET MVC Button](Icons_images/Icons_img79.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clipboard</td><td>
{{'![e clipboard in ASP.NET MVC Button](Icons_images/Icons_img80.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-userlogin</td><td>
{{'![e userlogin in ASP.NET MVC Button](Icons_images/Icons_img81.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-dataexport</td><td>
{{'![e dataexport in ASP.NET MVC Button](Icons_images/Icons_img82.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheadright</td><td>
{{'![e arrowheadright in ASP.NET MVC Button](Icons_images/Icons_img83.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheaddown</td><td>
{{'![e arrowheaddown in ASP.NET MVC Button](Icons_images/Icons_img84.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-undo</td><td>
{{'![e undo in ASP.NET MVC Button](Icons_images/Icons_img85.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-redo</td><td>
{{'![e redo in ASP.NET MVC Button](Icons_images/Icons_img86.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-bold</td><td>
{{'![e bold in ASP.NET MVC Button](Icons_images/Icons_img87.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-italic</td><td>
{{'![e italic in ASP.NET MVC Button](Icons_images/Icons_img88.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-underline</td><td>
{{'![e underline in ASP.NET MVC Button](Icons_images/Icons_img89.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-strikethrough</td><td>
{{'![e strikethrough in ASP.NET MVC Button](Icons_images/Icons_img90.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-font</td><td>
{{'![e font in ASP.NET MVC Button](Icons_images/Icons_img91.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowdown</td><td>
{{'![e rarrowdown in ASP.NET MVC Button](Icons_images/Icons_img92.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowleft</td><td>
{{'![e rarrowleft in ASP.NET MVC Button](Icons_images/Icons_img93.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowup</td><td>
{{'![e rarrowup in ASP.NET MVC Button](Icons_images/Icons_img94.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowright</td><td>
{{'![e rarrowright in ASP.NET MVC Button](Icons_images/Icons_img95.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-calender</td><td>
{{'![e calendar in ASP.NET MVC Button](Icons_images/Icons_img96.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-save</td><td>
{{'![e save in ASP.NET MVC Button](Icons_images/Icons_img97.png)'| markdownify }}

</td></tr>
</table>


