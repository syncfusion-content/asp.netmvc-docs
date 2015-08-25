---
layout: post
title: Behavior-Settings
description: behavior settings 
platform: ejmvc
control: Captcha
documentation: ug
---

# Behavior Settings 

## Regenerate Captcha

Captcha control supports regeneration of captcha image without full page refresh. You can achieve this by clicking refresh button. By default Captcha renders without refresh button. You can add the refresh button by setting EnableRefreshImage property to true. 

N>  To refresh the Captcha image, include “RequestMapper”. It enables you to get or set name for the post action function.



The following code example is used to render the Captcha with Refresh support.

1. Add the following code example to the corresponding CSHTML page to render Captcha with Refresh button.
 
   ~~~ javascript
 
		@Html.EJ().Captcha("captcha").EnableRefreshImage(true).RequestMapper("Refresh")
		
   ~~~
   {:.prettyprint }
   
   ~~~ cs

		// Add the following code in controller page for Captcha with refresh image
		public ActionResult Refresh(CaptchaParams parameters)
		{
			return parameters.CaptchaActions();
		}

   ~~~
   {:.prettyprint }


2. The following screenshot illustrates the Captcha with Refresh button. 

![](Behavior-Settings_images/Behavior-Settings_img2.png)



## Audio Accessibility

Sometimes, Captcha characters are too hard to identify. In this case Captcha with audio helps to understand the Captcha character.  Captcha supports captcha with audio.  You can achieve this by enabling EnableAudio propertyto true. When this property is set true, captcha renders with audio button and when you click the audio button it readouts the captcha characters. By default Captcha renders without audio button.

The following code example is used to render the Captcha with Audio.

1. Add the following code example to the corresponding CSHTML page to render Captcha with audio button.

   ~~~ javascript

		@Html.EJ().Captcha("captcha").EnableAudio(true)

   ~~~
   {:.prettyprint }

2. The following screenshot illustrates the Captcha with audio button. 

![](Behavior-Settings_images/Behavior-Settings_img3.png)



