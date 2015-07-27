---
layout: post
title: Dropdown-Button
description: dropdown button
platform: ejmvc
control: Split Button
documentation: ug
---

# Dropdown Button

You can change the Split Button as Dropdown Button that consists of a single button that when clicked displays a drop-down list of mutually exclusive items. You can achieve this by using default functionality of Split Button with ButtonMode as ButtonMode.Dropdown. Initially the TargetID is a mandatory one.

The following steps explain how to change the Split Button as Dropdown Button.

1. In the VIEW page, add the following button elements to configure Button widget.




{% highlight html %}
[CSHTML]

@*Add the code in the CSHTML page to configure and initialize the control*@



@Html.EJ().SplitButton("dropdownbtn").Text("login").ShowRoundedCorner(true).Size(ButtonSize.Medium).ContentType(ContentType.TextOnly).TargetID("menu1").ButtonMode(ButtonMode.Dropdown)

<ul id="menu1">

    <li><span>User</span></li>

    <li><span>Guest</span></li>

    <li><span>Admin</span></li>

</ul>

{% endhighlight %}



2. Execute the above code to render the following output.



{{ '![C:/Users/ApoorvahR/AppData/Roaming/Skype/apoorvahr_1880/media_messaging/media_cache/^FBB9E285A6F3042DAB9B40116599699BB899EC45D623A2651A^pimgpsh_fullsize_distr.jpg](Dropdown-Button_images/Dropdown-Button_img1.png)' | markdownify }}





