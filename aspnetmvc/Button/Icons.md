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

![ASPNETMVC_Button_IconsImage](Icons_images/Icons_img1.png)

 
## List of Icons

The complete list of icons is listed in the following table.

_List of icons_

<table>
<tr>
<td>
e-unpin</td><td>
{{'![ASPNETMVC_Button_unpinIconsImage](Icons_images/Icons_img2.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-pin</td><td>
{{'![ASPNETMVC_Button_pin_IconsImage](Icons_images/Icons_img3.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-upload</td><td>
{{'![ASPNETMVC_Button_upload_IconsImage](Icons_images/Icons_img4.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-reload</td><td>
{{'![ASPNETMVC_Button_reload_IconsImage](Icons_images/Icons_img5.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-collapse</td><td>
{{'![ASPNETMVC_Button_collapse_IconsImage](Icons_images/Icons_img6.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-cancel</td><td>
{{'![ASPNETMVC_Button_cancel_IconsImage](Icons_images/Icons_img7.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-expand</td><td>
{{'![ASPNETMVC_Button_expand_IconsImage](Icons_images/Icons_img8.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-minimize</td><td>
{{'![ASPNETMVC_Button_minimize_IconsImage](Icons_images/Icons_img9.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-login</td><td>
{{'![ASPNETMVC_Button_login_IconsImage](Icons_images/Icons_img10.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-orientationlanscape</td><td>
{{'![ASPNETMVC_Button_orientationlanscape_IconsImage](Icons_images/Icons_img11.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignleft</td><td>
{{'![ASPNETMVC_Button_alignleft_IconsImage](Icons_images/Icons_img12.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-aligncenter</td><td>
{{'![ASPNETMVC_Button_aligncenter_IconsImage](Icons_images/Icons_img13.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignright</td><td>
{{'![ASPNETMVC_Button_alignright_IconsImage](Icons_images/Icons_img14.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignjustify</td><td>
{{'![ASPNETMVC_Button_alignjustify_IconsImage](Icons_images/Icons_img15.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-alignnone</td><td>
{{'![ASPNETMVC_Button_alignnone_IconsImage](Icons_images/Icons_img16.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filterset</td><td>
{{'![ASPNETMVC_Button_filterset_IconsImage](Icons_images/Icons_img17.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-filternone</td><td>
{{'![ASPNETMVC_Button_filternone_IconsImage](Icons_images/Icons_img18.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadup-2x</td><td>
{{'![ASPNETMVC_Button_arrowheadup_IconsImage](Icons_images/Icons_img19.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheaddown-2x</td><td>
{{'![ASPNETMVC_Button_arrowheaddown_IconsImage](Icons_images/Icons_img20.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadleft-2x</td><td>
{{'![ASPNETMVC_Button_arrowheadleft_IconsImage](Icons_images/Icons_img21.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-arrowheadright-2x</td><td>
{{'![ASPNETMVC_Button_arrowheadright_IconsImage](Icons_images/Icons_img22.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-numbering</td><td>
{{'![ASPNETMVC_Button_numbering_IconsImage](Icons_images/Icons_img23.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-bullets</td><td>
{{'![ASPNETMVC_Button_bullets_IconsImage](Icons_images/Icons_img24.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-maximize</td><td>
{{'![ASPNETMVC_Button_maximize_IconsImage](Icons_images/Icons_img25.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-delete</td><td>
{{'![ASPNETMVC_Button_delete_IconsImage](Icons_images/Icons_img26.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-scroll</td><td>
{{'![ASPNETMVC_Button_scroll_IconsImage](Icons_images/Icons_img27.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-right-scroll</td><td>
{{'![ASPNETMVC_Button_right_IconsImage](Icons_images/Icons_img28.png)'| markdownify }}
</td></tr>
<tr>
<td>
e-search</td><td>
{{'![ASPNETMVC_Button_search_IconsImage](Icons_images/Icons_img29.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaback</td><td>
{{'![ASPNETMVC_Button_mediaback_IconsImage](Icons_images/Icons_img30.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaforward</td><td>
{{'![ASPNETMVC_Button_mediaforward_IconsImage](Icons_images/Icons_img31.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-medianext</td><td>
{{'![ASPNETMVC_Button_medianext_IconsImage](Icons_images/Icons_img32.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaprev</td><td>
{{'![ASPNETMVC_Button_mediaprev_IconsImage](Icons_images/Icons_img33.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaeject</td><td>
{{'![ASPNETMVC_Button_mediaeject_IconsImage](Icons_images/Icons_img34.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaclose</td><td>
{{'![ASPNETMVC_Button_mediaclose_IconsImage](Icons_images/Icons_img35.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediapause</td><td>
{{'![ASPNETMVC_Button_mediapause_IconsImage](Icons_images/Icons_img36.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-mediaplay</td><td>
{{'![ASPNETMVC_Button_mediaplay_IconsImage](Icons_images/Icons_img37.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-righttick</td><td>
{{'![ASPNETMVC_Button_righttick_IconsImage](Icons_images/Icons_img38.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-smile</td><td>
{{'![ASPNETMVC_Button_smile_IconsImage](Icons_images/Icons_img39.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-information</td><td>
{{'![ASPNETMVC_Button_information_IconsImage](Icons_images/Icons_img40.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-left-arrow</td><td>
{{'![ASPNETMVC_Button_left_IconsImage](Icons_images/Icons_img41.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-right-arrow</td><td>
{{'![ASPNETMVC_Button_right_IconsImage](Icons_images/Icons_img42.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-delete</td><td>
{{'![ASPNETMVC_Button_delete_IconsImage](Icons_images/Icons_img43.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-success</td><td>
{{'![ASPNETMVC_Button_percentage_IconsImage](Icons_images/Icons_img44.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-cancel</td><td>
{{'![ASPNETMVC_Button_file_IconsImage](Icons_images/Icons_img45.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-percentage-failed</td><td>
{{'![ASPNETMVC_Button_file_IconsImage](Icons_images/Icons_img46.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-file-retry</td><td>
{{'![ASPNETMVC_Button_file_IconsImage](Icons_images/Icons_img47.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-resize-handle</td><td>
{{'![ASPNETMVC_Button_resize_IconsImage](Icons_images/Icons_img48.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-down-arrow</td><td>
{{'![ASPNETMVC_Button_down-arrow_IconsImage](Icons_images/Icons_img49.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-time</td><td>
{{'![ASPNETMVC_Button_time_IconsImage](Icons_images/Icons_img50.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-up-arrow</td><td>
{{'![ASPNETMVC_Button_up-arrow_IconsImage](Icons_images/Icons_img51.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-date</td><td>
{{'![ASPNETMVC_Button_date_IconsImage](Icons_images/Icons_img52.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-datetime</td><td>
{{'![ASPNETMVC_Button_datetime_IconsImage](Icons_images/Icons_img53.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-collapse-arrow</td><td>
{{'![ASPNETMVC_Button_collapse_IconsImage](Icons_images/Icons_img54.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-expand-arrow</td><td>
{{'![ASPNETMVC_Button_expand_IconsImage](Icons_images/Icons_img55.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-restore</td><td>
{{'![ASPNETMVC_Button_restore_IconsImage](Icons_images/Icons_img56.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-plus</td><td>
{{'![ASPNETMVC_Button_plus_IconsImage](Icons_images/Icons_img57.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-minus</td><td>
{{'![ASPNETMVC_Button_minus_IconsImage](Icons_images/Icons_img58.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-handup</td><td>
{{'![ASPNETMVC_Button_handup_IconsImage](Icons_images/Icons_img59.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clock</td><td>
{{'![ASPNETMVC_Button_clock_IconsImage](Icons_images/Icons_img60.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cursor</td><td>
{{'![ASPNETMVC_Button_cursor_IconsImage](Icons_images/Icons_img61.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlink</td><td>
{{'![ASPNETMVC_Button_hyperlink_IconsImage](Icons_images/Icons_img62.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-hyperlinkbreak</td><td>
{{'![ASPNETMVC_Button_hyperlinkbreak_IconsImage](Icons_images/Icons_img63.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-settings</td><td>
{{'![ASPNETMVC_Button_settings_IconsImage](Icons_images/Icons_img64.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-shoppingcart</td><td>
{{'![ASPNETMVC_Button_shoppingcart_IconsImage](Icons_images/Icons_img65.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-palette</td><td>
{{'![ASPNETMVC_Button_palette_IconsImage](Icons_images/Icons_img66.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-warningmessage</td><td>
{{'![ASPNETMVC_Button_warningmessage_IconsImage](Icons_images/Icons_img67.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-cut</td><td>
{{'![ASPNETMVC_Button_cut_IconsImage](Icons_images/Icons_img68.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-copy</td><td>
{{'![ASPNETMVC_Button_copy_IconsImage](Icons_images/Icons_img69.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-paste</td><td>
{{'![ASPNETMVC_Button_paste_IconsImage](Icons_images/Icons_img70.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-edit</td><td>
{{'![ASPNETMVC_Button_edit_IconsImage](Icons_images/Icons_img71.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapleft</td><td>
{{'![ASPNETMVC_Button_swapleft_IconsImage](Icons_images/Icons_img72.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapright</td><td>
{{'![ASPNETMVC_Button_swapright_IconsImage](Icons_images/Icons_img73.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapup</td><td>
{{'![ASPNETMVC_Button_swapup_IconsImage](Icons_images/Icons_img74.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-swapdown</td><td>
{{'![ASPNETMVC_Button_swapdown_IconsImage](Icons_images/Icons_img75.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomin</td><td>
{{'![ASPNETMVC_Button_zoomin_IconsImage](Icons_images/Icons_img76.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-zoomout</td><td>
{{'![ASPNETMVC_Button_zoomout_IconsImage](Icons_images/Icons_img77.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-star</td><td>
{{'![ASPNETMVC_Button_star_IconsImage](Icons_images/Icons_img78.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-home</td><td>
{{'![ASPNETMVC_Button_home_IconsImage](Icons_images/Icons_img79.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-clipboard</td><td>
{{'![ASPNETMVC_Button_clipboard_IconsImage](Icons_images/Icons_img80.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-userlogin</td><td>
{{'![ASPNETMVC_Button_userlogin_IconsImage](Icons_images/Icons_img81.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-dataexport</td><td>
{{'![ASPNETMVC_Button_dataexport_IconsImage](Icons_images/Icons_img82.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheadright</td><td>
{{'![ASPNETMVC_Button_arrowheadright_IconsImage](Icons_images/Icons_img83.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-arrowheaddown</td><td>
{{'![ASPNETMVC_Button_arrowheaddown_IconsImage](Icons_images/Icons_img84.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-undo</td><td>
{{'![ASPNETMVC_Button_undo_IconsImage](Icons_images/Icons_img85.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-redo</td><td>
{{'![ASPNETMVC_Button_redo_IconsImage](Icons_images/Icons_img86.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-bold</td><td>
{{'![ASPNETMVC_Button_bold_IconsImage](Icons_images/Icons_img87.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-italic</td><td>
{{'![ASPNETMVC_Button_italic_IconsImage](Icons_images/Icons_img88.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-underline</td><td>
{{'![ASPNETMVC_Button_underline_IconsImage](Icons_images/Icons_img89.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-strikethrough</td><td>
{{'![ASPNETMVC_Button_strikethrough_IconsImage](Icons_images/Icons_img90.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-font</td><td>
{{'![ASPNETMVC_Button_font_IconsImage](Icons_images/Icons_img91.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowdown</td><td>
{{'![ASPNETMVC_Button_arrowdown_IconsImage](Icons_images/Icons_img92.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowleft</td><td>
{{'![ASPNETMVC_Button_arrowleft_IconsImage](Icons_images/Icons_img93.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowup</td><td>
{{'![ASPNETMVC_Button_arrowup_IconsImage](Icons_images/Icons_img94.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-rarrowright</td><td>
{{'![ASPNETMVC_Button_erarrowright_IconsImage](Icons_images/Icons_img95.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-calender</td><td>
{{'![ASPNETMVC_Button_calender_IconsImage](Icons_images/Icons_img96.png)'| markdownify }}

</td></tr>
<tr>
<td>
e-save</td><td>
{{'![ASPNETMVC_Button_save_IconsImage](Icons_images/Icons_img97.png)'| markdownify }}

</td></tr>
</table>


