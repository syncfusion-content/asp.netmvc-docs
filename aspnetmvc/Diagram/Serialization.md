---
layout: post
title: Serialization
description: serialization
platform: ejmvc
control: Diagram
documentation: ug
---

# Serialization

Serialization is the process of saving and loading for state persistence of diagram.

* Save
* Load

## Save and Load

The Diagram is serialized as JSON data while saving and Diagram is loaded from the Serialized JSON data.

The following code illustrates how to save and load diagram.

{% highlight js %}


var diagram = $("#Diagram").ejDiagram("instance");


//Returns Diagram model’s json data

var json= diagram.save();



//Loads the Diagram using saved json data 

diagram.load(json);



{% endhighlight %}



