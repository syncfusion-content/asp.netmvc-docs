---
layout: post
title: Validation
description: Validate the date using JQuery
platform: ejmvc
control: DatePicker
documentation: ug
---
# Validation

EJMVC DatePicker  is a form control and therefore its value to be validated before processing. Client side validation provides a better user experience by responding quickly at browser level. Most common client side validation plugin is [JQuery Validation](http://ajax.aspnetcdn.com/ajax/jquery.validate/1.14.0/jquery.validate.min.js). 

DatePicker supports this validation by built-in, so you can do client validation with simple steps to validate and respond validation message. The jQuery validate plugin rules and custom methods can be used in the DatePicker control with the help of two properties,[ValidationRules](http://help.syncfusion.com/js/api/ejdatepicker#members:validationrules) and [ValidationMessage](http://help.syncfusion.com/js/api/ejdatepicker#members:validationmessage). 

Before using those properties, you need to add the jQuery validate plugin to your html page.

Refer the below JQuery validation plugin script after JQuery script reference.

{% highlight cshtml %}

     <script src="http://ajax.aspnetcdn.com/ajax/jquery.validate/1.14.0/jquery.validate.min.js"></script>

{% endhighlight %}



{% highlight cshtml %}

    <!--form to submit-->

     @using (Html.BeginForm())
    {
    //Sets the feild to be required with validation message
    
    @Html.EJ().DatePicker("datepick").ValidationRules(rule => rule.AddRule("requred", true)).ValidationMessage(msg => msg.AddMessage("Requred", "Required Date value"));
    <input type="submit" value="click here!" />
    
    } 


{% endhighlight %}

N>  JQuery validation works only within the form element.
