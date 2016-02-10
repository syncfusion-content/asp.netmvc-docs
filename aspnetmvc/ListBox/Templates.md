---
layout: post
title: Templates | ListBox | ASP.NET MVC | Syncfusion
description: Templates
platform: ejmvc
control: ListBox
documentation: ug
---

# Templates

The ListBox widget’s appearance can be customized based on different needs using templates. The desired templates can be defined using the “template” property.

In the Model page, define a Class with Text, ImageName, Designation, Country fields. 

In the Controller, create a list of “EmployeeSpecialists” class and add the data.

In the View page add the below codes.

{% tabs %}        
{% highlight c# %}

//define model class with the corresponding property

public class EmployeeSpecialists
    {
        public string Text { get; set; }
        public string ImageName { get; set; }
        public string Designation { get; set; }
        public string Country { get; set; }
    }

//specify desired datasource data by using the model class properties

  public ActionResult Index()
        {
            List<EmployeeSpecialists> empl = new List<EmployeeSpecialists>();
            empl.Add(new EmployeeSpecialists { Text = "Erik Linden", ImageName = "3", Designation = "Representative", Country = "England" });
            empl.Add(new EmployeeSpecialists { Text = "John Linden", ImageName = "6", Designation = "Representative", Country = "Norway" });
            empl.Add(new EmployeeSpecialists { Text = "Louis", ImageName = "7", Designation = "Representative", Country = "Australia" });
            empl.Add(new EmployeeSpecialists { Text = "Lawrence", ImageName = "8", Designation = "Representative", Country = "India" });
            ViewBag.datasource = empl;
            return View();
        }

{% endhighlight %}

{% highlight razor %}

<div class="control">
    @{Html.EJ().ListBox("listboxsample")
    .Datasource((IEnumerable<EmployeeSpecialists>)ViewBag.datasource)
    .Height("238")
    .Width("350")
    .Template("<img class='image' src='../../Content/images/Employees/${ImageName}.png' alt='employee' height='50px' width='50px' /><div class='text'>${Text}</div><div class='desig'>${Designation}</div><div class='country'>${Country}</div>").Render();}
</div>

{% endhighlight %}

{% endtabs %}



 N> In the above code snippet, the image path (Content/images/Employees) is given just for demonstration. Hence the images will not be displayed while using the above code.
 
 
## See Also

[Data Binding](http://help.syncfusion.com/aspnetmvc/listbox/data-binding)

Define the styles for the template as below.

{% highlight css %}

    .image {
        margin: 0;
        padding: 3px 10px 3px 3px;
        border: 0 none;
        width: 60px;
        height: 60px;
        float: left;
    }

    .text {
        font-weight: bold;
        padding: 6px 3px 1px 3px;
    }

    .desig, .country {
        font-size: smaller;
        padding: 3px 3px -1px 0px;
    }




{% endhighlight %}



![ALt text](Templates_images\Templates_img1.png)
