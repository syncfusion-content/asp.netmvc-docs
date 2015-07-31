---
layout: post
title: Behavior-Settings
description: behavior settings
platform: ejmvc
control: Tab Control
documentation: ug
---

# Behavior Settings

## Close Button

By default, Tab contents are rendered without CloseButton. You can add the CloseButton by setting the ‘ShowCloseButton’ property to ‘true’. When you move cursor over the Tab headers, the CloseButton is displayed.   

The following code example is used to render the Tab widget with CloseButton.

1. Add the following code in your view page for simple Tab creation with CloseButton.



{% highlight html %}

// Add the following code example to the corresponding CSHTML page to render Tab with close button.



<div style="width: 550px">

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               </div>);

           }).ShowCloseButton(true).Render();}

</div>

{% endhighlight %}



2. The following screenshot illustrates the Tab with CloseButton. 

![](Behavior-Settings_images/Behavior-Settings_img1.png)


## Orientation

By default, Tab control renders in horizontal orientation. You can change the Orientation to vertical using the ‘HeaderPosition’ property. Using  this property, you can customize the header by ” Top”,” Bottom”, “Left”, and  “Right”.

The following code example is used to render the sub Tab widget in the vertical orientation. 

1. Add the following code in your view page for Tab orientation.



{% highlight html %}

// Add the following code example to the corresponding CSHTML page to render Tab with customized orientation.

<div style="width: 550px">

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                   .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               </div>);

           }).HeaderPosition(HeaderPosition.Left).Height("220").Render();}

</div>

{% endhighlight %}



2. The following screenshot illustrates the sub Tab with vertical orientation. 

![](Behavior-Settings_images/Behavior-Settings_img2.png)



## State Maintenance

When the page gets refreshed or reloaded, the Tab state is changed (i.e.) the focus is moved to start Tab. You can maintain the state of the Tab by using ‘EnablePersistence’ property. When this property is set to ‘true’, it retains the state. 

The following code example is used to render the Tab widget with state maintenance. 

1. Add the following code in your view page for Tabstatemaintenance.



{% highlight html %}

// Add the following code example to the corresponding CSHTML page to render Tab with state maintenance.

<div style="width: 550px">

    @{Html.EJ().Tab("dishtab").Items(data =>

           {

               data.Add().ID("pizzatype").Text("Pizza Type")

                   .ContentTemplate(@<div>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</div>);

               data.Add().ID("sandwichtype").Text("Sandwich Type")

                    .ContentTemplate(@<div>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.

               </div>);

           }).EnablePersistence(true).Render();}

</div>

{% endhighlight %}



2. The following screenshot illustrates the Tab with Statemaintenance.

![](Behavior-Settings_images/Behavior-Settings_img3.png)



_Figure_ _10__: State before page refresh_



![](Behavior-Settings_images/Behavior-Settings_img4.png)



