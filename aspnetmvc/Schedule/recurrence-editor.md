---
title: Getting started with RecurrenceEditor component and basic render.	 	
description: Rendering a basic Recurrence editor with properties and generate the recurrence rule for Recurrence editor.
platform: ejmvc
control: recurrence editor
documentation: ug
keywords: recurrence editor, recurrence widget, ejRecurrenceEditor, js recurrence editor
---
# Recurrence Editor

## Getting Started

To render the RecurrenceEditor control, the following list of external dependencies are needed, 

* [jQuery](http://jquery.com) - 1.7.1 and later versions
* [jsRender](https://github.com/borismoore/jsrender) - to render the templates
* [jQuery.easing](http://gsgd.co.uk/sandbox/jquery/easing) - to support animation effects in the components

The other required internal dependencies are tabulated below,


<table>
<tr>
<th>
File<br/><br/></th><th>
Description/Usage<br/><br/></th></tr>
<tr>
<td>
ej.core.min.js<br/><br/></td><td>
Must be referred always first before using all the JS controls.<br/><br/></td></tr>
<tr>
<td>
ej.globalize.min.js<br/><br/></td><td>
Must be referred to localize any of the JS control's text and content.<br/><br/></td></tr>
<tr>
<td>
ej.recurrenceeditor.min.js<br/><br/></td><td>
Schedule core file<br/><br/></td></tr>
<tr>
<td>
ej.scroller.js<br/><br/>ej.button.min.js<br/><br/>ej.datepicker.min.js<br/><br/>ej.checkbox.min.js<br/><br/>ej.editor.min.js<br/><br/>ej.dropdownlist.min.js<br/><br/>ej.togglebutton.min.js<br/><br/>ej.radiobutton.min.js<br/><br/></td><td>
These files are referred for proper working of the sub-controls used within RecurrenceEditor.<br/><br/></td></tr>
</table>

N> RecurrenceEditor uses one or more sub-controls, therefore refer the `ej.web.all.min.js` (which encapsulates all the `ej` controls and frameworks in a single file) in the application instead of referring all the above specified internal dependencies. 

To get the real appearance of the RecurrenceEditor, the dependent css file `ej.web.all.min.css` (which includes styles of all the widgets) should also needs to be referred.

# Overview

The **EJ Recurrence Editor** is allowed to show the different recurrence type which used in the schedule recurrence appointment creation as a portable. Using this control we can render recurrence editor anywhere in web page and can generate the recurrence rule based on value we selected. In this control, we can change the labels of the recurrence editor also customize the elements and frequencies using the properties
 

**Key Features**

Some of the key features of Scheduler are as follows, 

* **Frequencies** - 6 types of views are available namely Never, Daily, Weekly, Monthly, Yearly, Everyweekday.
* **SelectedRecurrenceType** - Selecting the recurrence types in the recurrence editor. 
* **firstDayOfWeek** - showing the first day in the week of date picker in recurrence editor.

## Basic Rendering the recurrence Editor

The recurrence Editor is an widget which is used the show the different recurrence type. it is used to generate the rule based on which we selected in the recurrence rule. 

Here, the example fo the basic recurrence editor widget.
{% highlight razor %}

  @(Html.EJ().RecurrenceEditor("RecurrenceEditor")
        .SelectedRecurrenceType: 0,  
            )

{% endhighlight %}

## Recurrence Editor for generate the recurrence rule.

The Recurrrence Editor is used to generate the recurrence rule for the scheduler appointment rendering.

The following code example depicts the way to render the recurrence editor and generate the recurrence rule.

{% highlight razor %}
        @(Html.EJ().RecurrenceEditor("RecurrenceEditor")
        .SelectedRecurrenceType(2)
        .RecurrenceEditorClientSideEvents(evt=>evt.Create("onCreate"))
        )
{% endhighlight %}
        
{% highlight html %}

    <div id="customWindow" style="display: none"></div>
    <button type="donerecur" onclick="closerecurence()" id="donerecur1" class='recurbutton' style="float:right;margin-right:20px;margin-bottom:10px;">Recurrence String</button>
    
 {% endhighlight %} 
 
 {% highlight js %}
 
     $(function () {         
         $("#donerecur1").ejButton({ width: '155px', height: '35px', showRoundedCorner: true });
         $("#RecurrenceEditor").after($("#donerecur1"));

     });
     function closerecurence() {
         var obj = $(".e-recurrenceeditor").data("ejRecurrenceEditor")
         obj.closeRecurPublic();
         alert(obj._recRule);

     }
     function onCreate() {
         this.element.find("#recurrencetype_wrapper").css("width", "33%");
     }
    
 {% endhighlight %} 


