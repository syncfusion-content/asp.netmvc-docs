---
layout: post
title: Behavior-Settings
description: behavior settings
platform: ejmvc
control: MaskEdit
documentation: ug
---

## Behavior Settings

Persistence Support

MaskEditTextBox provides state maintenance support. You can maintain the previous changes made in the control after a page loads.

Configure Persistence Support 

1. In the View page add MaskEditTextBox helper, and configure the EnablePersistence property as follows.



[_cshtml]

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").EnablePersistence(true)



Output of MaskEditTextBox with EnablePersistence is as follows. 



2. { ![](Behavior-Settings_images/Behavior-Settings_img1.png) | markdownify }
{:.image }


{ ![](Behavior-Settings_images/Behavior-Settings_img2.png) | markdownify }
{:.image }


Enabled or Disabled

MaskEditTextBox has an option to enable or disable its element. You can set the Enabled property as “False” to enable the Textbox controls.

Configure Enabled or Disabled 

3. In the View page add MaskEditTextBox helper, and configure the Enabled property.



[_cshtml]

@Html.EJ().MaskEdit("mask").Enabled(false).MaskFormat("99-999-99999")



Output when Enabled is “True” and when Enabled is “False”.

4. { ![](Behavior-Settings_images/Behavior-Settings_img3.png) | markdownify }
{:.image }




_Textboxes with enabled as True_

{ ![](Behavior-Settings_images/Behavior-Settings_img4.png) | markdownify }
{:.image }


Adjusting Txtbox Size

MaskEditTextBox size can be modified by using the Height and Width properties. You can customize the size of Textbox by using these properties.

Configure Height and Width 

MaskEditTextBox size can be modified by using the Height and Width properties. 



[_cshtml] @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Width("100").Height("50")

Output of MaskEditTextBox after setting “Height” and “Width” is as follows.

5. { ![](Behavior-Settings_images/Behavior-Settings_img5.png) | markdownify }
{:.image }










_MaskEditTextBox with height and width_

Define Value

The value of MaskEditTextBox can be assigned by using the Value property. The default value for Value property is null.

Configure Value

6. In the View page add MaskEditTextBox helper, and configure the Value property 



[_cshtml]

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("1234567890")





Output of MaskEditTextBox with the value property is as follows.



{ ![](Behavior-Settings_images/Behavior-Settings_img6.png) | markdownify }
{:.image }




_MaskEditTextBox with value_

Read Only Support

MaskEditTextBox supports read only option. When you enable the ReadOnly property to the control, the value cannot be changed in the MaskEditTextBox. You can set the ReadOnly property as “True” to enable this option.

Configure Read Only

In the View page add MaskEditTextBox helper, and configure the ReadOnly property.

7. 

[_cshtml]

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").ReadOnly(true)



Output of MaskEditTextBox when ReadOnly is “True” is as follows. MaskEditTextBox values cannot be edited or changed.



{ ![](Behavior-Settings_images/Behavior-Settings_img7.png) | markdownify }
{:.image }


Error Visibility

The MaskEditTextBox has an option that shows the error value with red colored text. It is used to validate the Mask Edit value. You can set the ShowError property as “True” to enable this option.

Configure Error Visibility

8. In the View page use the corresponding Textbox helperfor rendering Textbox controls. 



[_cshtml]

@* Add the following code in your view page to render Textbox controls.*@

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").ShowError(true)



Output for MaskEditTextBox when ShowError is “True” is as follows. 



{ ![](Behavior-Settings_images/Behavior-Settings_img8.png) | markdownify }
{:.image }




{ ![](Behavior-Settings_images/Behavior-Settings_img9.png) | markdownify }
{:.image }


Mask Edit Properties

Custom Character

The MaskEdit allows you to use the custom character option. The specified character is allowed to enter in the Mask Edit Textbox by using the CustomCharacter property.

Hide Prompt On Leave

The MaskEditTextBox provides the option to hide the prompt when you focus out from the control. The mask prompt is visible when you focus again to the control. The default value of HidePromptOnLeave is false.

Input Mode

The MaskEdit supports two type of inputs such as text and password that have been assigned by using the enum values ej.InputMode.Text and ej.InputMode.Password. The default value for InputMode is text in MaskEdit.

Mask Format

The MaskEdit provides the option to define the MaskFormat to the value. The default value for MaskFormat property is empty string.

The following steps explain the implementation of MaskEdit Properties.

