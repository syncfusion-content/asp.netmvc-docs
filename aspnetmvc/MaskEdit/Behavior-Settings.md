---
layout: post
title: Behavior-Settings
description: behavior settings
platform: ejmvc
control: MaskEdit
documentation: ug
---

# Behavior Settings

## Persistence Support

MaskEditTextBox provides state maintenance support. You can maintain the previous changes made in the control after a page loads.

### Configure Persistence Support 

In the View page add MaskEditTextBox helper, and configure the EnablePersistence property as follows.


{% highlight js %}

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").EnablePersistence(true)

{% endhighlight %}

Output of MaskEditTextBox with EnablePersistence is as follows. 



![](Behavior-Settings_images/Behavior-Settings_img1.png)

_MaskEditTextBox at initial load_

![](Behavior-Settings_images/Behavior-Settings_img2.png)

_MaskEditTextBox after changing the value and after page refresh_

## Enabled or Disabled

MaskEditTextBox has an option to enable or disable its element. You can set the Enabled property as “False” to enable the Textbox controls.

### Configure Enabled or Disabled 

In the View page add MaskEditTextBox helper, and configure the Enabled property.



{% highlight js %}

@Html.EJ().MaskEdit("mask").Enabled(false).MaskFormat("99-999-99999")

{% endhighlight %}

Output when Enabled is “True” and when Enabled is “False”.

![](Behavior-Settings_images/Behavior-Settings_img3.png)

_Textboxes with enabled as True_

![](Behavior-Settings_images/Behavior-Settings_img4.png)

_Textboxes with enabled as False_


## Adjusting Txtbox Size

MaskEditTextBox size can be modified by using the Height and Width properties. You can customize the size of Textbox by using these properties.

### Configure Height and Width 

MaskEditTextBox size can be modified by using the Height and Width properties. 

{% highlight js %}

[_cshtml] @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Width("100").Height("50")

{% endhighlight %}

Output of MaskEditTextBox after setting “Height” and “Width” is as follows.

![](Behavior-Settings_images/Behavior-Settings_img5.png)

_MaskEditTextBox with height and width_

## Define Value

The value of MaskEditTextBox can be assigned by using the Value property. The default value for Value property is null.

### Configure Value

In the View page add MaskEditTextBox helper, and configure the Value property 

{% highlight js %}

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("1234567890")

{% endhighlight %}



Output of MaskEditTextBox with the value property is as follows.


![](Behavior-Settings_images/Behavior-Settings_img6.png)

_MaskEditTextBox with value_

## Read Only Support

MaskEditTextBox supports read only option. When you enable the ReadOnly property to the control, the value cannot be changed in the MaskEditTextBox. You can set the ReadOnly property as “True” to enable this option.

### Configure Read Only

In the View page add MaskEditTextBox helper, and configure the ReadOnly property.

{% highlight js %}

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").ReadOnly(true)

{% endhighlight %}

Output of MaskEditTextBox when ReadOnly is “True” is as follows. MaskEditTextBox values cannot be edited or changed.



![](Behavior-Settings_images/Behavior-Settings_img7.png)

_MaskEditTextBox with readOnly _

## Error Visibility

The MaskEditTextBox has an option that shows the error value with red colored text. It is used to validate the Mask Edit value. You can set the ShowError property as “True” to enable this option.

### Configure Error Visibility

In the View page use the corresponding Textbox helperfor rendering Textbox controls. 



{% highlight js %}

@* Add the following code in your view page to render Textbox controls.*@

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").ShowError(true)

{% endhighlight %}

Output for MaskEditTextBox when ShowError is “True” is as follows. 



![](Behavior-Settings_images/Behavior-Settings_img8.png)

_Textbox with showError_



![](Behavior-Settings_images/Behavior-Settings_img9.png)

_Textbox without error_

## Mask Edit Properties

### Custom Character

The MaskEdit allows you to use the custom character option. The specified character is allowed to enter in the Mask Edit Textbox by using the CustomCharacter property.

### Hide Prompt On Leave

The MaskEditTextBox provides the option to hide the prompt when you focus out from the control. The mask prompt is visible when you focus again to the control. The default value of HidePromptOnLeave is false.

### Input Mode

The MaskEdit supports two type of inputs such as text and password that have been assigned by using the enum values ej.InputMode.Text and ej.InputMode.Password. The default value for InputMode is text in MaskEdit.

### Mask Format

The MaskEdit provides the option to define the MaskFormat to the value. The default value for MaskFormat property is empty string.

The following steps explain the implementation of MaskEdit Properties.

In the View page use the corresponding Textbox helperfor rendering MaskEdit control. 



{% highlight js %}

