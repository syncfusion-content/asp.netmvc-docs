---
layout: post
title: RTL-Support
description: rtl support
platform: ejmvc
control: Split Button
documentation: ug
---

## RTL Support

In some cases it is necessary to use right to left alignment. RTL support is provided by using EnableRTL property. In RTL mode when there is more than one content (image/text, image/image) in Split Button, then the content is aligned in right to left format. For example, when text is in left and image is in right position, after applying right to left alignment these position are interchanged.

The following steps explains you the details about rendering the button with Right to left alignment support

1. In the VIEW page, add the following button elements to configure Split Button widget.





[CSHTML]

@*Add the code in the CSHTML page to configure and initialize the control*@



    @*Enable the alignment format for split button control as follows.*@



&lt;div class="spltspan"&gt;

        @Html.EJ().SplitButton("spltbutton_rtl").Text("login").Size(ButtonSize.Small).ShowRoundedCorner(true).ContentType(ContentType.TextAndImage).PrefixIcon("e-login").ImagePosition(ImagePosition.ImageLeft).TargetID("Ul11").EnableRTL(true)

        &lt;ul id="Ul11"&gt;

            &lt;li&gt;<span>User</span>&lt;/li&gt;

            &lt;li&gt;<span>Guest</span>&lt;/li&gt;

            &lt;li&gt;<span>Admin</span>&lt;/li&gt;

        &lt;/ul&gt;



    &lt;/div&gt;





Execute the above code to render the following output.

{ ![](RTL-Support_images/RTL-Support_img1.png) | markdownify }
{:.image }