In the View page use the corresponding Textbox helperfor rendering MaskEdit control. 





[_cshtml]

@* Add the following code in your view page to render Textbox controls.*@

@{Html.EJ().MaskEdit("mask")

.MaskFormat("99-999-CCCC").CustomCharacter("r").

HidePromptOnLeave(true).InputMode(InputMode.Text).Render();}





The output for MaskEditTextBox with its properties is as follows.

{ ![](Behavior-Settings_images/Behavior-Settings_img10.png) | markdownify }
{:.image }




{ ![](Behavior-Settings_images/Behavior-Settings_img11.png) | markdownify }
{:.image }




{ ![](Behavior-Settings_images/Behavior-Settings_img12.png) | markdownify }
{:.image }




{ ![](Behavior-Settings_images/Behavior-Settings_img13.png) | markdownify }
{:.image }




{ ![](Behavior-Settings_images/Behavior-Settings_img14.png) | markdownify }
{:.image }


Appearance

Theme

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

CSS Class

The CSS can be customized by using the CssClass in the MaskEditTextBox. You can customize the MaskEditTextBox with CssClass property to appear like your desired control.

Configure CSS Class

9. In the View page add MaskEditTextBox helper, and configure the CssClass property. 



[_cshtml] @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("123456").CssClass("customCss")

1. Customize the CSS properties in custom CSS class.

[CSS]



    &lt;style&gt;

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

    &lt;/style&gt;



The output for MaskEditTextBox after applying CssClass is as follows.



{ ![](Behavior-Settings_images/Behavior-Settings_img15.png) | markdownify }
{:.image }


Rounded Corner Support

MaskEditTextBox provides you with rounded corner support whose appearance is different from normal textbox controls.

Configure Rounded Corner Support

2. In the View page add MaskEditTextBox helper, and configure the ShowRoundedCorner property. 



[_cshtml] 

@Html.EJ().MaskEdit("mask").Value("123456").ShowRoundedCorner(true)

Output of MaskEditTextBox when ShowRoundedCorner is “True”.

{ ![](Behavior-Settings_images/Behavior-Settings_img16.png) | markdownify }
{:.image }


Watr Mark Text Support

The Textboxes provide water mark text support. You can display the initial value in the control by water mark.

Configure Water Mark Text

In the View page use the corresponding Textbox helperfor rendering Textbox controls. 

[_cshtml]

3. @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").WatermarkText("MaskEdit")



Output of MaskEditTextBox when ShowRoundedCorner is “True”.

{ ![](Behavior-Settings_images/Behavior-Settings_img17.png) | markdownify }
{:.image }


Text Alignment Support

The MaskEditTextBox provides text alignment support that allows you to set the alignment of text in the control by using the TextAlign property.

Configure Text Alignment

In the View page use the corresponding MaskEdit helperfor rendering MaskEdit control. 



[_cshtml]

@Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").Value("12345677").TextAlign(TextAlign.Right)



The output for Textboxes when TextAlign is set to “right”.

{ ![](Behavior-Settings_images/Behavior-Settings_img18.png) | markdownify }
{:.image }


HTML Attributes Support

4. The MaskEditTextBox provides support for adding HTML attributes to the component. ‘HtmlAttributes’ property is used to add HTML attributes like, id, class etc.. to the components. We need to use IDictionary<string,object> to specify the HTML attributes. 

Configure HTMLAttributes property

1. In the View page add MaskEditTextBox helper, and configure the HtmlAttributes property. Here we have added the [Access key](http://en.wikipedia.org/wiki/Access_key) attribute. While pressing the “AccessKey” and “J” keys, MaskEditTextBox will gain focus.



[_cshtml]

@{IDictionary<string, object> maskAttribute = new Dictionary<string, object>();

maskAttribute.Add("accesskey", "j");

}



5. @Html.EJ().MaskEdit("mask").MaskFormat("99-999-99999").HtmlAttributes(maskAttribute)



2. Add the following JavaScript code to focus the MaskEditTextBox

[JavaScript]



    &lt;script type="text/javascript"&gt;

    $(function () {

        $(document).on("keydown", function (e) {

            if (e.altKey && e.keyCode === 74) { // j- key code.

                $("#mask").focus();

            }

        });

    });

&lt;/script&gt;

The output for MaskEditTextBox after configuring the HtmlAttributes property

{ ![](Behavior-Settings_images/Behavior-Settings_img19.png) | markdownify }
{:.image }






