---
layout: post
title: Miscellaneous | DateRangePicker | ASP.NET MVC | Syncfusion
description: miscellaneous
platform: ejmvc
control: DateRangePicker
documentation: ug
---

# Allow Editing

Editing in input box can be disabled by setting the false value to **AllowEdit** API. By default this property will be true and we can edit the value in input box.

~~~ cshtml
	
    @Html.EJ().DateRangePicker("DateRange").AllowEdit(false)

   ~~~  

# Enable/Disable

The control can be enabled / disabled using public methods, **enable** or **disable**.

 ~~~ cshtml
	
    @Html.EJ().DateRangePicker("DateRange").Value("05/28/2016-06/27/2016").ClientSideEvents(p => p.Create("Create"))

    <script>
    //Create event triggers after DateRangePicker created successfully.
     function Create() {
            $("#DateRange").ejDateRangePicker('disable');
        } 
    </script>

   ~~~  

## Clear Ranges

To clear the all selection and ranges in a popup we can make use of **clearRanges** method.

~~~ cshtml
    
    @Html.EJ().DateRangePicker("DateRange").ClientSideEvents(c=>c.BeforeClose("Clear"))

    <script>
    //BeforeClose event triggers before closing DateRangePicker popup
    function Clear() {
                $("#DateRange").ejDateRangePicker('clearRanges');
            }

    </script>
~~~

The following screenshot displays the output for the above code.

![](Miscellaneous_images/Miscellaneous.png)

    BeforeClose Event of DateRangePicker
    {:.caption}
