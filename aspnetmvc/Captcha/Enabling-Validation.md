---
layout: post
title: Enabling-Validation
description: enabling validation
platform: ejmvc
control: Captcha
documentation: ug
---

# Enabling Validation

## Auto Validation

You can validate the Captcha characters by default when you click the submit button without adding any validation code. You can achieve this by enabling EnableAutoValidation propertyto true. By default, this property is set as false. When this property is set as true Captcha renders with textbox.  Here, you can also customize the error message by using CustomErrorMessage property that accepts the string value. 

Next, define the target button that performs validation. You can achieve this by using TargetButton property. The button id that performs the click action should be assigned in TargetButton. 

{{ '![C:/Users/ApoorvahR/Desktop/Note.png](Enabling-Validation_images/Enabling-Validation_img1.png)' | markdownify }}
{:.image }
_Note: To validate the Captcha by default, include RequestMapper. It enables to get or set name for the post action function. The post action function is used to process the captcha values internally such as get values from client side for regeneration of captcha image and validation of the captcha._



The following code example is used to render the Captcha with Auto-Validation support.

1. Add the following code example to the corresponding CSHTML page to render Captcha with Auto-Validation support.
<table>
<tr>
<td>
<br>[CSHTML]  @(Html.EJ().Captcha("captcha").EnableAutoValidation(true).RequestMapper("Refresh").CustomErrorMessage("Invalid captcha code entered. Please try again.").TargetButton ("submit"))<br /><br /><br />    @Html.EJ().Button("submit").Size(ButtonSize.Large).Text("Submit").Type(ButtonType.Submit)</td></tr>
<tr>
<td>
[CS]// Add the following code in controller page for Captcha with Auto-Validation supportpublic ActionResult Refresh(CaptchaParams parameters){    return parameters.CaptchaActions();}</td></tr>
</table>




2. The following screenshot illustrates the Captcha with Auto-Validation support. 

{{ '![C:/Users/ApoorvahR/Desktop/3.png](Enabling-Validation_images/Enabling-Validation_img2.png)' | markdownify }}
{:.image }


## Validation by Method

Validation by method is used when EnableAutoValidation is set as false. Here, you can include TargetButton to validate Captcha. CaptchaService.IsValid() method is used to validate the Captcha. It requires three arguments namely as captcha, textbox, case sensitivity.

The following code example is used to render the Captcha with manual validation.

1. Add the following code example to the corresponding CSHTML page to render Captcha with manual validation support.
<table>
<tr>
<td>
<br>[CSHTML] @using (Html.BeginForm("Default", "Captcha", FormMethod.Post)){    @Html.EJ().Captcha("captcha").TargetButton("submit")<br />    @Html.TextBox("validateText")    @Html.ValidationMessage("myCaptcha")<br /><br />      @(Html.EJ().Button("submit").Size(ButtonSize.Large).Text("Submit")    .Type(ButtonType.Submit))}</td></tr>
<tr>
<td>
[CS]// Add the following code in Controller page for Captcha with manual validation support[HttpPost]        public ActionResult Default(FormCollection Values)        {            if (!CaptchaService.IsValid(Values["captcha"], Values["validateText "], true))                ModelState.AddModelError("mycaptcha", "Invalid characters. Try again!");            return View();        }</td></tr>
</table>


2. The following screenshot illustrates the Captcha with manual validation support. 

{{ '![C:/Users/ApoorvahR/Desktop/1.png](Enabling-Validation_images/Enabling-Validation_img3.png)' | markdownify }}
{:.image }


## Case Sensitive Validation 

Captcha supports to check case sensitivity (Upper case and lower case) of the Captcha characters at the time of validation. You can achieve this by enabling EnableCaseSensitivity propertyto true. By default this value is set as true.

The following code example is used to render the Captcha with Case sensitive validation support.

1. Add the following code example to the corresponding CSHTML page to render Captcha with Case sensitive validation support.
<table>
<tr>
<td>
<br>[CSHTML]   @(Html.EJ().Captcha("captcha").EnableAutoValidation(true).RequestMapper("Refresh").CustomErrorMessage("Invalid captcha code entered. Please try again.").TargetButton("submit ").EnableCaseSensitivity(true))<br /><br /><br />@Html.EJ().Button("submit").Size(ButtonSize.Large).Text("Submit").Type(ButtonType.Submit)</td></tr>
<tr>
<td>
[CS]// Add the following code in controller page for Captcha with case sensitive validation supportpublic ActionResult Refresh(CaptchaParams parameters){   return parameters.CaptchaActions();}</td></tr>
</table>


2. The following screenshot illustrates the Captcha with Case sensitive validation support. 

{{ '![C:/Users/ApoorvahR/Desktop/3.png](Enabling-Validation_images/Enabling-Validation_img4.png)' | markdownify }}
{:.image }


