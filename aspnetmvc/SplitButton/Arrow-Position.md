---
layout: post
title: Arrow Position | SplitButton | ASP.NET MVC | Syncfusion
description: arrow position
platform: ejmvc
control: SplitButton
documentation: ug
---

# Arrow Position

To provide a good look and feel for Split Button, position of arrow in Split Button is important. Using ArrowPosition property, you can easily customize the position of arrow inside Split Button without using any complex CSS. ArrowPosition property is applicable for both Split Button and Dropdown Button. This property represent the position of arrow with menu content.

_List of arrow position_

<table>
<tr>
<td>
Left</td><td>
Support for arrow in left.</td></tr>
<tr>
<td>
Right</td><td>
Support for arrow in right. </td></tr>
<tr>
<td>
Top</td><td>
Support for arrow in top. </td></tr>
<tr>
<td>
Bottom</td><td>
Support for arrow in bottom.</td></tr>
</table>


The following steps explain you the details on rendering the Split Button with above mentioned arrow position options.

1. In the View page, add the following button elements to configure Split Button widget.

   ~~~ cshtml

	@*Add the code in the CSHTML page to configure and initialize the control*@



	@Html.EJ().SplitButton("spltbutton11").Text("login").ShowRoundedCorner(true).Size(ButtonSize.Large).ContentType(ContentType.ImageOnly).TargetID("Ul11").PrefixIcon("e-icon e-login").ArrowPosition(ArrowPosition.Left)

	<ul id="Ul11">

		<li><span>User</span></li>

		<li><span>Guest</span></li>

		<li><span>Admin</span></li>

	</ul>

	@Html.EJ().SplitButton("spltbutton21").Text("login").ShowRoundedCorner(true).Size(ButtonSize.Mini).ContentType(ContentType.TextOnly).TargetID("Ul21").ArrowPosition(ArrowPosition.Top)

	<ul id="Ul21">

		<li><span>User</span></li>

		<li><span>Guest</span></li>

		<li><span>Admin</span></li>

	</ul>

	@Html.EJ().SplitButton("spltbutton31").Text("login").ShowRoundedCorner(true).Size(ButtonSize.Small).ContentType(ContentType.TextOnly).TargetID("Ul31").ArrowPosition(ArrowPosition.Bottom)

	<ul id="Ul31">

		<li><span>User</span></li>

		<li><span>Guest</span></li>

		<li><span>Admin</span></li>

	</ul>

	@Html.EJ().SplitButton("spltbutton41").Text("login").ShowRoundedCorner(true).Size(ButtonSize.Medium).ContentType(ContentType.TextOnly).TargetID("Ul41").ArrowPosition(ArrowPosition.Right)

	<ul id="Ul41">

		<li><span>User</span></li>

		<li><span>Guest</span></li>

		<li><span>Admin</span></li>

	</ul>

   ~~~
  

2. Execute the above code to render the following output.



![](Arrow-Position_images/Arrow-Position_img1.png)