@* Add the following code in your view page to render Textbox controls.*@

@{Html.EJ().MaskEdit("mask")

.MaskFormat("99-999-CCCC").CustomCharacter("r").

HidePromptOnLeave(true).InputMode(InputMode.Text).Render();}

{% endhighlight %}



The output for MaskEditTextBox with its properties is as follows.

![](Behavior-Settings_images/Behavior-Settings_img10.png)

_MaskEdit with MaskFormat_



![](Behavior-Settings_images/Behavior-Settings_img11.png)

_MaskEdit with HidePromtOnLeave_



![](Behavior-Settings_images/Behavior-Settings_img12.png)

_MaskEdit with prompt focus_



![](Behavior-Settings_images/Behavior-Settings_img13.png)

_MaskEdit with InputMode text_



![](Behavior-Settings_images/Behavior-Settings_img14.png)

_MaskEdit with CustomCharacter_

## Appearance

### Theme

The MaskEditTextBox control’s style and appearance can be controlled based on CSS classes. In order to apply styles to the Textbox control, you need to refer 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. If the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 12 themes support available for Textbox control namely:

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

### CSS Class

The CSS can be customized by using the CssClass in the MaskEditTextBox. You can customize the MaskEditTextBox with CssClass property to appear like your desired control.

#### Configure CSS Class

1. In the View page add MaskEditTextBox helper, and configure the CssClass property. 


   ~~~ css

		@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").CssClass("customCss")

   ~~~
   {:.prettyprint }

2. Customize the CSS properties in custom CSS class.

   ~~~ css



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

   ~~~
   {:.prettyprint }

The output for MaskEditTextBox after applying CssClass is as follows.



![](Behavior-Settings_images/Behavior-Settings_img15.png)

_Textboxes with cssClass_

### Rounded Corner Support

MaskEditTextBox provides you with rounded corner support whose appearance is different from normal textbox controls.

#### Configure Rounded Corner Support

In the View page add MaskEditTextBox helper, and configure the ShowRoundedCorner property. 



{% highlight js %} 

@Html.EJ().MaskEdit("mask").Value("123456").ShowRoundedCorner(true)

Output of MaskEditTextBox when ShowRoundedCorner is “True”.

{% endhighlight %}

![](Behavior-Settings_images/Behavior-Settings_img16.png)

_Textboxes with showRoundedCorner_

### Watr Mark Text Support

The Textboxes provide water mark text support. You can display the initial value in the control by water mark.

#### Configure Water Mark Text

In the View page use the corresponding Textbox helperfor rendering Textbox controls. 

{% highlight js %} 

 @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").WatermarkText("MaskEdit")

{% endhighlight %}

Output of MaskEditTextBox when ShowRoundedCorner is “True”.

![](Behavior-Settings_images/Behavior-Settings_img17.png)

_MaskEditTextBox with watermark text_

### Text Alignment Support

The MaskEditTextBox provides text alignment support that allows you to set the alignment of text in the control by using the TextAlign property.

#### Configure Text Alignment

In the View page use the corresponding MaskEdit helperfor rendering MaskEdit control. 



{% highlight js %}

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("12345677").TextAlign(TextAlign.Right)

{% endhighlight %}

The output for Textboxes when TextAlign is set to “right”.

![](Behavior-Settings_images/Behavior-Settings_img18.png)

_MaskEditTextBox with textAlign_

### HTML Attributes Support

The MaskEditTextBox provides support for adding HTML attributes to the component. ‘HtmlAttributes’ property is used to add HTML attributes like, id, class etc.. to the components. We need to use IDictionary<string,object> to specify the HTML attributes. 

#### Configure HTMLAttributes property

1. In the View page add MaskEditTextBox helper, and configure the HtmlAttributes property. Here we have added the [Access key](http://en.wikipedia.org/wiki/Access_key) attribute. While pressing the “AccessKey” and “J” keys, MaskEditTextBox will gain focus.



   ~~~ html

		@{IDictionary<string, object> maskAttribute = new Dictionary<string, object>();

		maskAttribute.Add("accesskey", "j");

		}
		
		@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").HtmlAttributes(maskAttribute)

   ~~~
   {:.prettyprint }


2. Add the following JavaScript code to focus the MaskEditTextBox

   ~~~ js



			<script type="text/javascript">

			$(function () {

				$(document).on("keydown", function (e) {

					if (e.altKey && e.keyCode === 74) { // j- key code.

						$("#mask").focus();

					}

				});

			});

		</script>

   ~~~
   {:.prettyprint }

The output for MaskEditTextBox after configuring the HtmlAttributes property

![](Behavior-Settings_images/Behavior-Settings_img19.png)

_MaskEditTextBox with focus_





