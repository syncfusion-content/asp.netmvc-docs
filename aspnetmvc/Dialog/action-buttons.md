---
layout: post
title: Action Buttons | Dialog | ASP.NET MVC | Syncfusion
description: How to enable the Interaction button like “Close”, “Minimize” and etc., in Dialog Widget.
platform: ejmvc
control: Control Name undefined
documentation: ug
keywords : ejdialog, MVC Dialog, EJ MVC Dialog, Dialog ui, web Dialog, ej Dialog, Dialog control, ASP.NET MVC Dialog, ASP MVC Dialog
---

# Action Buttons

The Dialog widget provides the following action buttons.

1. Close

2. Maximize

3. Minimize

4. Pin/Unpin

5. Collapse/Expand

You can display only the necessary buttons in the Dialog widget by configuring the `ActionButtons` property.

{% highlight razor %}


    @{
    List<string> actionButtons = new List<string>();
    actionButtons.Add("close");
    actionButtons.Add("maximize");
    actionButtons.Add("minimize");
    }

    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ActionButtons(actionButtons)
            .ContentTemplate(@<p>This is a Dialog</p>)
            .Render();
    }



{% endhighlight %}



![Action Buttons](action-buttons_images\action-buttons_img1.png)

## Customizing Action Buttons

We can customize the action buttons in dialog widget.

You can add new action button in the dialog widget by configuring the `actionButtonClick` event.

{% highlight razor %}


    @{
    List<string> actionButtons = new List<string>();
    actionButtons.Add("close");
    actionButtons.Add("maximize");
    actionButtons.Add("minimize");
	actionButtons.Add("collapsible");
	actionButtons.Add("pin");
	actionButtons.Add("mediaplay");
	actionButtons.Add("search");
    }

    @{
        Html.EJ()
            .Dialog("dialog")
            .Title("Dialog")
            .ActionButtons(actionButtons)
			.ClientSideEvents(event =>event.ActionButtonClick("playMedia"))
            .ContentTemplate(@<p>This is a Dialog</p>)
            .Render();			
    }

{% endhighlight %}
	

{% highlight javascript %}
          
		  function playMedia(args)
		    {
               console.log(args.buttonID);
            }
		
{% endhighlight %}
      



![Action Buttons](action-buttons_images\action-buttons_img2.png)

