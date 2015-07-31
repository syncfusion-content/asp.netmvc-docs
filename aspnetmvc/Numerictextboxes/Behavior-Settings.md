---
layout: post
title: Behavior-Settings
description: behavior settings
platform: ejmvc
control: NumericTextBox
documentation: ug
---

## Behavior Settings

Decimal Places

DecimalPlaces property specifies number of values allowed after the decimal point.The default value of DecimalPlaces property is 0 i.e., by default you cannot specify decimal value in NumericTextBox. We need to add this property to allow decimal values.

Configure Decimal Places

In the View page add NumericTextBox helper, and configure the DecimalPlaces property as shown below.

[_cshtml]



@Html.EJ().NumericTextbox("numeric").DecimalPlaces(3).Value("333")

The output is as follows.



{{ '![](Behavior-Settings_images/Behavior-Settings_img1.png)' | markdownify }}
{:.image }


Persistence Support

NumericTextBox provides state maintenance support. You can maintain the previous changes made in the control after a page loads.

Configure Persistence Support 

In the View page add NumericTextBox helper, and configure the EnablePersistence property as shown below.

[_cshtml]



 @Html.EJ().NumericTextbox("numeric").Value("11").EnablePersistence(true) 



Output of NumericTextBox with EnablePersistence is as follows. 



1. {{ '![](Behavior-Settings_images/Behavior-Settings_img2.png)' | markdownify }}
{:.image }


{{ '![](Behavior-Settings_images/Behavior-Settings_img3.png)' | markdownify }}
{:.image }


Strict Mode Support

NumericTextBox allows you to use the strict mode option by setting the EnableStrictMode property. You can set the MinValue and MaxValue to the controls to enable strict mode functionality. Default value of this property is false. When the textbox value exceeds the MaxValue, it restricts the exceeded value and returns the MaxValue. Likewise when the textbox value goes below MinValue, it restricts the new value and returns the MinValue. When this property is enabled, it will not restrict the specified value and an error class is added to indicate wrong value is provided to the textbox.

Configure Strict Mode Support 

2. In the View page add NumericTextBox helper, and configure the EnableStrictMode property.

[_cshtml]

@Html.EJ().NumericTextbox("numeric").MinValue(-3).MaxValue(5).Value(“10”).EnableStrictMode(true)

Output when EnableStrictMode is “True” is as follows.

{{ '![](Behavior-Settings_images/Behavior-Settings_img4.png)' | markdownify }}
{:.image }


Enabled or Disabled

NumericTextBox has an option to enable or disable its element. You can set the Enabled property as “False” to enable the Textbox controls.

Configure Enabled or Disabled 

3. In the View page add NumericTextBox helper, and configure the Enabled property.



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("1").Enabled(false) 





Output when Enabled is “True” and when Enabled is “False”.



{{ '![](Behavior-Settings_images/Behavior-Settings_img5.png)' | markdownify }}
{:.image }


{{ '![](Behavior-Settings_images/Behavior-Settings_img6.png)' | markdownify }}
{:.image }


Adjusting Textbox Size

NumericTextBox size can be modified by using the Height and Width properties. 

Configure Height and Width 

4. In the View page add NumericTextBox helper, and configure the Height and Width property.



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Width("100").Height("50").Value("1")

 Output of NumericTextBox after setting “Height” and “Width” is as follows.



{{ '![](Behavior-Settings_images/Behavior-Settings_img7.png)' | markdownify }}
{:.image }


Increment Step

The IncrementStep property is used to increase or decrease the amount of value in the Numeric textbox. 

Configure Increment Step

In the View page add NumericTextBox helper, and configure the IncrementStep property.



[_cshtml]

@Html.EJ().NumericTextbox("numeric").IncrementStep(2).Value("1")

Output of Numeric textbox with IncrementStep is as follows.



{{ '![](Behavior-Settings_images/Behavior-Settings_img8.png)' | markdownify }}
{:.image }




{{ '![](Behavior-Settings_images/Behavior-Settings_img9.png)' | markdownify }}
{:.image }


Define Name

When you have placed the NumericTextBox in a form, the Name property is used to send the field value at form submission. The default value of the Name property is null.

Configure Name

5. In the View page add NumericTextBox helper, and configure the Name property.  





[_cshtml]

