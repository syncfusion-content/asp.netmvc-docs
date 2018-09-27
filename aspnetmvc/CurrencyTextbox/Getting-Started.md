---
layout: post
title: Getting Started | CurrencyTextBox  | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: CurrencyTextBox
documentation: ug
---

# Getting Started

This section explains briefly about how to create a EJMVC CurrencyTextBox in ASP.NET MVC platform.

## Create your first CurrencyTextBox in MVC

From the following steps you can learn how to create and use CurrencyTextBox in your application. Here we have showcased, a small Electric bill calculator application using EJMVC Editors widgets.The Essential ASP.NET MVC Editors control includes Numeric, Percentage, Currency and MaskEdit textbox controls. This will guide you to use the wide range of Editors functionalities to complete this application. 

![](Getting-Started_images/Getting-Started_img1.png)

Electricity Bill Calculator
{:.caption}

### Create Editors 

ASP.NET MVC Editors renders built-in features like keyboard navigation, min and max range and flexible API’s. 

1. Create a MVC Project and add necessary Dll’s and Scripts. Refer [MVC-Getting Started](https://help.syncfusion.com/aspnetmvc/getting-started#). 
2. Add necessary helper elements to render the Editor components.

   ~~~ html

		<div class="editors">

		<div class="element-text" style="">Electricity Bill Calculator</div>

		<br />

		<table class="editors">

			 <tbody>

				 <tr>

				   <td>

					  <label>Unit meters</label>

				   </td>

				   <td>    @* NumericTextBox creation with watermark text *@

					  @Html.EJ().NumericTextbox("numeric").WatermarkText("Units")

				   </td>

				</tr>

				<tr>

					<td>

					   <label>Service Tax</label>

					</td>

					<td>     @* PercentageTextBox creation with watermark text *@

						 @Html.EJ().PercentageTextbox("percent").WatermarkText("Tax")

					</td>

				</tr>

				<tr>

					 <td>

					   <label>Fare</label>

					</td>

					<td>    @* CurrencyTextBox creation with watermark text *@

						@Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit")

					</td>

				</tr>

				<tr>

					<td>

					   <label>Mobile No</label>

					</td>

					<td>    @* MaskEditTextBox creation with watermark text *@

					   @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number")

					</td>

			   </tr>

			 </tbody></table>

		  <div class="pay-bill">      @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate")

		  </div>

		</div>

   ~~~
 


3. The following styles are added to arrange the Editors.

   ~~~ css

		<style type="text/css" class="cssStyles">

			.element-text

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

			.pay-bill

			{

				margin:15px 0px 10px 208px;

			}

			.editors label

			{

				display: block;

				width: 130px;

			}

		</style>
		
   ~~~
 



4. Execute the code to render Editors as follows

![](Getting-Started_images/Getting-Started_img2.png)

CurrencyTextBox with watermark text
{:.caption}

### Set MinValue, MaxValue and value in CurrencyTextBox

You can set the “MinValue”,“MaxValue” and “Value” in Currency, Percentage and Currency text boxes for maintaining the range in Editors widgets. In this scenario, you have to enter the values between the default ranges and enter the phone number in the MaskEdit widget by using the ”MaskFormat” property. By using DecimalPlaces property for CurrencyTextBox you can get decimal values. The following code example illustrates how to achieve this.

{% highlight html%}

<div class="editors">

<div class="element-text" style="">Electricity Bill Calculator</div>

<br />

<table class="editors">

     <tbody>

         <tr>

           <td>

              <label>Unit meters</label>

           </td>

           <td>    @Html.EJ().NumericTextbox("numeric").WatermarkText("Units").MinValue(1).MaxValue(10000).Value("70")

           </td>

        </tr>

        <tr>

            <td>

               <label>Service Tax</label>

            </td>

            <td>                 @Html.EJ().PercentageTextbox("percent").WatermarkText("Tax").MinValue(5).MaxValue(100).Value("15")

            </td>

        </tr>

        <tr>

             <td>

               <label>Fare</label>

            </td>

            <td>                @Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit").MinValue(0.00).MaxValue(100000.00).Value("350.00").DecimalPlaces(2)

            </td>

        </tr>

        <tr>

            <td>

               <label>Mobile No</label>

            </td>

            <td>

               @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number").MaskFormat("99-999-99999").Value("9090909090")

            </td>

       </tr>

     </tbody>

</table>

  <div class="pay-bill">

    @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate")

  </div>

</div>
{% endhighlight %}

The following screenshot illustrates the output of the above code examples. 

![](Getting-Started_images/Getting-Started_img3.png)

CurrencyTextBox with Min/Max Value ranges
{:.caption}

### Setting the Strict Mode Option

You can set the “StrictMode” option to restrict entering values defined outside the range. The following code example illustrates how to set strict mode option. 

{% highlight html %}
<div class="editors">

<div class="element-text" style="">ElectricityBill Calculator</div><br />

<table class="editors">

     <tbody>

         <tr>

           <td>

              <label>Unit meters</label>

           </td>

           <td>                  @Html.EJ().NumericTextbox("numeric").WatermarkText("Units").MinValue(1).MaxValue(10000).Value("70").EnableStrictMode(true)

           </td>

        </tr>

        <tr>

            <td>

               <label>Service Tax</label>

            </td>

            <td>     

				@Html.EJ().PercentageTextbox("percent").WatermarkText("Tax").MinValue(5).MaxValue(100).Value("15")

            </td>

        </tr>

        <tr>

             <td>

               <label>Fare</label>

            </td>

            <td>   

				@Html.EJ().CurrencyTextbox("currency").WatermarkText("Amount per unit").MinValue(0.00).MaxValue(100000.00).Value("350.00").DecimalPlaces(2)

            </td>

        </tr>

        <tr>

            <td>

               <label>Mobile No</label>

            </td>

            <td>    

               @Html.EJ().MaskEdit("maskedit").WatermarkText("Phone number").MaskFormat("99-999-99999").Value("9090909090")

            </td>

       </tr>

     </tbody>

</table>

  <div class="pay-bill">

		@Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").

  </div>

</div>

{% endhighlight %}

Run the above code example and you can see that it restricts entering a value exceeding the MinValue and MaxValue range mentioned in the Numeric textbox.

### Set Calculation process with CurrencyTextBox Widgets

You can use events to calculate the total and displays the value. You can achieve this with the help of Click event in the button widget. The calculation steps are written in the call back function of Click event button.

To customize the button, you can set the ContentType as TextAndImage to include the icon before the text and add the ClientSideEvents for click event.

{% highlight js %}
<div class="editors">



@* Please refer the table format for textboxes customization *@

  <div class="pay-bill">

   @Html.EJ().Button("btn").Size(ButtonSize.Small).Text("Calculate").ClientSideEvents(c=>c.Click("calculateBill"))

  </div>

</div>



<script type="text/javascript">   

function calculateBill() {

        // Declares Necessary variable creation 

        var unitMeter, serviceTax, amountPerKm;

        unitMeter = $("#numeric").data("ejNumericTextbox");// Object of Numeric 

        serviceTax = $("#percent").data("ejPercentageTextbox");// Object of Percentage

        amountPerKm = $("#currency").data("ejCurrencyTextbox"); // Object of Currency

        mobileNumber = $("#maskedit").data("ejMaskEdit"); // Object of MaskEdit        

        // This is used to calculate the Net amount

        var netAmount = unitMeter.model.value * amountPerKm.model.value;

        // This is used to calculate the service tax amount

        var sTax = (netAmount * serviceTax.model.value) / 100;

        // This shows the calculated amount for the units

        alert("The amount $" + (netAmount + sTax) + " has been sent as message to " + mobileNumber.model.value + ".");

    }

</script>
{% endhighlight %}

Run the above code sample, fill the required Textbox fields and click the Calculate button. The values are displayed and an alert message is shown. The following screen shot illustrates the final output of the Electricity bill calculator. 

![](Getting-Started_images/Getting-Started_img4.png)

Electricity bill calculator with alert
{:.caption}