---
layout: post
title: Localization | Diagram | ASP.NET MVC | Syncfusion
description: localization 
platform: ejmvc
control: Diagram
documentation: ug
---

# Localization

* Localization is the process of providing controls in different cultures to help you set your own culture easily. Diagram provides localization support for Context Menu items.
* The Diagram model’s `Locale` property is used to define the culture code. 

The following code illustrates how to provide localization support for Context Menu items.

{% highlight razor %}

@*Initialize diagram control*@
<div>
   @Html.EJ().Diagram("diagram", ViewData["diagramModel"] as Syncfusion.JavaScript.DataVisualization.Models.DiagramProperties)
</div>

// Defines the context menu items with spanish language
ej.datavisualization.Diagram.Locale["es-ES"] = {
	cut: "Corte",
	copy: "Copia",
	paste: "Pasta",
	undo: "Deshacer",
	redo: "Rehacer",
	selectAll: "Seleccionar todo",
	grouping: "Agrupación",
	group: "Grupo",
	ungroup: "Desagrupar",
	order: "Fin",
	bringToFront: "Traer a delante",
	moveForward: "Movimiento adelante",
	sendToBack: "Enviar a espalda",
	sendBackward: "Enviar hacia atrás"
};

{% endhighlight %}

{% highlight c# %}
      DiagramProperties model = new DiagramProperties();

      //Adds nodes and connectors to model
      model.Nodes.Add(new Node()
      {
          Name = "rectangle1",
          OffsetY = 100,
          Labels = new Collection() { 
              new Label(){Text="Rectangle1"}
          }
      });

      model.Nodes.Add(new Node()
      {
          Name = "rectangle2",
          OffsetY = 300,
          Labels = new Collection() { 
              new Label(){ Text="Rectangle2" }
          }
      });

      model.Connectors.Add(new Connector()
      {
          Name = "connector1",
          SourceNode = "rectangle1",
          TargetNode = "rectangle2"
      });

      //Defines the default properties
      model.DefaultSettings.Node = new Node()
      {
          Width = 100,
          Height = 100,
          OffsetX = 100,
          BorderColor = "#1BA0E2",
          FillColor = "darkcyan",
          Labels = new Collection() { new Label() { FontColor = "white" } }
      };

      //Sets the culture
      model.Locale = "es-ES";
      ViewData["diagramModel"] = model;

{% endhighlight %}

![](/aspnetmvc/Diagram/Localization_images/Localization_img1.png)

N> You have to define the textual descriptions of the context menu items for your custom cultures.