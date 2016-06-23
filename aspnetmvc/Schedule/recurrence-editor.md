---
title: Getting started with RecurrenceEditor component and basic render.	 	
description: Rendering a basic Recurrence editor with properties and generate the recurrence rule for Recurrence editor.
platform: ejmvc
control: recurrence editor
documentation: ug
keywords: recurrence editor, recurrence widget, ejRecurrenceEditor, js recurrence editor
---
# Recurrence Editor

The Recurrence Editor includes the entire recurrence related information in a separate portable manner which can be either utilized as a separate widget or else can be embed within the appointment window of Scheduler to enable recurrence options within it. The recurrence rule can be easily generated based on the frequency selected. The customizations such as changing the labels of the recurrence editor is also possible to achieve through its properties. The frequencies available are Never, Daily, Weekly, Monthly, Yearly and Every weekday.

## Getting Started

Follow the steps as mentioned in the [Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) page of the Introduction part to create an MVC application with required assembly references, scripts and stylesheets to render the Recurrence Editor.

Add the basic Recurrence Editor code in the View page as shown below,

{% highlight razor %}

  @(Html.EJ().RecurrenceEditor("RecurrenceEditor")
        .SelectedRecurrenceType(0)  
    )

{% endhighlight %}

## Generating Recurrence Rule

The Recurrence Editor can be used to generate the recurrence rule as a string, based on the repeat options selected.

The following code example depicts the way to generate the recurrence rule.

{% highlight razor %}
        @(Html.EJ().RecurrenceEditor("RecurrenceEditor")
        .SelectedRecurrenceType(2)
        .RecurrenceEditorClientSideEvents(evt=>evt.Create("onCreate"))
        )
{% endhighlight %}

Define a button separately and add it to the page as shown below and while clicking on it, make use of the client-side public method `getRecurrenceRule` of the Recurrence Editor to generate the recurrence rule string explicitly.
        
{% highlight html %}

    <button onclick="closerecurrence()" id="donerecur1" class='recurbutton' style="float:right;margin-right:20px;margin-bottom:10px;">Recurrence String</button>
    
 {% endhighlight %} 
 
 {% highlight js %}
 
     $(function () {         
         $("#donerecur1").ejButton({ width: '155px', height: '35px', showRoundedCorner: true });
         $("#RecurrenceEditor").after($("#donerecur1"));

     });
     function closerecurrence() {
         var obj = $(".e-recurrenceeditor").data("ejRecurrenceEditor")
         obj.getRecurrenceRule(); // recurrence rule gets generated here, as per the options selected in the recurrence editor
         alert(obj._recRule);

     }
     function onCreate() {
         this.element.find("#recurrencetype_wrapper").css("width", "33%");
     }
    
 {% endhighlight %} 


