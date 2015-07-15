---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: CurrencyTextBox
documentation: ug
---

# Getting Started

This section explains briefly about how to create a EJMVC CurrencyTextBox in ASP.NET MVC platform.

## Create your first CurrencyTextBox in MVC

From the following steps you can learn how to create and use CurrencyTextBox in your application. Here we have showcased, a small Electric bill calculator application using EJMVC Editors widgets.The Essential ASP.NET MVC Editors control includes numeric, percentage, currency and maskedit textbox controls. This will guide you to use the wide range of Editors functionalities to complete this application. 

{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


Create Editors 

ASP.NET MVC Editors renders built-in features like keyboard navigation, min and max range and flexible API’s. 

1. Create a MVC Project and add necessary Dll’s and Scripts. Refer [MVC-Getting Started](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm). 
2. Add necessary helper elements to render the Editor components.



&lt;div class="editors"&gt;

&lt;div class="ele-icon"&gt;&lt;/div&gt;

<div class="ele-txt" style="">Electricity Bill Calculator</div>

&lt;br /&gt;

&lt;table class="editors"&gt;

     &lt;tbody&gt;

         &lt;tr&gt;

           &lt;td&gt;

              <label>Unit meters</label>

           &lt;/td&gt;

           &lt;td&gt;    @* NumericTextBox creation with watermark text *@

              @Html.EJ().NumericTextbox("numeric").WatermarkText("Units")

           &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Service Tax</label>

            &lt;/td&gt;

            &lt;td&gt;     @* PercentageTextBox creation with watermark text *@

                 @Html.EJ().PercentageTextbox("percent").WatermarkText("Tax")

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

             &lt;td&gt;

               <label>Fare</label>

            &lt;/td&gt;

            &lt;td&gt;    @* CurrencyTextBox creation with watermark text *@

                @Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit")

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Mobile No</label>

            &lt;/td&gt;

            &lt;td&gt;    @* MaskEditTextBox creation with watermark text *@

               @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number")

            &lt;/td&gt;

       &lt;/tr&gt;

     &lt;/tbody&gt;&lt;/table&gt;

  &lt;div class="paybill"&gt;      @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").ContentType(ContentType.TextAndImage).PrefixIcon("e-calender")

  &lt;/div&gt;

&lt;/div&gt;

3. The following styles are added to arrange the Editors.  You can add the following location in the URL path for the background image and to apply styling [http://js.syncfusion.com/UG/Web/Content/electricity.png](http://js.syncfusion.com/UG/Web/Content/electricity.png)



&lt;style type="text/css" class="cssStyles"&gt;

    .ele-icon

    {

        display: inline-block;

        background-image: url(http://js.syncfusion.com/UG/Web/Content/electricity.png);

        background-repeat: no-repeat;

        background-size: contain;

        height: 50px;

        width: 50px;

        margin-left:50px;

        margin-top:15px;

    }

    .ele-txt

    {

        display: inline-block;

        font-size: 20px;

        font-weight: bolder;

        height: 50px;

        position: relative;

        text-align: center;

        top: -20px;

    }

    .editors

    {

        max-width: 400px;

        border: 2px solid #DDDDDD;

    }

        .editors table

        {

            border:0px;

            padding-left:50px;

        }

    .paybill

    {

        margin:15px 0px 10px 208px;

    }

    .editors label

    {

        display: block;

        width: 130px;

    }

&lt;/style&gt;



4. Execute the code to render Editors as follows

{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }


_CurrencyTextBox with watermark text_

Set MinValue, MaxValue and value in CurrencyTextBox

You can set the “MinValue”,“MaxValue” and “Value” in Currency, percentage and Currency text boxes for maintaining the range in Editors widgets. In this scenario, you have to enter the values between the default ranges and enter the phone number in the Maskedit widget by using the”MaskFormat” property. By using DecimalPlaces property for CurrencyTextBox you can get decimal values. The following code example illustrates how to achieve this.

&lt;div class="editors"&gt;

&lt;div class="ele-icon"&gt;&lt;/div&gt;

<div class="ele-txt" style="">Electricity Bill Calculator</div>

&lt;br /&gt;

&lt;table class="editors"&gt;

     &lt;tbody&gt;

         &lt;tr&gt;

           &lt;td&gt;

              <label>Unit meters</label>

           &lt;/td&gt;

           &lt;td&gt;    @Html.EJ().NumericTextbox("numeric").WatermarkText("Units").MinValue(1).MaxValue(10000).Value("70")

           &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Service Tax</label>

            &lt;/td&gt;

            &lt;td&gt;                 @Html.EJ().PercentageTextbox("percent").WatermarkText("Tax").MinValue(5).MaxValue(100).Value("15")

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

             &lt;td&gt;

               <label>Fare</label>

            &lt;/td&gt;

            &lt;td&gt;                @Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit").MinValue(0.00).MaxValue(100000.00).Value("350.00").DecimalPlaces(2)

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Mobile No</label>

            &lt;/td&gt;

            &lt;td&gt;

               @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number").MaskFormat("99-999-99999").Value("9090909090")

            &lt;/td&gt;

       &lt;/tr&gt;

     &lt;/tbody&gt;

&lt;/table&gt;

  &lt;div class="paybill"&gt;

    @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").ContentType(ContentType.TextAndImage).PrefixIcon("e-calender")

  &lt;/div&gt;

&lt;/div&gt;

The following screenshot illustrates the output of the above code examples. 

{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


Setting the Strict Mode Option

You can set the “StrictMode” option to restrict entering values defined outside the range. The following code example illustrates how to set strict mode option. 

&lt;div class="editors"&gt;

&lt;div class="ele-icon"&gt;&lt;/div&gt;

<div class="ele-txt" style="">ElectricityBill Calculator</div>&lt;br /&gt;

&lt;table class="editors"&gt;

     &lt;tbody&gt;

         &lt;tr&gt;

           &lt;td&gt;

              <label>Unit meters</label>

           &lt;/td&gt;

           &lt;td&gt;                  @Html.EJ().NumericTextbox("numeric").WatermarkText("Units").MinValue(1).MaxValue(10000).Value("70").EnableStrictMode(true)

           &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Service Tax</label>

            &lt;/td&gt;

            &lt;td&gt;     

@Html.EJ().PercentageTextbox("percent").WatermarkText("Tax").MinValue(5).MaxValue(100).Value("15")

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

             &lt;td&gt;

               <label>Fare</label>

            &lt;/td&gt;

            &lt;td&gt;   

@Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit").MinValue(0.00).MaxValue(100000.00).Value("350.00").DecimalPlaces(2)

            &lt;/td&gt;

        &lt;/tr&gt;

        &lt;tr&gt;

            &lt;td&gt;

               <label>Mobile No</label>

            &lt;/td&gt;

            &lt;td&gt;    

               @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number").MaskFormat("99-999-99999").Value("9090909090")

            &lt;/td&gt;

       &lt;/tr&gt;

     &lt;/tbody&gt;

&lt;/table&gt;

  &lt;div class="paybill"&gt;

@Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").ContentType(ContentType.TextAndImage).PrefixIcon("e-calender")

  &lt;/div&gt;

&lt;/div&gt;

Run the above code example and you can see that it restricts entering a value exceeding the MinValue and MaxValue range mentioned in the numeric textbox.

Set Calculation process with CurrencyTextBox Widgets

You can use events to calculate the total and displays the value. You can achieve this with the help of Click event in the button widget. The calculation steps are written in the call back function of Click event button.

To customize the button, set the ContentType as TextAndImage to include the icon before the text. Add the PrefixIcon value as “e-calender” and add the ClientSideEvents for click event.

&lt;div class="editors"&gt;



@* Please refer the table format for textboxes customization *@

  &lt;div class="paybill"&gt;

   @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").ContentType(ContentType.TextAndImage).PrefixIcon("e-calender").ClientSideEvents(c=>c.Click("calculateBill"))

  &lt;/div&gt;

&lt;/div&gt;



&lt;script type="text/javascript"&gt;   

function calculateBill() {

        // Declares Necessary variable creation 

        var kmcalc, servtax, amuntperkm;

        umcalc = $("#numeric").data("ejNumericTextbox");// Object of Numeric 

        servtax = $("#percent").data("ejPercentageTextbox");// Object of Percentage

        amuntperkm = $("#currency").data("ejCurrencyTextbox"); // Object of Currency

        cusmob = $("#maskedit").data("ejMaskEdit"); // Object of MaskEdit        

        // This is used to calculate the Net amount

        var netamunt = umcalc.model.value * amuntperkm.model.value;

        // This is used to calculate the service tax amount

        var sTax = (netamunt * servtax.model.value) / 100;

        // This shows the calculated amount for the units

        alert("The amount $" + (netamunt + sTax) + " has been sent as message to " + cusmob.model.value + ".");

    }

&lt;/script&gt;

Run the above code sample, fill the required Textbox fields and click the Calculate button. The values are displayed and an alert message is shown. The following screen shot illustrates the final output of the Electricity bill calculator. 

{ ![](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }


