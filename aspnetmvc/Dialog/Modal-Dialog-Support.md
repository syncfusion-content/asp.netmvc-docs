---
layout: post
title: Modal-Dialog-Support
description: modal dialog support
platform: ejmvc
control: Dialog
documentation: ug
---

## Modal Dialog Support

The modal dialog is used like an alert window that disables the main window and explore its content for the purpose of interacting with others. 

Configure Modal Dialog

The following steps explains you the implementation of modal dialog. 

1. In the VIEW page set a helper element with dialog content for rendering the Dialog control. 





[CSHTML]

// In the CSHTML page add the Dialog widget using helpers and set EnableModal to ‘true’. 





@{Html.EJ().Dialog("dialogLoginForm").Title("Login Form").ContentTemplate(@&lt;div&gt;

            &lt;table&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        User Name

                        &lt;input type="text" id="txtName" class="ejinputtext" style="width: 100%" /&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td&gt;

                        Password

                        &lt;input type="text" id="Text1" class="ejinputtext" style="width: 100%" /&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td align="center"&gt;

                        &lt;input type="button" id="downloadBtn" value="Login" class="e-btn" style="width: 100px; height: 30px" /&gt;

                    &lt;/td&gt;

                &lt;/tr&gt;

                &lt;tr&gt;

                    &lt;td align="center"&gt;

                        <a href="#">Forgot Password</a>

                    &lt;/td&gt;

                &lt;/tr&gt;

            &lt;/table&gt;

        &lt;/div&gt;).Width(250).Height("250").EnableModal(true).Render();}









2. The output of modal dialog control. 

{ ![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/diacenter.PNG](Modal-Dialog-Support_images/Modal-Dialog-Support_img1.png) | markdownify }
{:.image }


_Figure_ _20__: Modal Dialog_

