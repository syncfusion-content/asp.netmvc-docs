---
layout: post
title: State-Maintenance
description: state maintenance
platform: ejmvc
control: Progress Bar
documentation: ug
---

## State Maintenance

Save current model value to cookies for State Maintenance. While refreshing the ProgressBar widget, page retains the model value applied from browser cookies. By default, the ‘EnablePersistence’ property is set to ‘false’ in the ProgressBar.

The following steps explain the State Maintenance in the ProgressBar control.

1. In the VIEW page, add a helper element to render the ProgressBar widget.


{% highlight html %}
// Add the following code example to the corresponding CSHTML page to enable the state maintenance in the ProgressBar control.
@Html.EJ().ProgressBar("progressbar").Value(70).Height("20").Width("500").EnablePersistence(true)
{% endhighlight %}

{% highlight javascript %}
<script>
	var progress;
	$(document).ready(function () {
	progress = $("#progressbar").data("ejProgressBar");
	progress.setModel({ text: progress.getValue() + " %"});
	});
</script>      
{% endhighlight %}




The following screenshot displays the output.

![C:/Users/Gopal Lakshmanan/Desktop/dialog concept and features/propersis.PNG](State-Maintenance_images/State-Maintenance_img1.png)



