---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Captcha
documentation: ug
---

# Getting Started

## Create your first Captcha in ASP.NET MVC

This section enables you to configure the Captcha control in your ASP.NET MVC application and also in learning how to use captcha with auto validation in web forms.

{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


Create Captcha Control

The Captcha is one of the way to prevent dictionary attacks, it basically comes with the random text. The following steps are used to create Captcha control.  

1. You can create an MVC Project and add necessary Dll and script with the given [MVC-Getting Started](http://help.syncfusion.com/ug/js/default.htm) Documentation.
2. Add the following code to the corresponding view page for Captcha rendering.



[CSHTML]

&lt;div&gt;

    @Html.EJ().Captcha("SignUpCaptcha")

&lt;/div&gt;



3. Add the following handler codes to the web.config file for Captcha image rendering.



[web.config]

&lt;!--add the following code in &lt;system.web&gt;-->

 &lt;system.web&gt;

    &lt;httpHandlers&gt;

      &lt;add verb="*" path="captimage.axd" type="Syncfusion.JavaScript.ImageHandler, Syncfusion.EJ, Version=XX.XXXX.X.XX, Culture=neutral, PublicKeyToken=3D67ED1F87D44C89" /&gt;

    &lt;/httpHandlers&gt;

&lt;/system.web&gt;

&lt;!--add the following code in &lt;system.webserver&gt;-->

&lt;system.webserver&gt;    

-----------------------

-----------------------

    &lt;handlers&gt;      

      &lt;add verb="*" path="captimage.axd" name="syncfusion_generatetools" type="Syncfusion.JavaScript.ImageHandler, Syncfusion.EJ, Version=XX.XXXX.X.XX, Culture=neutral, PublicKeyToken=3d67ed1f87d44c89" /&gt;      

    &lt;/handlers&gt;

&lt;/system.webserver&gt;



Note: Version=XX.XXXX.X.X - It will vary depend up on .Net frame work version and Essential studio version you have using. If you are using Essential studio version as-12.3.0.36 and .Net frame work is 4.5 use like following Version=12.3450.0.36





The following screen shot displays the output of the above codes.

{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }


Enable Audio and Refresh 

The Captcha controlsupports captcha in the form of audio and when you click the audio button it readouts the captcha characters. You can achieve this by setting “EnableAudio” property to true. Enable refresh is used to refresh or change the captcha image without full page refresh. This is achieved by adding “EnableRefreshImage” property to true. Also include RequestMapper for refresh support.

1. Add the following code example to view page to render captcha with Audio and Refresh.



[CSHTML]

   &lt;div&gt;        @Html.EJ().Captcha("SignUpCaptcha").EnableAudio(true).EnableRefreshImage(true).RequestMapper("Refresh")

   &lt;/div&gt;



2. Add the following code example to corresponding controller page to render captcha with Audio and Refresh.



[CONTROLLER]



        public ActionResult Refresh(CaptchaParams parameters)

        {

            return parameters.CaptchaActions();

        }





The following screenshot displays the output of the above codes.

{ ![](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }


Auto Validation  

The Captcha supports automatic validation by enabling the property EnableAutoValidation. When you set this property to true, captcha validation is done automatically. When the validation fails, CustomErrorMessage property supports to display the customized error message.

1. Add the following code example to view page for auto validation.



[CSHTML]( CaptchaFeatures)



@using (Html.BeginForm("CaptchaFeatures", "Captcha", FormMethod.Post))

{  

&lt;div class="frame" style="width: 500px"&gt;

        &lt;div class="control" style="width: 560px;"&gt;

            &lt;table class="tableprop"&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        &lt;h2 style="text-align:center"&gt;

                            Sign Up</h2>

                        &lt;br&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        <span class="NodeText">Enter Your Name</span>

                    &lt;/td&gt;

                    &lt;td&gt;

                        &lt;input type="text" name="username" /&gt;

                        @if (!(bool)ViewBag.NameStatus)

                        {<span style="color: red">Invalid Value</span>}

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        <span class="NodeText">Email</span>

                    &lt;/td&gt;

                    &lt;td&gt;

                        &lt;input type="text" name="email" /&gt;

                        @if (!(bool)ViewBag.EmailStatus)

                        {<span style="color: red">Invalid Value</span>}

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        <span class="NodeText">Enter Your Password</span>

                    &lt;/td&gt;

                    &lt;td&gt;

                        &lt;input type="password" name="password" /&gt;

                        @if (!(bool)ViewBag.PasswordStatus)

                        {<span style="color: red">Invalid Password</span>}

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        <span class="NodeText">Re-Enter Your Password</span>

                    &lt;/td&gt;

                    &lt;td&gt;

                        &lt;input type="password" name="repassword" /&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                    &lt;/td&gt;

                    &lt;td&gt;

                        &lt;div&gt;

                            @Html.EJ().Captcha("myCaptcha").EnableRefreshImage(true).EnableAudio(true).EnableAutoValidation(true).RequestMapper("Refresh").CustomErrorMessage("Invalid captcha code entered. Please try again.").TargetButton("submit")

                        &lt;/div&gt;

                        &lt;br /&gt;

                        &lt;br /&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                    &lt;/td&gt;

                    &lt;td&gt;

                        @Html.EJ().Button("submit").Size(ButtonSize.Large).Text("Submit").Type(ButtonType.Submit)

                    &lt;/td&gt;

                &lt;/tr&gt;

            &lt;/table&gt;           

        &lt;/div&gt;

    &lt;/div&gt;       

}





[CSHTML]( CaptchaSuccess)

<div class="frame" style="height: 300px; width: 500px; border: 1px solid gray; padding: 10px;

    background: #f9f9f9">

    &lt;div class="control"&gt;

        &lt;table&gt;

            &lt;tr&gt;

                &lt;td style="padding: 50px;"&gt;

                    &lt;br&gt;

                    &lt;br&gt;

                    &lt;h2&gt;

                        Thank you for registering.&lt;/h2&gt;

                    &lt;br&gt;

                &lt;/td&gt;

            &lt;/tr&gt;

        &lt;/table&gt;

    &lt;/div&gt;

&lt;/div&gt; 



2. Add the following code example to corresponding controller page for captcha with Auto-Validation support.



[CONTROLLER]



        public ActionResult CaptchaFeatures()

        {

            ViewBag.NameStatus = true;

            ViewBag.PasswordStatus = true;

            ViewBag.EmailStatus = true;

            return View();

        }

        [HttpPost]

        public ActionResult CaptchaFeatures(FormCollection Values)

        {

            if (!string.IsNullOrEmpty(Values["username"].ToString()) && (Values["username"].ToString().Length > 3))

                ViewBag.NameStatus = true;

            else

                ViewBag.NameStatus = false;

            if (!string.IsNullOrEmpty(Values["email"].ToString()) && (Values["email"].ToString().Length > 3))

                ViewBag.EmailStatus = true;

            else

                ViewBag.EmailStatus = false;

            if ((!string.IsNullOrEmpty(Values["password"].ToString())) && (Values["password"].ToString().Length > 3) && (Values["password"].ToString().Equals(Values["repassword"].ToString())))

                ViewBag.PasswordStatus = true;

            else

                ViewBag.PasswordStatus = false;

            if ((bool)ViewBag.NameStatus && (bool)ViewBag.PasswordStatus && (bool)ViewBag.EmailStatus)

                return View("CaptchaSuccess");

            else

                return View();

        }



        public ActionResult Refresh(CaptchaParams parameters)

        {

            return parameters.CaptchaActions();

        }



        public ActionResult CaptchaSuccess()

        {

            return View();

        }



The following screenshot is the output for the above code example.

{ ![](Getting-Started_images/Getting-Started_img4.png) | markdownify }
{:.image }


{ ![](Getting-Started_images/Getting-Started_img5.png) | markdownify }
{:.image }


