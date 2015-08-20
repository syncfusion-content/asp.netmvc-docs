---
layout: post
title: Behavior-Settings
description: behavior settings 
platform: ejmvc
control: Dialog
documentation: ug
---

# Behavior Settings 

## Resize Support

The Dialog control can be resized using this feature. You can resize the Dialog by dragging the bottom right corner area.

## Enable Resize Option

The following steps explains you the implementation of resize option in the Dialog control. 





1. In a VIEW page set a helper element with dialog content for rendering the Dialog control. 


   ~~~ js

	   // In the CSHTML page, add the Dialog widget using helpers and set EnableResize to ‘true’. 

	   @{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

	   EnableResize(true).Render();}

   ~~~
   {:.prettyprint }






2. The output for Dialog control when “EnableResize” is “true” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img1.png) 

   _Figure 6: Dialog with “EnableResize”_

                                                                              

## Drag Support

The Dialog control supports the drag functionality. You can click the Dialog header and drag the control anywhere in the web page.

## Allow Drag Option

The following steps explains you the implementation of drag option in the Dialog control. 

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 



   ~~~ js

	   // In the CSHTML page add the Dialog widget using helpers and set AllowDraggable to ‘true’.


	   @{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

	   AllowDraggable(true).Render();}

   ~~~
   {:.prettyprint }






2. The output for Dialog control when “AllowDraggable” is “true” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img2.png) 

   _Figure 7: Dialog with "AllowDraggable"_
                                                          

## Close Icon ToolTip Support

1. You can change the close icon tooltip in the Dialog control by using CloseIconTooltipproperty. The default value for CloseIconTooltip is close in the Dialog control.

## Define Close Icon ToolTip

The following steps explains you the implementation of close icon tooltip option in the Dialog control. 

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 


   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and assign the CloseIconTooltip property as close.



		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>)

		   .Width(300).Height("200").CloseIconTooltip("close").Render();}
   
   ~~~
   {:.prettyprint }



2. The output for Dialog control when “CloseIconTooltip” is “close” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img3.png)
   
   _Figure 8: Dialog with "CloseIconTooltip_


## Persistence Support

The Dialog control supports the state maintenance where you can maintain the state of the Dialog control in the web page. The default value for EnablePersistence is false in the Dialog control.

## Enable Persistence Option

The following steps explains the implementation of persistence support in the Dialog control. 

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 




{% highlight html %}

// In the CSHTML page add the Dialog widget using helpers and set EnablePersistence to ‘true’.



    @{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>)

      .Width(300).Height("200").EnablePersistence(true).Render();}


{% endhighlight %}



Make resize and reload the web page. The state is maintained in the Dialog control. The output for Dialog control when “EnablePersistence” is “true” is as follows. 

![](Behavior-Settings_images/Behavior-Settings_img4.png)

_Figure 9: Dialog with “EnablePersistence"_


## Enabled or Disabled

The Dialog control supports the Enabled or Disabled option that allows you to enable or disable the Dialog control in the web page.

## Disable Dialog Control

The following steps explains you the implementation of disable option in the Dialog control. 

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 




   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and set Enabled to ‘false’.



			@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>)

			  .Width(300).Height("200").Enabled(false).Render();}

   ~~~
   {:.prettyprint }




2. The output for Dialog control when Enabled is “false” is as follows.



   ![](Behavior-Settings_images/Behavior-Settings_img5.png)

   _Figure11: Dialog with “Enabled" as “false”_                                                                  

## Positioning Dialog

The Dialog provides the option to place the control based upon its X-axis and Y-axis position in the web page. The following steps explains you the implementation of dialog position option.

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 


   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and set the Position values.



		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>

					The Syncfusion Dialog control is rendered.<br />

					Position

					<br />

					X-Axis : 20

					<br />

					Y-Axis : 26

				</div>).Width(300).Height("200").Position(p => p.XValue("20").YValue("26")).

		Render();}

   ~~~
   {:.prettyprint }


2. The output for Dialog control after setting X-axis and Y-axis value.

   ![](Behavior-Settings_images/Behavior-Settings_img6.png)

   _Figure12: Dialog with “Position"_

## Header Option

You can show or hide the Dialog header by setting ShowHeader property. The following steps explains you the implementation of Dialog header option.

## Show Header

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 

   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and set the ShowHeader as true. 

		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

		ShowHeader(true).Render();}

   ~~~
   {:.prettyprint }






2. The output for Dialog control when ShowHeader is “true” is as follows.

![](Behavior-Settings_images/Behavior-Settings_img7.png)' | markdownify }}

_Figure13: Dialog with “ShowHeader" as “true”_                                           

## Hide Header

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 


   ~~~ js
   
		// In the CSHTML page add the Dialog widget using helpers and set the ShowHeader to ‘false’. 

		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

		ShowHeader(false).Render();}

   ~~~
   {:.prettyprint }


2. The output for Dialog control when ShowHeader is “false” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img8.png)
   
   _Figure14: Dialog with “ShowHeader" as “false”_                                     

## Show at Initial

The Dialog control contains an option to be opened state or closed state at initial.

 The default value for ShowOnInit is true. Setting false to the ShowOnInit hides the Dialog control at initialization.

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 


   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and set the ShowOnInit to ‘true’.

		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

		ShowOnInit(true).Render();}

   ~~~
   {:.prettyprint }


2. The output for Dialog control when ShowOnInit is “true” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img9.png)



_Figure15: Dialog with “ShowOnInit"_                               

## Rounded Corner Support

The Dialog can support with rounded corner appearance, the default value for ShowRoundedCorner is false. 

1. In the VIEW page set a helper element with the dialog content for rendering the Dialog control. 



   ~~~ js

		// In the CSHTML page add the Dialog widget using helpers and set ShowRoundedCorner to ‘true’.



		@{Html.EJ().Dialog("dialog").Title("Syncfusion Dialog").ContentTemplate(@<div>The Syncfusion Dialog control is rendered.</div>).Width(300).Height("200").

		ShowRoundedCorner(true).Render();}


   ~~~
   {:.prettyprint }





2. The output for Dialog control when ShowRoundedCorner is “true” is as follows.

   ![](Behavior-Settings_images/Behavior-Settings_img10.png)



_Figure16: Dialog with “ShowRoundedCorner"_

