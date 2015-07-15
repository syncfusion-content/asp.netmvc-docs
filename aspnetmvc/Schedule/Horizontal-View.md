---
layout: post
title: Horizontal-View
description: horizontal view
platform: ejmvc
control: Schedule
documentation: ug
---

## Horizontal View

* You can customize the appearance of the Schedule control by using schedule modes. This can change the view of the schedule. 
* It is possible to change the mode of the schedule. It can be customized by using orientation property.



Orientation

* It defines the orientation type of the Schedule control. It renders the Schedule  either in horizontal mode or vertical mode. By default, orientation property is set as “Vertical”. 
* The valid enum values that are accepted by orientation property are as follows,
1. ej.Schedule.Orientation.Vertical
2. ej.Schedule.Orientation.Horizontal
* You can set the Schedule control to horizontal mode using the following code example.



[Razor]



@*Set Orientation as Horizontal mode *@

@(Html.EJ().Schedule("Schedule1")

.Orientation(Orientation.Horizontal)

)



Execute the above code to render the following output.



{ ![](Horizontal-View_images/Horizontal-View_img1.png) | markdownify }
{:.image }


The above example illustrates the horizontal view of Schedule control. Similarly you can also set the mode of the Schedule as “vertical”.



[Razor]



@*Set Orientation as Vertical mode*@

@(Html.EJ().Schedule("Schedule1")

.Orientation(Orientation.Vertical)

)



Execute the above code to render the following output.

{ ![](Horizontal-View_images/Horizontal-View_img2.png) | markdownify }
{:.image }


Resources

Horizontal Multiple Resources

* Horizontal Multiple Resource feature provides support for rendering multiple resources on the Schedule control. You can group multiple resources under certain categories. You can also save the appointments simultaneously on multiple resources or within the multiple categories using allowMultiple property enabled for different levels of resources.
* Horizontal Multiple Resources is varied from Multiple resources by including the orientation property.It can change the appearance of the Schedule.
* Horizontal view contains another property as resourceHeaderTemplateId. It allows you to render the resource header of the Schedule. When the orientation is in horizontal mode, resourceHeaderTemplateId can be applied.



[Razor]

@(Html.EJ().Schedule("Schedule1")

@*Set horizontal orientation *@

.CurrentView(CurrentView.Month)

.CurrentDate(new DateTime(2014,4,5))

.CellWidth("40px")

.Orientation(Orientation.Horizontal)

@*Setting Resources *@

.Resources(res=> {

res.Field("OwnerId").Title("Owner").Name("Owners").AllowMultiple(true)

.ResourceSettings(flds => flds.Datasource(ViewBag.Owners).Text("text").Id("id").Color("color")).Add();

})

.Group(gr=> {

gr.Resources(ViewBag.Resources);

})

@*Setting Appointments *@

.AppointmentSettings(fields => fields.Datasource(ViewBag.datasource)

.Id("Id")

.Subject("Subject")

.StartTime("StartTime")

.EndTime("EndTime")

.AllDay("AllDay")

.Recurrence("Recurrence")

.RecurrenceRule("RecurrenceRule")

.ResourceFields("OwnerId"))



)



[controller]

// follow the code as same as declared in Resources part



Execute the above code to render the following output.

{ ![](Horizontal-View_images/Horizontal-View_img3.png) | markdownify }
{:.image }


Horizontal Resource Grouping

* The Schedule control supports another important property as group related to the multiple resources that accepts the unique name assigned to each resources in the resource collection. The names that are all listed in this option is grouped in the Schedule control.
* It is possible to change the orientation in horizontal resource grouping. Horizontal view has another one property as resourceHeaderTemplateId. It allows to render the resource header of the schedule. When the orientation is in horizontal mode, resourceHeaderTemplateId can be applied.



[Razor]



@(Html.EJ().Schedule("Schedule1")

@*Set Horizontal orientation *@

.CurrentDate(new DateTime(2014,5,5))

.Orientation(Orientation.Horizontal)

@*Grouping Resources *@

.Resources(res=> {

res.Field("RoomId").Title("Room").Name("Rooms").AllowMultiple(false)

.ResourceSettings(flds => flds.Datasource(ViewBag.Rooms).Text("text").Id("id").Color("color")).Add();

res.Field("OwnerId").Title("Owner").Name("Owners").AllowMultiple(true)

.ResourceSettings(flds => flds.Datasource(ViewBag.Owners).Text("text").Id("id").GroupId("groupId").Color("color")).Add();

})

.Group(gr=> {

gr.Resources(ViewBag.Resources);

})

@*Setting appointments *@

.AppointmentSettings(fields => fields.Datasource(ViewBag.datasource)

.Id("Id")

.Subject("Subject")

.StartTime("StartTime")

.EndTime("EndTime")

.AllDay("AllDay")

.Recurrence("Recurrence")

.RecurrenceRule("RecurrenceRule")

.ResourceFields("RoomId,OwnerId"))



)



[controller]

// follow the code as same as declared in Resource Grouping  part



Execute the above code to render the following output.



{ ![](Horizontal-View_images/Horizontal-View_img4.png) | markdownify }
{:.image }


