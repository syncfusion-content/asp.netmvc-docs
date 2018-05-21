---
layout: post
title: Methods and Events
description: methods and events in treemap
platform: ejmvc
control: TreeMap
documentation: ug
---

# Methods and Events

## Method

## Refresh()

`refresh()` method is used to reload the treemap with updated values.

#### Returns: void
{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap"))

    <script type="text/javascript">
        $("#treemap").ejTreeMap();
        var treemapObj = $("#treemap").data("ejTreeMap");
        treemapObj.refresh();
    </script>

{% endhighlight %}


## DrillDown()

`drillDown()` method is used to reload the treemap with updated values.

#### Returns: void
{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap"))

    <script type="text/javascript">
        $("#treemap").ejTreeMap();
        var treemapObj = $("#treemap").data("ejTreeMap");
        treemapObj.drillDown();
    </script>

{% endhighlight %}

## Events

## TreeMapItemSelected

`TreeMapItemSelected` event will trigger when treemap item is selected. 

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns selected treeMapItem object.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .TreeMapItemSelected("itemSelected")
    )
    function itemSelected(sender) { 
        // do something
    }

{% endhighlight %}

## DrillStarted

`DrillStarted` event will fire, when the drilldown action is started in the treemap control.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns selected drilled treeMap object.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .DrillStarted("onDrillStarted")
    )
    function onDrillStarted(sender) { 
        // do something
    }

{% endhighlight %}

## DrillDownItemSelected

If the treemap drilldown item is selected, then `DrillDownItemSelected` event will fire.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns selected drilldown treeMap object.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .DrillDownItemSelected("drillDownItemSelected")
    )
    function drillDownItemSelected(sender) { 
        // do something
    }

{% endhighlight %}

## HeaderTemplateRendering

`HeaderTemplateRendering` event will fire before rendering the treemap drilldown header template.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns drilldown header.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .HeaderTemplateRendering("loadTemplate")
    )
    function loadTemplate(sender) { 
        // do something
    }

{% endhighlight %}

## Refreshed

`Refreshed` event will trigger after refreshing the treemap control with updated values.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Refresh and load the treemap.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .Refreshed("onRefreshed")
    )
    function onRefreshed(sender) { 
        // do something
    }

{% endhighlight %}

## TreeMapGroupSelected

`TreeMapGroupSelected` event will fired when the group selection is performed on treemap items.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
           <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns the  selected group of treeMapItems as  object.</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .TreeMapGroupSelected("groupSelected")
    )
    function groupSelected(sender) { 
        // do something
    }

{% endhighlight %}


## ItemRendering

`ItemRendering` event will trigger while rendering each item in treemap.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns each leaf items in treemap</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .ItemRendering("itemRendering")
    )
    function itemRendering(sender) { 
        // do something
    }

{% endhighlight %}

## LegendItemRendering

`LegendItemRendering` event will trigger while rendering each legend item in treemap.

<table class="params">
    <thead>
        <tr>
            <th>Name</th>
            <th>Type</th>
            <th class="last">Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td class="name">{% highlight html %}originalEvent{% endhighlight %}</td>
            <td class="type"><span class="param-type">object</span></td>
            <td class="description last">Returns each legend item in treemap</td>
        </tr>
    </tbody>
</table>

{% highlight CSHTML %}

    @(Html.EJ().TreeMap("treemap")
        .LegendItemRendering("legendItemRendering")
    )
    function legendItemRendering(sender) { 
        // do something
    }

{% endhighlight %}


### Click

`Click` event will trigger while clicking an item in the treemap.



{% highlight CSHTML %}
 
@(Html.EJ().TreeMap("treemap")

.Click("click")

)
 
function click(){
    // Do Something
}

{% endhighlight %}

### DoubleClick

`DoubleClick` event will trigger while double clicking an item in the treemap



{% highlight CSHTML %}
 
@(Html.EJ().TreeMap("treemap")

.DoubleClick("doubleClick")

)

function doubleClick(){
    // Do Something
}

{% endhighlight %}

### RightClick

`RightClick` event will trigger while right clicking an item in the treemap.



{% highlight CSHTML %}
 
@(Html.EJ().TreeMap("treemap")

.RightClick("rightClick")

)
 
function rightClick(){
    // Do Something
}

{% endhighlight %}