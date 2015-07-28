---
layout: post
title: Keyboard-interaction
description: keyboard interaction
platform: ejmvc
control: Rotator
documentation: ug
---

# Keyboard interaction

The AllowKeyboardNavigation property turns on keyboardinteraction with the Rotator items. You must set this property to ‘true’ to access the keyboard shortcuts. The default value is ‘true’. The value set to this property is Boolean.

The entire Rotator commands are accessed through the keyboard by specifying the KeyboardShortcut in the following table.

<table>
<tr>
<th>
Keyboard Shortcut</th><th>
Function</th></tr>
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

{% highlight html %}
    // Add this code in your CSHTML page and refer local data section for binding Rotator items.
	<ul id="slide" style="display: none">    
		<li> <img src="@Url.Content("~/Images/rotator/green.jpg")" title="Green" /> </li>    
		<li> <img src="@Url.Content("~/Images/rotator/snow.jpg")" title="Snow" /> </li>    
		<li> <img src="@Url.Content("~/Images/rotator/wheat.jpg")" title="Wheat" /> </li>    
		<li> <img src="@Url.Content("~/Images/rotator/tablet.jpg")" title="Tablet" /> </li>    
		<li>        <img src="@Url.Content("~/Images/rotator/sea.jpg")" title="Sea" /></li>    
		<li>        <img src="@Url.Content("~/Images/rotator/bread.jpg")" title="Bread" /></li>
	</ul>
	
	@Html.EJ().Rotator("slidercontent").Items(itemElement =>  { 
	
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/green.jpg")" /> </div>);                           
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/snow.jpg")"/>  </div>);                           
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/wheat.jpg")" />  </div>);                           
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/tablet.jpg")" /> </div>);                           
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/sea.jpg")" /> </div>);                           
	itemElement.Add().ContentTemplate(@<div> <img class="image" src="@Url.Content("~/Images/rotator/bread.jpg")" /> </div>);})
	
	.SlideWidth("600px").SlideHeight("350px")
	.ShowThumbnail(true).ThumbnailSourceID("slide")
	.AllowKeyboardNavigation(true).ShowPlayButton(true)  
	
{% endhighlight %}
	
{% highlight js %}

<script type="text/JavaScript"> 
   
$(function () {   
     
	//Control focus key      
	
	$(document).on("keydown", function (e) {   
	
	if (e.altKey && e.keyCode === 74) 
	
	{ 
	
		// j- key code.         
		
		$("#slidercontent")[0].focus();    
        
		}        
		
	});    });
	
</script>

{% endhighlight %}

Run the above sample, we get the output like this,

![](Keyboard-interaction_images/Keyboard-interaction_img1.png)