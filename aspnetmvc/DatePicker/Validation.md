---
layout: post
title: Validation
description: Validate date field value using jQuery
platform: ejmvc
control: DatePicker
documentation: ug
---
# Validation

EJMVC DatePicker provides very cool way to validate the value by custom rules and messages before its get processing. Enhanced APIs and built-in validation support in EJWEB DatePicker provides the quick validation in client side itself which provides the easy customization and better user experience than the validating the values in  server side. Most common client side validation plugin is [jQuery Validation](http://ajax.aspnetcdn.com/ajax/jquery.validate/1.14.0/jquery.validate.min.js). 

DatePicker supports this validation by built-in, so you can do client validation with simple steps to validate and respond validation message. The jQuery validate plugin rules and custom methods can be used in the DatePicker control with the help of two properties,[ValidationRules](http://help.syncfusion.com/js/api/ejdatepicker#members:validationrules) and [ValidationMessage](http://help.syncfusion.com/js/api/ejdatepicker#members:validationmessage). 

Before using those properties, you need to add the jQuery validate plugin to your HTML page.

Refer the below jQuery validation plugin script after jQuery script reference.

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

N>  jQuery validation works only within the form element.
