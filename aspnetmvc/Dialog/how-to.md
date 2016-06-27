---
layout: post
title: How To? | Dialog | ASP.NET MVC | Syncfusion
description: How to achieve specific requirements in Dialog widget for Essential ASP.NET MVC
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

# How To?

## Create Multiple Dialogs

Essential Studio for ASP.NET library supports multiple Dialog widgets in the same web page with different contents and different functionalities.

Initialize the Dialog widgets by configuring as below.

{% highlight razor %}


    @{
        Html.EJ()
            .Dialog("firstdialog")
            .Title("Dialog")
            .Width(250)
            .Position(pos => pos.XValue("20px").YValue("20px"))
            .ContentTemplate(@<p>This is a simple dialog</p>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("seconddialog")
            .Title("Window")
            .Width(250)
            .Position(pos => pos.XValue("300px").YValue("20px"))
            .ContentTemplate(@<p>This is a different dialog</p>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("thirddialog")
            .Title("Popup")
            .Width(250)
            .Position(pos => pos.XValue("150px").YValue("150px"))
            .ContentTemplate(@<p>This is an another dialog</p>)
            .Render();
    }



{% endhighlight %}



N> If the position of the dialog is not set as above, all the three dialogs will be overlapped with each other.

![Create Multiple Dialogs](how-to_images\create-multiple-dialogs_img1.png)


## Create Nested Dialog

A Dialog widget can be nested within another Dialog widget.

Create a div element to render the child Dialog widget and use it as a content of parent Dialog widget.

{% highlight razor %}


    @{
        Html.EJ()
            .Button("outerbutton")
            .Text("Open Dialog")
            .Type(ButtonType.Button)
            .ClientSideEvents(evt => evt.Click("openDialog"))
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("outerdialog")
            .Title("Dialog")
            .Width(500)
            .Height(400)
            .ShowOnInit(false)
            .ContentTemplate(@<div>
                @Html.EJ().Button("innerbutton").Text("Open Nested Dialog").ClientSideEvents(evt => evt.Click("openNestedDialog"))
            </div>)
            .Render();
    }

    @{
        Html.EJ()
            .Dialog("seconddialog")
            .Title("Window")
            .Width(400)
            .Height(300)
            .ShowOnInit(false)
            .ContentTemplate(@<p>This is a nested dialog</p>)
            .Render();
    }



{% endhighlight %}


Add the below script to the view page

{% highlight js %}


    <script>
        function openDialog() {
            $("#outerdialog").ejDialog("open");
        }
        function openNestedDialog() {
            $("#seconddialog").ejDialog("open");
        }
    </script>



{% endhighlight %}

## Create a Confirmation Dialog with Footer section

Essential JS library supports Alert Dialog widgets.

Using `ShowFooter` property to render Alert Dialog with Footers in Dialog widget.

Create a Dialog Widget with enabling Footer property.

{% highlight razor %}

    <div class="control">
        @Html.EJ().Button("btnOpen").Size(ButtonSize.Medium).Type(ButtonType.Button).Height("30").Width("150").ClientSideEvents(evt=>evt.Click("onOpen")).Text("Click to open dialog")
        @{Html.EJ().Dialog("basicDialog").Containment(".control").Title("Software Installation Agreement").ContentTemplate(                                        
                 @<div class="cnt">
                    Do you really leave the session?
            </div>).Target(".control").ShowFooter(true).FooterTemplateId("sample").ClientSideEvents(evt => evt.Close("onDialogClose")).Render();
        }

    </div>

	
{% endhighlight %}

Add the following script to close and open the Dialog widget.

{% highlight javascript %}

     $("#btnOpen").hide();
    function onDialogClose(args) {
        $("#btnOpen").show();
    }
    function onOpen() {
        $("#btnOpen").hide();
        $("#basicDialog").ejDialog("open");
	});

{% endhighlight %}

Initialize Footer in Dialog widgets by adding the script section as below.

{% highlight javascript %}

    <script id="sample" type="text/x-jsrender">
	<div class="footerspan" style="float:right">
	
          @Html.EJ().Button("btn1").Size(ButtonSize.Mini).Height("30").Width("70").Text("Ok")
		  
          @Html.EJ().Button("btn2").Size(ButtonSize.Mini).Height("30").Width("70").Text("Cancel")
		  
    </div>
    <div class="condition" style="float:left; margin-left:15px">
      @Html.EJ().CheckBox("check1").Text("Dont ask me this again")
    </div> 
    </script>
 
{% endhighlight %}

![Create Alert Dialog](how-to_images\dialog-footer1.png)

