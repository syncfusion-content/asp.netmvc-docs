---
layout: post
title: Responsive Layout | Toolbar | ASP.NET MVC | Syncfusion
description: responsive layout
platform: ejmvc
control: Toolbar
documentation: ug
---

# Responsive Layout

Responsive Layout is aimed at crafting sites to provide an optimal viewing experience—easy reading and navigation with a minimum of resizing, panning, and scrolling—across a wide range of devices (from mobile phones to desktop computer monitors). You can achieve Responsive Layout by using default functionality of Toolbar with IsResponsive as true and also you need to give Toolbar Width as in percentage value and add ej.responsive.css file in this sample. CDN link for the responsive css file is as follows.

[http://cdn.syncfusion.com/13.1.0.21/js/web/responsive-css/ej.responsive.css](http://cdn.syncfusion.com/13.1.0.21/js/web/responsive-css/ej.responsive.css)

Add the above css link in the code sample.        

1. Add the following code example in your HTML page.


{% tabs %}


{% highlight CSHTML %}

<div class="control">

    @Html.EJ().Toolbar("ToolbarItem").Width("65%").Height("33px").IsResponsive(true).Items(s =>

    {

        s.Add().Id("OtherFormat").SpriteCssClass("PdfDocument e-icon convertToOthers ").TooltipText("Convert PDF files to Word or Excel Online…");

        s.Add().Id("PDFOnline").SpriteCssClass("PdfDocument e-icon convertToPdf ").TooltipText("Convert files to PDF Online");

        s.Add().Id("Signature").SpriteCssClass("PdfDocument e-icon signature ").TooltipText("Sign, add text or send a document for signature");

        s.Add().Id("Save").SpriteCssClass("PdfDocument e-icon save ").TooltipText("Save file ( Ctrl+S )");

        s.Add().Id("Print").SpriteCssClass("PdfDocument e-icon print ").TooltipText("Print file ( Ctrl+P )");

        s.Add().Id("Message").SpriteCssClass("PdfDocument e-icon msg ").TooltipText("Message");

    }).Items(s1 =>

    {

        s1.Add().Id("Previous").SpriteCssClass("PdfDocument e-icon previous ").TooltipText("Show previous page ( Left Arrow )");

        s1.Add().Id("Next").SpriteCssClass("PdfDocument e-icon next ").TooltipText("Show next page ( Right Arrow )");

        s1.Add().Id("page").SpriteCssClass("PdfDocument ").ContentTemplate(@<input type="text" value="1" />);

        s1.Add().Id("count").ContentTemplate(@<span>/1</span>);

    }).Items(s2 =>

    {

        s2.Add().Id("ZoomOut").SpriteCssClass("PdfDocument e-icon zoomOut ").TooltipText("Zoom Out");

        s2.Add().Id("ZoomIn").SpriteCssClass("PdfDocument e-icon zoomIn ").TooltipText("Zoom In");

        s2.Add().Id("ZoomValue").SpriteCssClass("PdfDocument ").ContentTemplate(@<div>

            @dropdown()

        </div>);

    }).Items(s3 =>

{

    s3.Add().Id("FitFull").SpriteCssClass("PdfDocument e-icon fitOne ").TooltipText("Fit one full page to window");

    s3.Add().Id("StickyNote").SpriteCssClass("PdfDocument e-icon sticky ").TooltipText("Add stick note ( Ctrl+6 ) ");

    s3.Add().Id("ReadMode").SpriteCssClass("PdfDocument e-icon readMode ").TooltipText("View File in Read Mode");

})

    @helper dropdown()

{

    <div id="percentlist">

        <ul>

            <li>10%</li>

            <li>25%</li>

            <li>50%</li>

            <li>100%</li>

            <li>400%</li>

            <li>800%</li>

            <li>1600%</li>

            <li>3200%</li>

            <li>6400%</li>

        </ul>

    </div>        

    @Html.EJ().DropDownList("selectPercent").Width("90").Value("100%").TargetID("percentlist")

}

</div>

{% endhighlight %}

{% highlight css %}


<style type="text/css" class="cssStyles">

	.e-tooltxt .PdfDocument.e-icon 
	{

		background-image: url('http://js.syncfusion.com/UG/Web/Content/pdf-icon.png');

		background-repeat: no-repeat;

		display: block;

		height: 30px;

		width: 30px;

	}



	.e-tooltxt .PdfDocument.e-icon:hover 
	{

		background-image: url('http://js.syncfusion.com/UG/Web/Content/pdf-icon-white.png');

	}



	.PdfDocument.e-icon.convertToOthers 
	{

		background-position: -349px 0px;

	}



	.PdfDocument.e-icon.convertToPdf 
	{

		background-position: -527px 0px;

	}



	.PdfDocument.e-icon.signature 
	{

		background-position: 2px 0px;

	}



	.PdfDocument.e-icon.save 
	{

		background-position: -87px 0px;

	}



	.PdfDocument.e-icon.msg 
	{

		background-position: -483px 0px;

	}



	.PdfDocument.e-icon.previous 
	{

		background-position: -395px 0px;

	}



	.PdfDocument.e-icon.next 
	{

		background-position: -439px 0px;

	}



	.PdfDocument.e-icon.zoomIn 
	{

		background-position: -175px 0px;

	}



	.PdfDocument.e-icon.zoomOut 
	{

		background-position: -219px 0px;

	}



	.PdfDocument.e-icon.fitOne 
	{

		background-position: -264px 0px;

	}



	.PdfDocument.e-icon.sticky 
	{

		background-position: -131px -1px;

	}



	.PdfDocument.e-icon.readMode 
	{

		background-position: -308px 0px;

	}



	.PdfDocument.e-icon.print 
	{

		background-position: -43px 0px;

	}



	#ZoomValue .PdfDocument 
	{

		width: 90px;

	}



	#page .PdfDocument input 
	{

		text-align: center;

		width: 20px;

		height: 21px;

	}



	#count span 
	{

		width: 30px;

		height: 30px;

		position: relative;

		top: 2px;

		text-align: center;

		vertical-align: middle;

	}

</style>

{% endhighlight %}

{% endtabs %}  

Execute the above code to render the following output.

![](Responsive-Layout_images/Responsive-Layout_img1.png)


