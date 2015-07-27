---
layout: post
title: Date-in-other-months
description: date in other months
platform: ejmvc
control: DateTimePicker
documentation: ug
---

# Date in other months

DateTimePicker calendar can display the dates in other months at the start or end of the current month. To enable or disable the display of other month dates in the current month, you can use the property called ShowOtherMonths. By setting this property value as “True” you can display the dates in other months at the start or end of the current month. By default the value of this property is “True”. 

Consider you are going to calculate the monthly report of your company’s employee attendance. To avoid the mistake of selecting other month dates while calculating current month report, you can disable showing other month dates in the current month. You can achieve this requirement by setting ShowOtherMonths value as “False”.

1. Add the following code in your CSHTML page to render DateTimePicker widget.

   ~~~ html
   
     [_cshtml]
	 
	    @*Add the following code example to the corresponding CSHTML page to render DateTimePicker widget with customized other months*@

		@Html.EJ().DateTimePicker("DateTime").ShowOtherMonths(false).Width("175px")

   ~~~
   {:.prettyprint }
   

2. The following screenshot displays the output for the above code.

	![](Date-in-other-months_images/Date-in-other-months_img1.png)



