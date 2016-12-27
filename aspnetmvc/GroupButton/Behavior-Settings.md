---
layout: post
title: Button Type | GroupButton | ASP.NET MVC | Syncfusion
description: Groupbutton
platform: aspnet mvc
control: GroupButton
documentation: ug
---

# Behavior settings

Groupbutton provides options through which you can customize the default behavior of Groupbutton control.

## Groupbutton Mode

The default behavior of Groupbutton is like Radiobutton, i.e., only one item can be selected at a time.

{% highlight html %}

@Html.EJ().GroupButton("GroupButton").GroupButtonMode(GroupButtonMode.RadioButton).Items(item =>
                   {
                       item.Add().Text("Save");
                       item.Add().Text("Open");
                       item.Add().Text("Delete");
                   })

{% endhighlight %}

![](Behavior-Settings_images/Radiobutton.png)
RadioButton mode {:.caption}

To enable selection of one or more Groupbutton items at a time, you can set the Groupbutton mode to Checkbox. With this, you can toggle the each button’s state to perform actions, since all the button will behave like individual buttons.

{% highlight html %}

 @Html.EJ().GroupButton("GroupButton").GroupButtonMode(GroupButtonMode.CheckBox).Items(item =>
                   {
                       item.Add().Text("Save");
                       item.Add().Text("Open");
                       item.Add().Text("Delete");
                   })   

{% endhighlight %}

![](Behavior-Settings_images/Checkbox.png)
CheckBox mode {:.caption}
