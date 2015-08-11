---
layout: post
title: Modal-Dialog-Support
description: modal dialog support
platform: ejmvc
control: Dialog
documentation: ug
---

# Modal Dialog Support

The modal dialog is used like an alert window that disables the main window and explore its content for the purpose of interacting with others. 

## Configure Modal Dialog

The following steps explains you the implementation of modal dialog. 

1. In the VIEW page set a helper element with dialog content for rendering the Dialog control. 





{% highlight html %}

// In the CSHTML page add the Dialog widget using helpers and set EnableModal to ‘true’. 





@{Html.EJ().Dialog("dialogLoginForm").Title("Login Form").ContentTemplate(@<div>

            <table>

                <tr>

                    <td>

                        User Name

                        <input type="text" id="txtName" class="ejinputtext" style="width: 100%" />

                    </td>

                </tr>

                <tr>

                    <td>

                        Password

                        <input type="text" id="Text1" class="ejinputtext" style="width: 100%" />

                    </td>

                </tr>

                <tr>

                    <td align="center">

                        <input type="button" id="downloadBtn" value="Login" class="e-btn" style="width: 100px; height: 30px" />

                    </td>

                </tr>

                <tr>

                    <td align="center">

                        <a href="#">Forgot Password</a>

                    </td>

                </tr>

            </table>

        </div>).Width(250).Height("250").EnableModal(true).Render();}


{% endhighlight %}






2. The output of modal dialog control. 

![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/diacenter.PNG](Modal-Dialog-Support_images/Modal-Dialog-Support_img1.png)



_Figure20: Modal Dialog_

