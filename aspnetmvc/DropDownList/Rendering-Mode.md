---
layout: post
title: Rendering Mode in DropDownList control for Syncfusion ASP.NET MVC
description: Describes about rendering mode in DropDownList control for Syncfusion ASP.NET MVC.
platform: mvc
control: DropDownList
documentation: ug
---

# Rendering Mode

DropDownList control can be created using UL-LI element. 

By default DropDownList control is rendered using DropDownList helper to which you can pass popup items using Datasource and DropDownListFields property. 
## Using UL-LI

You can bind the predefined set of UL-LI elements to generate the list of popup items. These items can be customized by adding any images, div elements, radio buttons, text boxes etc.

Create a div with UL-LI elements and assign that div id into TargetID property for rendering the DropDownList control.

{% highlight html %}

	@Html.EJ().DropDownList("DropDownList1").TargetID("mailtoolslist")

	<div id="mailtoolslist">

    	<ul>

        	<li>

            	<div class="mailtools categorize"></div>
            	Categorize and Move</li>
        
        	<li>
            	<div class="mailtools done"></div>
            	Done</li>
        
        	<li>
            
            	<div class="mailtools flag"></div>
            	Flag & Move</li>
        
        	<li>
            
	            <div class="mailtools forward"></div>
    	        Forward</li>
        
	        <li>
            
	            <div class="mailtools movetofolder"></div>
	            Move to Folder</li>
        
	        <li>
            
	            <div class="mailtools newmail"></div>
	            New E-mail</li>
        
	        <li>
            
	            <div class="mailtools meeting"></div>
	            New Meeting</li>
        
	        <li>
            
	            <div class="mailtools reply"></div>
	            Reply & Delete</li>
        
    	</ul>
    
	</div>
	
{% endhighlight %}

{% highlight css %}

    	 .mailtools {
        	display: block;
        	background-image: url('iconsapps.png');
        	height: 25px;
        	width: 25px;
        	background-position: center center;
        	background-repeat: no-repeat;
        
    	}
    
     	.mailtools.done {
	        background-position: 0 0;
        
	    }
    
	     .mailtools.movetofolder {
    	    background-position: 0 -22px;
        
	    }
    
	     .mailtools.categorize {
	        background-position: 0 -46px;
        
	    }
    
	    .mailtools.flag {
    	    background-position: 0 -70px;
        
    	}
    
     	.mailtools.forward {
        	background-position: 0 -94px;
        
    	}
    
     	.mailtools.newmail {
        	background-position: 0 -116px;
        
	    }
    
    	 .mailtools.reply {
        	background-position: 0 -140px;
        
    	}
    
     	.mailtools.meeting {
        	background-position: 0 -164px;
        
    	}    

{% endhighlight %}

{% highlight js %}

    	$(function() {
		
        	$('#dropdown1').ejDropDownList({
			
            	targetID: "mailtoolslist"
				
        	});
			
    	});

{% endhighlight %}


N> Images for this sample are available in (installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\samples\web\themes\images<br/>
	
	
![](RenderingMode_images/RenderingMode_img1.jpeg)

N> Any EJ control can be embedded in the target element but the default action of that control should be prevented in order to create custom actions. To show a sample, integration with TreeView control is demonstrated [here](http://mvc.syncfusion.com/demos/web/dropdownlist/integrationwithwidgets)