@Html.EJ().NumericTextbox("numeric").Name("Numeric")

Define Value

The value of NumericTextBox can be assigned by using the Value property. The default value for Value property is null.

Configure Value

6. In the View page add NumericTextBox helper, and configure the Value property.  



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("12")

Output of NumericTextBox with the value property is as follows.

{{ '![](Behavior-Settings_images/Behavior-Settings_img10.png)' | markdownify }}
{:.image }


Define MaxValue and MinValue

MaxValue

The maximum limit value can be assigned to the NumericTextBox by using the MaxValue property. The default value of MaxValue property is 1.7976931348623157e+308. 

MinValue

The minimum limit value can be assigned to the NumericTextBox by using the MinValue property. The default value of MinValue property is -1.7976931348623157e+308.

Configure MaxValue and MinValue

7. In the View page add NumericTextBox helper, and configure the MinValue and MaxValue property.  .  





[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("2").MinValue(-1).MaxValue(2)

Output of NumericTextBox with MaxValue and MinValue is as follows.



{{ '![](Behavior-Settings_images/Behavior-Settings_img11.png)' | markdownify }}
{:.image }




{{ '![](Behavior-Settings_images/Behavior-Settings_img12.png)' | markdownify }}
{:.image }


Read Only Support

NumericTextBox supports read only option. When you enable the ReadOnly property to the control, the value cannot be changed in the NumericTextBox. You can set the ReadOnly property as “True” to enable this option.

Configure Read Only

In the View page add NumericTextBox helper, and configure the ReadOnly property.

[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("1").ReadOnly(true) 

Output of NumericTextBox when ReadOnly is “True” is as follows. NumericTextBox values cannot be edited or changed.

{{ '![](Behavior-Settings_images/Behavior-Settings_img13.png)' | markdownify }}
{:.image }


Appearance

Theme

NumericTextBox control’s style and appearance can be controlled based on CSS classes. In order to apply styles you need to refer 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. If the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available namely:

* default-theme
* flat-azure-dark
* fat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark

CSS Class

The CSS can be customized by using the CssClass in the NumericTextBox. You can customize the NumericTextBox with CssClass property to appear like your desired control.

Configure CSS Class

8. In the View page add NumericTextBox helper, and configure the CssClass property. 



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("1").CssClass("customCss")

1. Customize the CSS properties in custom CSS class.

[CSS]



    <style>

        .customCss .e-box {

            border-color: #9d241b;

        }

        .customCss .e-input {

            background-color: #f6db8d;            

        }

        .customCss .e-select {

            background-color: #ecf6ac;

            border-color: #3c36e7;

        }

    </style>



Output of NumericTextBox after applying CssClass is as follows.

{{ '![](Behavior-Settings_images/Behavior-Settings_img14.png)' | markdownify }}
{:.image }


Rounded Corner Support

NumericTextBox provides you with rounded corner support whose appearance is different from normal textbox controls.

Configure Rounded Corner Support

2. In the View page add NumericTextBox helper, and configure the ShowRoundedCorner property. 



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("1").ShowRoundedCorner(true)

Output of NumericTextBox when ShowRoundedCorner is “True”.

{{ '![](Behavior-Settings_images/Behavior-Settings_img15.png)' | markdownify }}
{:.image }


Spin Button Support

NumericTextBox provides you the option as to whether to display the split button in the widget or remove it from the control by using showSpinButton property.

Configure Spin Button

In the View page add NumericTextBox helper, and configure the ShowSpinButton property. 



[_cshtml]

@Html.EJ().NumericTextbox("numeric").Value("1").ShowSpinButton(false)



Output of NumericTextBox when ShowSpinButton is “False”.

{{ '![](Behavior-Settings_images/Behavior-Settings_img16.png)' | markdownify }}
{:.image }




Water Mark Text Support

The NumericTextBox provide water mark text support. You can display the initial value in the control by water mark.

Configure Water Mark Text

In the View page add NumericTextBox helper, and configure the ShowSpinButton property.



[_cshtml]

@Html.EJ().NumericTextbox("numeric").WatermarkText("Numeric")



Output of NumericTextBox after applying WaterMarkText is as follows.



{{ '![](Behavior-Settings_images/Behavior-Settings_img17.png)' | markdownify }}
{:.image }


