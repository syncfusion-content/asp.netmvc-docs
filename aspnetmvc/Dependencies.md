---
layout: post
title: Dependencies | ASP.NET MVC | Syncfusion
description: Dependencies and CDN
platform: ejmvc
control: Common 
documentation: ug
---

# Dependencies

Other than the above specified assemblies, Scripts and StyleSheets are the two essential requirements to render the Syncfusion components. The components mainly relies on the following 3 common libraries –

* jQuery 1.7.1 and later versions
* JsRender
* jQuery.easing

**jsRender** script file is required to render the templates.

**jQuery.easing** script file is required, so as to support the animation effects in the components.

## Scripts

* All the required scripts for rendering a component is available in a minified format in the below specified location, 

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\ JavaScript\assets`

  _**For example**, If you have installed the Essential Studio package within **C:\Program Files(x86)**, then navigate to the below location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets`

* When you navigate to the above location, you can see the folder named **external**, where the common script libraries (like jQuery, jQuery.easing, JsRender and so on) are available and another folder named **scripts** within which the Syncfusion components UI scripts are available in a minified format. You can copy the required scripts from the location depicted below and use it in your application.

  ![](Dependencies_images/Dependencies_img1.jpeg)

## StyleSheet

* The stylesheets required for supporting the theming and styling of the Syncfusion components (both mobile and web) is available in a minified format in the below specified location, 

  `(installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\ JavaScript\assets\css`

  _**For** **example**, If you have installed the Essential Studio package within **C:\Program Files (x86),** then navigate to the below location,_
  `C:\Program Files (x86)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets\css`

* When you navigate to the above location, you can see 2 folders namely **mobile** and **web**. The mobile related CSS files are present within the **mobile** folder and all the CSS files related to web components are availed within the **web** folder. You can copy the required CSS files from the location depicted below and use it in your application.

  ![](Dependencies_images/Dependencies_img2.jpeg)

## EJ Icon Package

The **Essential Studio for JavaScript** provides a set of icons that can be utilized in your application by applying the class names in element. To make it simple and standard, the EJ Icon class names are followed by **“e-icon e-{icon name}“** syntax.  

## How to use EJ icons in your application?

**Step 1:**

To use the icon fonts in your application, you need to maintain the folder structure of the theme files and the corresponding images for icons.

You have to include the common-images folder in the specified theme folder for displaying icons and refer theme files in your application.

**For example**:

“default-theme” folder CSS which contains the “ej.widgets.all.min.css/ej.web.all.min.css” and “ej.theme.min.css” file. The “ej.widgets.core.min.css” file is in the outside of the default theme folder as shown below:

![](IconLibrary_images/themefolder.png)

Theme files are available in the following location:

(Installed location)\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets\css\web\default-theme.


**Step 2:**

The following example showcases to display the EJ Icon by using their corresponding class names.

{% tabs %}
{% highlight html %}

<!doctype html>
<html>
<head>
    <title>Essential Studio for JavaScript : EJ Icon Package</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" charset="utf-8"  />
    <link href="Content/ej/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
</head>
<body>
  <div class="icons">
   <ul>
     <li>
       <div class="e-icon e-search"></div>
     </li>
     <li>
       <div class="e-icon e-settings"></div>
     </li>
     <li>
       <div class="e-icon e-upload"></div>
     </li>
     <li>
       <div class="e-icon e-font"></div>
     </li>
   </ul>
   <ul>
      <li>
        <div class="e-icon e-indent"></div>
      </li>
      <li>
        <div class="e-icon e-outdent"></div>
      </li>
      <li>
        <div class="e-icon e-redo"></div>
      </li>
      <li>
        <div class="e-icon e-undo"></div>
      </li>
     </ul>
  </div>
</body>
</html>

{% endhighlight %}

{% highlight css %}

<style type="text/css" class="cssStyles">
   div.icons li
        {
            display: inline-block;
            vertical-align: middle;
            padding: 20px;
            list-style: none;
           
        }
</style>

{% endhighlight %}
{% endtabs %}

N>  Make sure the CSS file (ej.widgets.all.min.css/ej.web.all.min.css) is referred in your application.

Execute the above code to render the following output.

![](IconLibrary_images/output.png)

**Step 3:**

The complete list of EJ icons are listed in the following table. You have to use the below class names prefix with e- in your application.

  <style type="text/css" class="cssStyles"> 
      table {
          width: 730px;
      } 
      .txt{
	    margin-top: 5px;
        text-align:center;
       }
	  .spriteimage {
         background-image: url('IconLibrary_images/spritesheet.png');			
		 height: 50px;
		 width: 50px;
		 background-repeat: no-repeat;
		 display: block;
         margin: 0 auto;
	   }

	  .spriteimage.shrink {
	      background-position: -13px -6px;
	   }
	  .spriteimage.enlarge {
	      background-position: -576px -389px;
	   }
	  .spriteimage.key {
		  background-position: -859px -830px;
	   }
	  .spriteimage.list {
		  background-position: -489px -54px;
	   }
	  .spriteimage.listnum {
		  background-position: -890px -675px;
	   }

	  .spriteimage.listnum_01 {
            background-position: -213px -885px;
        }
		.spriteimage.indent {
            background-position: -844px -896px;
        }
		.spriteimage.indent_01 {
            background-position: -963px -501px;
        }
		.spriteimage.outdent {
            background-position: -3px -950px;
        }
		.spriteimage.outdent_01 {
            background-position: -76px 3px;
        }
		
		.spriteimage.close {
            background-position: -661px -2px;
			float: none;
			opacity: 3.2;
        }
		.spriteimage.close_01 {
            background-position: 5px -103px;
        }
		.spriteimage.undo {
            background-position: -650px -103px;
        }
		.spriteimage.undo_01 {
            background-position: -337px -159px;
        }
		.spriteimage.redo {
            background-position: -146px -216px;
        }
		
		.spriteimage.redo_01 {
            background-position: -638px -213px;
        }
		.spriteimage.video {
            background-position: -800px -263px;
        }
		.spriteimage.video_01 {
            background-position: -472px -320px;
        }
		.spriteimage.cross {
            background-position: -197px -379px;
        }
		.spriteimage.brush {
            background-position: -754px -380px;
        }
		
		.spriteimage.dcol {
            background-position: 0px -449px;
        }
		.spriteimage.dcol_01 {
            background-position: -218px -495px;
        }
		.spriteimage.drow {
            background-position: -720px -561px;
        }
		.spriteimage.drow_01 {
            background-position: -379px -615px;
        }
		.spriteimage.icolleft {
            background-position: -108px -658px;
        }
		
		.spriteimage.icolleft_01 {
            background-position: -171px -720px;
        }
		.spriteimage.icolleft_02 {
            background-position: -3px -779px;
        }
		.spriteimage.icolright {
            background-position: -652px -775px;
        }
		.spriteimage.icolright_01 {
            background-position: -721px -831px;
        }
		.spriteimage.icolright_02 {
            background-position: -912px 1px;
        }
		
		.spriteimage.irowbelow {
            background-position: -904px -45px;
        }
		.spriteimage.irowbelow_01 {
            background-position: -908px -98px;
        }
		.spriteimage.irowbelow_2 {
            background-position: -910px -157px;
        }
		.spriteimage.irowabove {
            background-position: -66px -47px;
        }
		.spriteimage.irowabove_01 {
            background-position: -910px -213px;
        }
		
		.spriteimage.irowabove_02 {
            background-position: -916px -274px;
        }
		.spriteimage.table {
            background-position: -170px -58px;
        }
		.spriteimage.table_01 {
            background-position: -911px -447px;
        }
		.spriteimage.table_02 {
            background-position: -911px -341px;
        }
		.spriteimage.sigma {
            background-position: -906px -504px;
        }
		
		.spriteimage.sigma_01 {
            background-position: -880px -557px;
        }
		.spriteimage.uppercase {
            background-position: -264px -45px;
        }
		.spriteimage.uppercase_01 {
            background-position: -486px -152px;
        }
		.spriteimage.lowercase {
            background-position: -766px -45px;
        }
		.spriteimage.lowercase_01 {
            background-position: -910px -389px;
        }
		
		.spriteimage.bgcolor {
            background-position: -323px -264px;
        }
		.spriteimage.superscript {
            background-position: -880px -613px
        }
		.spriteimage.superscript_01 {
            background-position: -153px -661px;
        }
		.spriteimage.subscript {
            background-position: 1px -666px;
        }
		.spriteimage.subscript_01 {
            background-position: -432px -724px;
        }
		
		.spriteimage.restore {
            background-position: -915px -837px;
        }
		.spriteimage.upload {
            background-position: -267px -661px;
        }
		.spriteimage.download {
            background-position: -490px -724px;
        }
		.spriteimage.save {
            background-position: -914px -726px;
        }
		.spriteimage.save_01 {
            background-position: -4px -893px;
        }
		
		.spriteimage.save_02 {
            background-position: -61px -893px;
        }
		.spriteimage.mail {
            background-position: -316px -661px;
        }
		.spriteimage.arrowhead-right {
            background-position: -367px -659px;
        }
		.spriteimage.arrowhead-right_01 {
            background-position: -163px -886px;
        }
		.spriteimage.arrowhead-left {
            background-position: -270px -893px;
        }
		
		.spriteimage.arrowhead-left_01 {
            background-position: -314px -886px;
        }
		.spriteimage.arrowhead-up {
            background-position: -365px -896px;
        }
		.spriteimage.arrowhead-down {
            background-position: -407px -888px;
        }
		.spriteimage.arrow-sans-right {
            background-position: -455px -891px;
        }
		.spriteimage.arrow-sans-right_01 {
            background-position: -203px -553px;
        }
		
		.spriteimage.arrow-sans-left {
            background-position: -624px -896px;
        }
		.spriteimage.arrow-sans-left_01 {
            background-position: -673px -888px;
        }
		.spriteimage.arrow-sans-up {
            background-position: -706px -616px;
        }
		.spriteimage.arrow-sans-down {
            background-position: -485px -552px;
        }
		.spriteimage.datetime {
            background-position: -723px -896px;
        }
		
		.spriteimage.datetime_01 {
            background-position: -911px -888px;
        }
		.spriteimage.calendar {
            background-position: -967px 4px;
        }
		.spriteimage.calendar_01 {
            background-position: -963px -51px;
        }
		.spriteimage.calendar-plus {
            background-position: -966px -105px;
        }
		.spriteimage.calendar-edit {
            background-position: -966px -156px;
        }
		
		.spriteimage.chevron-right {
            background-position: -966px -214px;
        }
		.spriteimage.chevron-right_01 {
            background-position: -969px -331px;
        }
		.spriteimage.chevron-right_02 {
            background-position: -969px -267px;
        }
		.spriteimage.chevron-left {
            background-position: -969px -393px;
        }
		.spriteimage.chevron-left_01 {
            background-position: -969px -446px;
        }
		
		.spriteimage.chevron-left_02 {
            background-position: -956px -550px;
        }
		.spriteimage.chevron-up {
            background-position: -756px -608px;
        }
		.spriteimage.chevron-up_01 {
            background-position: -570px -107px;
        }
		.spriteimage.chevron-down {
            background-position: -936px -617px
        }
		.spriteimage.chevron-down_01 {
            background-position: -946px -653px;
        }
		
		.spriteimage.chevron-circle-right {
            background-position: -117px -54px;
        }
		.spriteimage.chevron-circle-left {
            background-position: -313px -53px;
        }
		.spriteimage.font {
            background-position: -968px -715px;
        }
		.spriteimage.strikethrough {
            background-position: -915px -788px;
        }
		.spriteimage.strikethrough_01 {
            background-position: -67px -944px;
        }
		
		.spriteimage.bold {
            background-position: -969px -756px;
        }
		.spriteimage.bold_01 {
            background-position: -969px -892px;
        }
		.spriteimage.italic {
            background-position: -972px -811px;
        }
		.spriteimage.italic_01 {
            background-position: -120px -954px;
        }
		.spriteimage.underline {
            background-position: -178px -944px;
        }
		
		.spriteimage.underline_01 {
            background-position: -228px -951px;
        }
		.spriteimage.reply {
            background-position: -697px -48px;
        }
		.spriteimage.forward {
            background-position: -285px -946px;
        }
		.spriteimage.export {
            background-position: -338px -946px;
        }
		.spriteimage.user {
            background-position: -125px 1px;
        }
		
		.spriteimage.clipboard {
            background-position: -173px 1px;
        }
		.spriteimage.home {
            background-position: -218px 3px;
        }
		.spriteimage.clear {
            background-position: -268px -4px;
        }
		.spriteimage.resize-handle {
            background-position: -325px 4px;
        }
		.spriteimage.link {
            background-position: -385px 9px;
        }
		
		.spriteimage.link_01 {
            background-position: -438px 9px;
        }
		.spriteimage.unlink {
            background-position: -494px 4px;
        }
		.spriteimage.unlink_01 {
            background-position: -548px 11px;
        }
		.spriteimage.external-link {
            background-position: -601px 10px;
        }
		.spriteimage.external-link_01 {
            background-position: -712px 10px;
        }
		
		.spriteimage.clock {
            background-position: -770px 3px;
        }
		.spriteimage.settings {
            background-position: -818px 3px;
        }
		.spriteimage.cut {
            background-position: -219px -45px;
        }
		.spriteimage.cut_01 {
            background-position: -379px -44px;
        }
		.spriteimage.copy {
            background-position: -438px -44px;
        }
		
		.spriteimage.copy_01 {
            background-position: -541px -37px;
        }
		.spriteimage.copy_02 {
            background-position: -594px -45px;
        }
		.spriteimage.paste {
            background-position: -652px -43px;
        }
		.spriteimage.paste_01 {
            background-position: -821px -43px;
        }
		.spriteimage.star {
            background-position: -44px -93px;
        }
		
		.spriteimage.pointer {
            background-position: -96px -104px;
        }
		.spriteimage.sortdirect {
            background-position: -149px -106px;
        }
		.spriteimage.shoppingcart {
            background-position: -196px -103px;
        }
		.spriteimage.shoppingcart_01 {
            background-position: -239px -94px;
        }
		.spriteimage.cursor {
            background-position: -298px -107px;
        }
		
		.spriteimage.warning {
            background-position: -350px -98px;
        }
		.spriteimage.zoom-out {
            background-position: -393px -98px;
        }
		.spriteimage.zoom-out_01 {
            background-position: -455px -98px;
        }
		.spriteimage.zoom-out_02 {
            background-position: -513px -98px;
        }
		.spriteimage.zoom-in {
            background-position: -697px -97px;
        }
		
		.spriteimage.zoom-in_01 {
            background-position: -747px -108px;
        }
		.spriteimage.zoom-in_02 {
            background-position: -800px -108px;
        }
		.spriteimage.arrow-circle-left {
            background-position: -853px -108px;
        }
		.spriteimage.arrow-circle-left_01 {
            background-position: -2px -153px;
        }
		.spriteimage.arrow-circle-left_02 {
            background-position: -63px -153px;
        }
		
		.spriteimage.arrow-circle-right {
            background-position: -116px -153px;
        }
		.spriteimage.arrow-circle-right_01 {
            background-position: -176px -156px;
        }
		.spriteimage.arrow-circle-right_02 {
            background-position: -230px -156px;
        }
		.spriteimage.arrow-circle-up {
            background-position: -281px -167px;
        }
		.spriteimage.arrow-circle-down {
            background-position: -387px -159px;
        }
		
		.spriteimage.edit {
            background-position: -575px -158px;
        }
		.spriteimage.edit_01 {
            background-position: -627px -158px;
        }
		.spriteimage.edit_02 {
            background-position: -435px -158px;
        }
		.spriteimage.edit_03 {
            background-position: -686px -158px;
        }
		.spriteimage.edit_04 {
            background-position: -805px -158px;
        }
		
		.spriteimage.edit_05 {
            background-position: -857px -158px;
        }
		.spriteimage.notification {
            background-position: 5px -211px;
        }
		.spriteimage.notification_01 {
            background-position: -44px -216px;
        }
		.spriteimage.info {
            background-position: -94px -219px;
        }
		.spriteimage.smiley {
            background-position: -196px -210px;
        }
		
		.spriteimage.checkmark {
            background-position: -488px -202px;
        }
		.spriteimage.checkmark_01 {
            background-position: -739px -206px;
        }
		.spriteimage.media-play {
            background-position: -248px -214px;
        }
		.spriteimage.media-pause {
            background-position: -793px -207px;
        }
		.spriteimage.media-eject {
            background-position: -300px -212px;
        }
		
		.spriteimage.media-next {
            background-position: -351px -220px;
        }
		.spriteimage.media-previous {
            background-position: -402px -219px;
        }
		.spriteimage.media-forward {
            background-position: -537px -219px;
        }
		.spriteimage.media-forward_01 {
            background-position: -589px -212px;
        }
		.spriteimage.media-forward_02 {
            background-position: -843px -212px;
        }
		
		.spriteimage.media-forward_03 {
            background-position: -152px -264px;
        }
		.spriteimage.media-forward_04 {
            background-position: -213px -270px;
        }
		.spriteimage.media-backward {
            background-position: -268px -264px;
        }
		.spriteimage.media-backward_01 {
            background-position: -402px -262px;
        }
		.spriteimage.media-backward_02 {
            background-position: -458px -266px;
        }
		
		.spriteimage.media-backward_03 {
            background-position: -514px -266px;
        }
		.spriteimage.media-backward_04 {
            background-position: -642px -266px;
        }
		.spriteimage.play-circle {
            background-position: -692px -277px;
        }
		.spriteimage.full-screen-expand {
            background-position: -745px -263px;
        }
		.spriteimage.full-screen-expand_01 {
            background-position: -1px -317px;
        }
		
		.spriteimage.full-screen-collapse {
            background-position: -59px -317px;
        }
		.spriteimage.full-screen-collapse_01 {
            background-position: -117px -317px;
        }
		.spriteimage.bullets {
            background-position: -855px -277px;
        }
		.spriteimage.bullets_01 {
            background-position: -173px -328px;
        }
		.spriteimage.filter {
            background-position: -230px -335px;
        }
		
		.spriteimage.filter_01 {
            background-position: -283px -324px;
        }
		.spriteimage.filternone {
            background-position: -325px -324px;
        }
		.spriteimage.filternone_01 {
            background-position: -372px -324px;
        }
		.spriteimage.filter-settings {
            background-position: -415px -324px;
        }
		.spriteimage.align-right {
            background-position: -518px -324px;
        }
		
		.spriteimage.align-right_01 {
            background-position: -572px -316px;
        }
		.spriteimage.align-left {
            background-position: -623px -321px;
        }
		.spriteimage.align-left_01 {
            background-position: -752px -321px;
        }
		.spriteimage.align-justify {
            background-position: -802px -321px;
        }
		.spriteimage.align-justify_01 {
            background-position: -850px -325px;
        }
		
		.spriteimage.align-center {
            background-position: 4px -383px;
        }
		.spriteimage.align-center_01 {
            background-position: -47px -383px
        }
		.spriteimage.align-none {
            background-position: -99px -383px;
        }
		.spriteimage.search {
            background-position: -146px -379px;
        }
		.spriteimage.search_01 {
            background-position: -244px -382px;
        }
		
		.spriteimage.image {
            background-position: -296px -385px;
        }
		.spriteimage.image_01 {
            background-position: -358px -375px;
        }
		.spriteimage.plus {
            background-position: -469px -382px;
        }
		.spriteimage.plus_01 {
            background-position: -691px -213px;
        }
		.spriteimage.minus {
            background-position: -521px -373px;
        }
		
		.spriteimage.minus_01 {
            background-position: -860px 13px;
        }
		.spriteimage.code {
            background-position: -421px -377px;
        }
		.spriteimage.code_01 {
            background-position: 4px -264px;
        }
		.spriteimage.code-hexagon {
            background-position: -683px -375px;
        }
		.spriteimage.file-code {
            background-position: -802px -384px;
        }
		
		.spriteimage.file-html {
            background-position: -856px -389px;
        }
		.spriteimage.palette {
            background-position: -101px -433px;
        }
		.spriteimage.reload {
            background-position: -156px -438px;
        }
		.spriteimage.delete {
            background-position: -623px -377px;
        }
		.spriteimage.delete_01 {
            background-position: -206px -438px;
        }
		
		.spriteimage.delete_02 {
            background-position: -356px -442px;
        }
		.spriteimage.delete_03 {
            background-position: -405px -442px;
        }
		.spriteimage.delete_04 {
            background-position: -458px -439px;
        }
		.spriteimage.delete_05 {
            background-position: -507px -443px;
        }
		.spriteimage.pin {
            background-position: -554px -445px;
        }
		
		.spriteimage.unpin {
            background-position: -601px -439px;
        }
		.spriteimage.stop {
            background-position: -653px -439px;
        }
		.spriteimage.power-cord {
            background-position: -698px -443px;
        }
		.spriteimage.fullborders {
            background-position: -853px -443px;
        }
		.spriteimage.threed {
            background-position: 2px -503px;
        }
		
		.spriteimage.file-excel {
            background-position: -52px -499px;
        }
		.spriteimage.file-text {
            background-position: -755px -441px;
        }
		.spriteimage.file-text_01 {
            background-position: -94px -499px;
        }
		.spriteimage.file-mdx {
            background-position: -159px -497px;
        }
		.spriteimage.file-empty {
            background-position: -270px -499px;
        }
		
		.spriteimage.file-list {
            background-position: -329px -503px;
        }
		.spriteimage.file-delete_01 {
            background-position: -383px -502px;
        }
		.spriteimage.file-settings {
            background-position: -432px -503px;
        }
		.spriteimage.circle-square {
            background-position: -485px -496px;
        }
		.spriteimage.diagonal-square {
            background-position: -543px -493px;
        }
		
		.spriteimage.hexagon-square {
            background-position: -603px -496px;
        }
		.spriteimage.pentagon-square {
            background-position: -659px -496px;
        }
		.spriteimage.globe {
            background-position: -811px -502px;
        }
		.spriteimage.globe_01 {
            background-position: -151px -557px;
        }
		.spriteimage.vertical-barchart {
            background-position: -773px -550px;
        }
		
		.spriteimage.vertical-barchart_01 {
            background-position: -826px -550px;
        }
		.spriteimage.horizontal-barchart {
            background-position: 2px -605px;
        }
		.spriteimage.horizontal-barchart_01 {
            background-position: -50px -603px;
        }
		.spriteimage.pie-chart {
            background-position: -101px -617px;
        }
		.spriteimage.triangle {
            background-position: -153px -617px;
        }
		
		.spriteimage.inverted-triangle {
            background-position: -210px -600px;
        }
		.spriteimage.pyramid {
            background-position: -268px -612px;
        }
		.spriteimage.inverted-pyramid {
            background-position: -857px -494px;
        }
		.spriteimage.comments {
            background-position: -323px -613px;
        }
		.spriteimage.folder {
            background-position: -272px -555px;
        }
		
		.spriteimage.folder_01 {
            background-position: -432px -600px;
        }
		.spriteimage.folder-open {
            background-position: -488px -600px;
        }
		.spriteimage.folder-open_01 {
            background-position: -539px -600px;
        }
		.spriteimage.folder-add {
            background-position: -601px -600px;
        }
		.spriteimage.signal {
            background-position: -657px -600px;
        }
		
		.spriteimage.sort-alpha-desc {
            background-position: -820px -600px;
        }
		.spriteimage.sort-alpha-desc_01 {
            background-position: -50px -661px;
        }
		.spriteimage.sort-alpha-asc {
            background-position: -437px -668px;
        }
		.spriteimage.sort-alpha-asc_01 {
            background-position: -492px -661px;
        }
		.spriteimage.print {
            background-position: -212px -668px;
        }
		
		.spriteimage.print_01 {
            background-position: -551px -661px;
        }
		.spriteimage.print_02 {
            background-position: -607px -661px;
        }
		.spriteimage.print_03 {
            background-position: -664px -661px;
        }
		.spriteimage.word {
            background-position: -721px -661px;
        }
		.spriteimage.word_01 {
            background-position: -771px -661px;
        }
		
		.spriteimage.word-export {
            background-position: -827px -661px;
        }
		.spriteimage.pdf {
            background-position: -2px -722px;
        }
		.spriteimage.pdf_01 {
            background-position: -53px -722px;
        }
		.spriteimage.pdf-export {
            background-position: -106px -722px;
        }
		.spriteimage.excel {
            background-position: -226px -714px;
        }
		
		.spriteimage.excel_01 {
            background-position: -284px -733px;
        }
		.spriteimage.excel-export {
            background-position: -338px -724px;
        }
		.spriteimage.powerpoint-export {
            background-position: -548px -718px;
        }
		.spriteimage.ie {
            background-position: -604px -727px;
        }
		.spriteimage.exit {
            background-position: -661px -728px;
        }
		
		.spriteimage.document {
            background-position: -713px -723px;
        }
		.spriteimage.documents {
            background-position: -766px -723px;
        }
		.spriteimage.question {
            background-position: -381px -719px;
        }
		.spriteimage.film {
            background-position: -818px -723px;
        }
		.spriteimage.volume-up {
            background-position: -60px -775px;
        }
		
		.spriteimage.circle-one {
            background-position: -120px -782px;
        }
		.spriteimage.circle-two {
            background-position: -174px -782px;
        }
		.spriteimage.circle-three {
            background-position: -337px -782px;
        }
		.spriteimage.circle-four {
            background-position: -393px -782px;
        }
		.spriteimage.arrow-right {
            background-position: -449px -782px;
        }
		
		.spriteimage.arrow-left {
            background-position: -501px -782px;
        }
		.spriteimage.arrow-left_01 {
            background-position: -559px -782px;
        }
		.spriteimage.arrow-up {
            background-position: -231px -782px;
        }
		.spriteimage.arrow-down {
            background-position: -607px -782px;
        }
		.spriteimage.arrow-down_01 {
            background-position: -252px -442px;
        }
		
		.spriteimage.sync {
            background-position: -711px -782px;
        }
		.spriteimage.sync-disabled {
            background-position: -759px -782px;
        }
		.spriteimage.paperclip {
            background-position: -808px -782px;
        }
		.spriteimage.paperclip_01 {
            background-position: -58px -837px;
        }
		.spriteimage.circle {
            background-position: -857px -782px;
        }
		
		.spriteimage.circle_01 {
            background-position: -233px -833px;
        }
		.spriteimage.th-list {
            background-position: -448px -832px;
        }
		.spriteimage.th-large {
            background-position: -657px -829px;
        }
		.spriteimage.th {
            background-position: -111px -838px;
        }
		.spriteimage.th-small {
            background-position: -506px -838px;
        }
		
		.spriteimage.view-details {
            background-position: -558px -849px;
        }
		.spriteimage.file-resize-four-direction {
            background-position: -781px -837px;
        }
		.spriteimage.file-resize-horizontal {
            background-position: -281px -833px;
        }
	
</style>  
<table>
<tr>
<td>
<div class="spriteimage shrink"></div>
 <div class="txt">shrink</div>
</td>
<td>
<div class="spriteimage enlarge"></div>
<div class="txt">enlarge</div>
</td>
<td>
<div class="spriteimage key"></div>
<div class="txt">key</div>
</td>
<td>
<div class="spriteimage list"></div>
<div class="txt">list</div>
</td>
<td>
<div class="spriteimage listnum"></div>
<div class="txt">list-numbered</div>
</td>
</tr>

 <tr>
<td>
 <div class="spriteimage listnum_01"></div>
<div class="txt">list-numbered_01</div>
</td>
<td>
<div class="spriteimage indent"></div>
<div class="txt">indent</div>
 </td>
 <td>
<div class="spriteimage indent_01"></div>
<div class="txt">indent_01</div>
</td>
<td>
<div class="spriteimage outdent"></div>
<div class="txt">outdent</div>
</td>
<td>
<div class="spriteimage outdent_01"></div>
<div class="txt">outdent_01</div>
</td>
</tr>

<tr>
 <td>
<div class="spriteimage close"></div>
<div class="txt">close</div>
</td>
<td>
<div class="spriteimage close_01"></div>
<div class="txt">close_01</div>
</td>
<td>
<div class="spriteimage undo"></div>
<div class="txt">undo</div>
</td>
<td>
<div class="spriteimage undo_01"></div>
<div class="txt">undo_01</div>
</td>
<td>
<div class="spriteimage redo"></div>
<div class="txt">redo</div>
</td>	
</tr>

<tr>
<td>
<div class="spriteimage redo_01"></div>
<div class="txt">redo_01</div>
</td>
<td>
<div class="spriteimage video"></div>
<div class="txt">video</div>
</td>
<td>
<div class="spriteimage video_01"></div>
<div class="txt">video_01</div>
</td>
<td>
<div class="spriteimage cross"></div>
<div class="txt">cross-circle</div>
</td>
<td>
<div class="spriteimage brush"></div>
<div class="txt">clean-brush</div>
</td>
</tr> 

<tr>
 <td>
<div class="spriteimage dcol"></div>
<div class="txt">delete-column</div>
</td>
 <td>
<div class="spriteimage dcol_01"></div>
<div class="txt">delete-column_01</div>
</td>
 <td>
<div class="spriteimage drow"></div>
<div class="txt">delete-row</div>
</td>
 <td>
<div class="spriteimage drow_01"></div>
<div class="txt">delete-row_01</div>
</td>
 <td>
<div class="spriteimage icolleft"></div>
<div class="txt">insert-column-left</div>
</td>
</tr>

<tr>
 <td>
<div class="spriteimage icolleft_01"></div>
<div class="txt">insert-column-left_01</div>
</td>
 <td>
<div class="spriteimage icolleft_02"></div>
<div class="txt">insert-column-left_02</div>
</td>
 <td>
<div class="spriteimage icolright"></div>
<div class="txt">insert-column-right</div>
</td>
 <td>
<div class="spriteimage icolright_01"></div>
<div class="txt">insert-column-right_01</div>
</td>
 <td>
<div class="spriteimage icolright_02"></div>
<div class="txt">insert-column-right_02</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage irowbelow"></div>
<div class="txt">insert-row-below</div>
</td>
<td>
<div class="spriteimage irowbelow_01"></div>
<div class="txt">insert-row-below_01</div>
</td>
<td>
<div class="spriteimage irowbelow_2"></div>
<div class="txt">insert-row-below_02</div>
</td>
<td>
<div class="spriteimage irowabove"></div>
<div class="txt">insert-row-above</div>
</td>
<td>
<div class="spriteimage irowabove_01"></div>
<div class="txt">insert-row-above_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage irowabove_02"></div>
<div class="txt">insert-row-above_02</div>
</td>
<td>
<div class="spriteimage table"></div>
<div class="txt">table</div>
</td>
<td>
<div class="spriteimage table_01"></div>
<div class="txt">table_01</div>
</td>
<td>
<div class="spriteimage table_02"></div>
<div class="txt">table_02</div>
</td>
<td>
<div class="spriteimage sigma"></div>
<div class="txt">sigma</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage sigma_01"></div>
<div class="txt">sigma_01</div>
</td>
<td>
<div class="spriteimage uppercase"></div>
<div class="txt">uppercase</div>
</td>
<td>
<div class="spriteimage uppercase_01"></div>
<div class="txt">uppercase_01</div>
</td>
<td>
<div class="spriteimage lowercase"></div>
<div class="txt">lowercase</div>
</td>
<td>
<div class="spriteimage lowercase_01"></div>
<div class="txt">lowercase_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage bgcolor"></div>
<div class="txt">background-color</div>
</td>
<td>
<div class="spriteimage superscript"></div>
<div class="txt">superscript</div>
</td>
<td>
<div class="spriteimage superscript_01"></div>
<div class="txt">superscript_01</div>
</td>
<td>
<div class="spriteimage subscript"></div>
<div class="txt">subscript</div>
</td>
<td>
<div class="spriteimage subscript_01"></div>
<div class="txt">subscript_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage restore"></div>
<div class="txt">restore</div>
</td>
<td>
<div class="spriteimage upload"></div>
<div class="txt">upload</div>
</td>
<td>
<div class="spriteimage download"></div>
<div class="txt">download</div>
</td>
<td>
<div class="spriteimage save"></div>
<div class="txt">save</div>
</td>
<td>
<div class="spriteimage save_01"></div>
<div class="txt">save_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage save_02"></div>
<div class="txt">save_02</div>
</td>
<td>
<div class="spriteimage mail"></div>
<div class="txt">mail/message</div>
</td>
<td>
<div class="spriteimage arrowhead-right"></div>
<div class="txt">arrowhead-right</div>
</td>
<td>
<div class="spriteimage arrowhead-right_01"></div>
<div class="txt">arrowhead-right_01</div>
</td>
<td>
<div class="spriteimage arrowhead-left"></div>
<div class="txt">arrowhead-left</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage arrowhead-left_01"></div>
<div class="txt">arrowhead-left_01</div>
</td>
<td>
<div class="spriteimage arrowhead-up"></div>
<div class="txt">arrowhead-up</div>
</td>
<td>
<div class="spriteimage arrowhead-down"></div>
<div class="txt">arrowhead-down</div>
</td>
<td>
<div class="spriteimage arrow-sans-right"></div>
<div class="txt">arrow-sans-right</div>
</td>
<td>
<div class="spriteimage arrow-sans-right_01"></div>
<div class="txt">arrow-sans-right_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage arrow-sans-left"></div>
<div class="txt">arrow-sans-left</div>
</td>
<td>
<div class="spriteimage arrow-sans-left_01"></div>
<div class="txt">arrow-sans-left_01</div>
</td>
<td>
<div class="spriteimage arrow-sans-up"></div>
<div class="txt">arrow-sans-up</div>
</td>
<td>
<div class="spriteimage arrow-sans-down"></div>
<div class="txt">arrow-sans-down</div>
</td>
<td>
<div class="spriteimage datetime"></div>
<div class="txt">datetime</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage datetime_01"></div>
<div class="txt">datetime_01</div>
</td>
<td>
<div class="spriteimage calendar"></div>
<div class="txt">calendar</div>
</td>
<td>
<div class="spriteimage calendar_01"></div>
<div class="txt">calendar_01</div>
</td>
<td>
<div class="spriteimage calendar-plus"></div>
<div class="txt">calendar-plus</div>
</td>
<td>
<div class="spriteimage calendar-edit"></div>
<div class="txt">calendar-edit</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage chevron-right"></div>
<div class="txt">chevron-right</div>
</td>
<td>
<div class="spriteimage chevron-right_01"></div>
<div class="txt">chevron-right_01</div>
</td>
<td>
<div class="spriteimage chevron-right_02"></div>
<div class="txt">chevron-right_02</div>
</td>
<td>
<div class="spriteimage chevron-left"></div>
<div class="txt">chevron-left</div>
</td>
<td>
<div class="spriteimage chevron-left_01"></div>
<div class="txt">chevron-left_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage chevron-left_02"></div>
<div class="txt">chevron-left_02</div>
</td>
<td>
<div class="spriteimage chevron-up"></div>
<div class="txt">chevron-up</div>
</td>
<td>
<div class="spriteimage chevron-up_01"></div>
<div class="txt">chevron-up_01</div>
</td>
<td>
<div class="spriteimage chevron-down"></div>
<div class="txt">chevron-down</div>
</td>
<td>
<div class="spriteimage chevron-down_01"></div>
<div class="txt">chevron-down_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage chevron-circle-right"></div>
<div class="txt">chevron-circle-right</div>
</td>
<td>
<div class="spriteimage chevron-circle-left"></div>
<div class="txt">chevron-circle-left</div>
</td>
<td>
<div class="spriteimage font"></div>
<div class="txt">font</div>
</td>
<td>
<div class="spriteimage strikethrough"></div>
<div class="txt">strikethrough</div>
</td>
<td>
<div class="spriteimage strikethrough_01"></div>
<div class="txt">strikethrough_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage bold"></div>
<div class="txt">bold</div>
</td>
<td>
<div class="spriteimage bold_01"></div>
<div class="txt">bold_01</div>
</td>
<td>
<div class="spriteimage italic"></div>
<div class="txt">italic</div>
</td>
<td>
<div class="spriteimage italic_01"></div>
<div class="txt">italic_01</div>
</td>
<td>
<div class="spriteimage underline"></div>
<div class="txt">underline</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage underline_01"></div>
<div class="txt">underline_01</div>
</td>
<td>
<div class="spriteimage reply"></div>
<div class="txt">reply</div>
</td>
<td>
<div class="spriteimage forward"></div>
<div class="txt">forward</div>
</td>
<td>
<div class="spriteimage export"></div>
<div class="txt">export</div>
</td>
<td>
<div class="spriteimage user"></div>
<div class="txt">user</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage clipboard"></div>
<div class="txt">clipboard</div>
</td>
<td>
<div class="spriteimage home"></div>
<div class="txt">home</div>
</td>
<td>
<div class="spriteimage clear"></div>
<div class="txt">clear</div>
</td>
<td>
<div class="spriteimage resize-handle"></div>
<div class="txt">resize-handle</div>
</td>
<td>
<div class="spriteimage link"></div>
<div class="txt">link</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage link_01"></div>
<div class="txt">link_01</div>
</td>
<td>
<div class="spriteimage unlink"></div>
<div class="txt">unlink</div>
</td>
<td>
<div class="spriteimage unlink_01"></div>
<div class="txt">unlink_01</div>
</td>
<td>
<div class="spriteimage external-link"></div>
<div class="txt">external-link</div>
</td>
<td>
<div class="spriteimage external-link_01"></div>
<div class="txt">external-link_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage clock"></div>
<div class="txt">clock</div>
</td>
<td>
<div class="spriteimage settings"></div>
<div class="txt">settings</div>
</td>
<td>
<div class="spriteimage cut"></div>
<div class="txt">cut</div>
</td>
<td>
<div class="spriteimage cut_01"></div>
<div class="txt">cut_01</div>
</td>
<td>
<div class="spriteimage copy"></div>
<div class="txt">copy</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage copy_01"></div>
<div class="txt">copy_01</div>
</td>
<td>
<div class="spriteimage copy_02"></div>
<div class="txt">copy_02</div>
</td>
<td>
<div class="spriteimage paste"></div>
<div class="txt">paste</div>
</td>
<td>
<div class="spriteimage paste_01"></div>
<div class="txt">paste_01</div>
</td>
<td>
<div class="spriteimage star"></div>
<div class="txt">star</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage pointer"></div>
<div class="txt">pointer</div>
</td>
<td>
<div class="spriteimage sortdirect"></div>
<div class="txt">sortdirect</div>
</td>
<td>
<div class="spriteimage shoppingcart"></div>
<div class="txt">shoppingcart</div>
</td>
<td>
<div class="spriteimage shoppingcart_01"></div>
<div class="txt">shoppingcart_01</div>
</td>
<td>
<div class="spriteimage cursor"></div>
<div class="txt">cursor</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage warning"></div>
<div class="txt">warning</div>
</td>
<td>
<div class="spriteimage zoom-out"></div>
<div class="txt">zoom-out</div>
</td>
<td>
<div class="spriteimage zoom-out_01"></div>
<div class="txt">zoom-out_01</div>
</td>
<td>
<div class="spriteimage zoom-out_02"></div>
<div class="txt">zoom-out_02</div>
</td>
<td>
<div class="spriteimage zoom-in"></div>
<div class="txt">zoom-in</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage zoom-in_01"></div>
<div class="txt">zoom-in_01</div>
</td>
<td>
<div class="spriteimage zoom-in_02"></div>
<div class="txt">zoom-in_02</div>
</td>
<td>
<div class="spriteimage arrow-circle-left"></div>
<div class="txt">arrow-circle-left</div>
</td>
<td>
<div class="spriteimage arrow-circle-left_01"></div>
<div class="txt">arrow-circle-left_01</div>
</td>
<td>
<div class="spriteimage arrow-circle-left_02"></div>
<div class="txt">arrow-circle-left_02</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage arrow-circle-right"></div>
<div class="txt">arrow-circle-right</div>
</td>
<td>
<div class="spriteimage arrow-circle-right_01"></div>
<div class="txt">arrow-circle-right_01</div>
</td>
<td>
<div class="spriteimage arrow-circle-right_02"></div>
<div class="txt">arrow-circle-right_02</div>
</td>
<td>
<div class="spriteimage arrow-circle-up"></div>
<div class="txt">arrow-circle-up</div>
</td>
<td>
<div class="spriteimage arrow-circle-down"></div>
<div class="txt">arrow-circle-down</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage edit"></div>
<div class="txt">edit</div>
</td>
<td>
<div class="spriteimage edit_01"></div>
<div class="txt">edit_01</div>
</td>
<td>
<div class="spriteimage edit_02"></div>
<div class="txt">edit_02</div>
</td>
<td>
<div class="spriteimage edit_03"></div>
<div class="txt">edit_03</div>
</td>
<td>
<div class="spriteimage edit_04"></div>
<div class="txt">edit_04</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage edit_05"></div>
<div class="txt">edit_05</div>
</td>
<td>
<div class="spriteimage notification"></div>
<div class="txt">notification</div>
</td>
<td>
<div class="spriteimage notification_01"></div>
<div class="txt">notification_01</div>
</td>
<td>
<div class="spriteimage info"></div>
<div class="txt">info</div>
</td>
<td>
<div class="spriteimage smiley"></div>
<div class="txt">smiley</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage checkmark"></div>
<div class="txt">checkmark</div>
</td>
<td>
<div class="spriteimage checkmark_01"></div>
<div class="txt">checkmark_01</div>
</td>
<td>
<div class="spriteimage media-play"></div>
<div class="txt">media-play</div>
</td>
<td>
<div class="spriteimage media-pause"></div>
<div class="txt">media-pause</div>
</td>
<td>
<div class="spriteimage media-eject"></div>
<div class="txt">media-eject</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage media-next"></div>
<div class="txt">media-next</div>
</td>
<td>
<div class="spriteimage media-previous"></div>
<div class="txt">media-previous</div>
</td>
<td>
<div class="spriteimage media-forward"></div>
<div class="txt">media-forward</div>
</td>
<td>
<div class="spriteimage media-forward_01"></div>
<div class="txt">media-forward_01</div>
</td>
<td>
<div class="spriteimage media-forward_02"></div>
<div class="txt">media-forward_02</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage media-forward_03"></div>
<div class="txt">media-forward_03</div>
</td>
<td>
<div class="spriteimage media-forward_04"></div>
<div class="txt">media-forward_04</div>
</td>
<td>
<div class="spriteimage media-backward"></div>
<div class="txt">media-backward</div>
</td>
<td>
<div class="spriteimage media-backward_01"></div>
<div class="txt">media-backward_01</div>
</td>
<td>
<div class="spriteimage media-backward_02"></div>
<div class="txt">media-backward_02</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage media-backward_03"></div>
<div class="txt">media-backward_03</div>
</td>
<td>
<div class="spriteimage media-backward_04"></div>
<div class="txt">media-backward_04</div>
</td>
<td>
<div class="spriteimage play-circle"></div>
<div class="txt">play-circle</div>
</td>
<td>
<div class="spriteimage full-screen-expand"></div>
<div class="txt">full-screen-expand</div>
</td>
<td>
<div class="spriteimage full-screen-expand_01"></div>
<div class="txt">full-screen-expand_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage full-screen-collapse"></div>
<div class="txt">full-screen-collapse</div>
</td>
<td>
<div class="spriteimage full-screen-collapse_01"></div>
<div class="txt">full-screen-collapse_01</div>
</td>
<td>
<div class="spriteimage bullets"></div>
<div class="txt">bullets</div>
</td>
<td>
<div class="spriteimage bullets_01"></div>
<div class="txt">bullets_01</div>
</td>
<td>
<div class="spriteimage filter"></div>
<div class="txt">filter</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage filter_01"></div>
<div class="txt">filter_01</div>
</td>
<td>
<div class="spriteimage filternone"></div>
<div class="txt">filternone</div>
</td>
<td>
<div class="spriteimage filternone_01"></div>
<div class="txt">filternone_01</div>
</td>
<td>
<div class="spriteimage filter-settings"></div>
<div class="txt">filter-settings</div>
</td>
<td>
<div class="spriteimage align-right"></div>
<div class="txt">align-right</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage align-right_01"></div>
<div class="txt">align-right_01</div>
</td>
<td>
<div class="spriteimage align-left"></div>
<div class="txt">align-left</div>
</td>
<td>
<div class="spriteimage align-left_01"></div>
<div class="txt">align-left_01</div>
</td>
<td>
<div class="spriteimage align-justify"></div>
<div class="txt">align-justify</div>
</td>
<td>
<div class="spriteimage align-justify_01"></div>
<div class="txt">align-justify_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage align-center"></div>
<div class="txt">align-center</div>
</td>
<td>
<div class="spriteimage align-center_01"></div>
<div class="txt">align-center_01</div>
</td>
<td>
<div class="spriteimage align-none"></div>
<div class="txt">align-none</div>
</td>
<td>
<div class="spriteimage search"></div>
<div class="txt">search</div>
</td>
<td>
<div class="spriteimage search_01"></div>
<div class="txt">search_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage image"></div>
<div class="txt">image</div>
</td>
<td>
<div class="spriteimage image_01"></div>
<div class="txt">image_01</div>
</td>
<td>
<div class="spriteimage plus"></div>
<div class="txt">plus</div>
</td>
<td>
<div class="spriteimage plus_01"></div>
<div class="txt">plus_01</div>
</td>
<td>
<div class="spriteimage minus"></div>
<div class="txt">minus</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage minus_01"></div>
<div class="txt">minus_01</div>
</td>
<td>
<div class="spriteimage code"></div>
<div class="txt">code</div>
</td>
<td>
<div class="spriteimage code_01"></div>
<div class="txt">e-code_01</div>
</td>
<td>
<div class="spriteimage code-hexagon"></div>
<div class="txt">code-hexagon</div>
</td>
<td>
<div class="spriteimage file-code"></div>
<div class="txt">file-code</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage file-html"></div>
<div class="txt">file-html</div>
</td>
<td>
<div class="spriteimage palette"></div>
<div class="txt">palette</div>
</td>
<td>
<div class="spriteimage reload"></div>
<div class="txt">reload</div>
</td>
<td>
<div class="spriteimage delete"></div>
<div class="txt">delete</div>
</td>
<td>
<div class="spriteimage delete_01"></div>
<div class="txt">delete_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage delete_02"></div>
<div class="txt">delete_02</div>
</td>
<td>
<div class="spriteimage delete_03"></div>
<div class="txt">delete_03</div>
</td>
<td>
<div class="spriteimage delete_04"></div>
<div class="txt">delete_04</div>
</td>
<td>
<div class="spriteimage delete_05"></div>
<div class="txt">delete_05</div>
</td>
<td>
<div class="spriteimage pin"></div>
<div class="txt">pin</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage unpin"></div>
<div class="txt">unpin</div>
</td>
<td>
<div class="spriteimage stop"></div>
<div class="txt">stop</div>
</td>
<td>
<div class="spriteimage power-cord"></div>
<div class="txt">power-cord</div>
</td>
<td>
<div class="spriteimage fullborders"></div>
<div class="txt">fullborders</div>
</td>
<td>
<div class="spriteimage threed"></div>
<div class="txt">3d</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage file-excel"></div>
<div class="txt">file-excel</div>
</td>
<td>
<div class="spriteimage file-text"></div>
<div class="txt">file-text</div>
</td>
<td>
<div class="spriteimage file-text_01"></div>
<div class="txt">file-text_01</div>
</td>
<td>
<div class="spriteimage file-mdx"></div>
<div class="txt">file-mdx</div>
</td>
<td>
<div class="spriteimage file-empty"></div>
<div class="txt">file-empty</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage file-list"></div>
<div class="txt">file-list</div>
</td>
<td>
<div class="spriteimage file-delete_01"></div>
<div class="txt">file-delete_01</div>
</td>
<td>
<div class="spriteimage file-settings"></div>
<div class="txt">file-settings</div>
</td>
<td>
<div class="spriteimage circle-square"></div>
<div class="txt">circle-square</div>
</td>
<td>
<div class="spriteimage diagonal-square"></div>
<div class="txt">diagonal-square</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage hexagon-square"></div>
<div class="txt">hexagon-square</div>
</td>
<td>
<div class="spriteimage pentagon-square"></div>
<div class="txt">pentagon-square</div>
</td>
<td>
<div class="spriteimage globe"></div>
<div class="txt">globe</div>
</td>
<td>
<div class="spriteimage globe_01"></div>
<div class="txt">globe_01</div>
</td>
<td>
<div class="spriteimage vertical-barchart"></div>
<div class="txt">vertical-barchart</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage vertical-barchart_01"></div>
<div class="txt">vertical-barchart_01</div>
</td>
<td>
<div class="spriteimage horizontal-barchart"></div>
<div class="txt">horizontal-barchart</div>
</td>
<td>
<div class="spriteimage horizontal-barchart_01"></div>
<div class="txt">horizontal-barchart_01</div>
</td>
<td>
<div class="spriteimage pie-chart"></div>
<div class="txt">pie-chart</div>
</td>
<td>
<div class="spriteimage triangle"></div>
<div class="txt">triangle</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage inverted-triangle"></div>
<div class="txt">inverted-triangle</div>
</td>
<td>
<div class="spriteimage pyramid"></div>
<div class="txt">pyramid</div>
</td>
<td>
<div class="spriteimage inverted-pyramid"></div>
<div class="txt">inverted-pyramid</div>
</td>
<td>
<div class="spriteimage comments"></div>
<div class="txt">comments</div>
</td>
<td>
<div class="spriteimage folder"></div>
<div class="txt">folder</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage folder_01"></div>
<div class="txt">folder_01</div>
</td>
<td>
<div class="spriteimage folder-open"></div>
<div class="txt">folder-open</div>
</td>
<td>
<div class="spriteimage folder-open_01"></div>
<div class="txt">folder-open_01</div>
</td>
<td>
<div class="spriteimage folder-add"></div>
<div class="txt">folder-add</div>
</td>
<td>
<div class="spriteimage signal"></div>
<div class="txt">signal</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage sort-alpha-desc"></div>
<div class="txt">sort-alpha-desc</div>
</td>
<td>
<div class="spriteimage sort-alpha-desc_01"></div>
<div class="txt">sort-alpha-desc_01</div>
</td>
<td>
<div class="spriteimage sort-alpha-asc"></div>
<div class="txt">sort-alpha-asc</div>
</td>
<td>
<div class="spriteimage sort-alpha-asc_01"></div>
<div class="txt">sort-alpha-asc_01</div>
</td>
<td>
<div class="spriteimage print"></div>
<div class="txt">print</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage print_01"></div>
<div class="txt">print_01</div>
</td>
<td>
<div class="spriteimage print_02"></div>
<div class="txt">print_02</div>
</td>
<td>
<div class="spriteimage print_03"></div>
<div class="txt">print_03</div>
</td>
<td>
<div class="spriteimage word"></div>
<div class="txt">word</div>
</td>
<td>
<div class="spriteimage word_01"></div>
<div class="txt">word_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage word-export"></div>
<div class="txt">word-export</div>
</td>
<td>
<div class="spriteimage pdf"></div>
<div class="txt">pdf</div>
</td>
<td>
<div class="spriteimage pdf_01"></div>
<div class="txt">pdf_01</div>
</td>
<td>
<div class="spriteimage pdf-export"></div>
<div class="txt">pdf-export</div>
</td>
<td>
<div class="spriteimage excel"></div>
<div class="txt">excel</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage excel_01"></div>
<div class="txt">excel_01</div>
</td>
<td>
<div class="spriteimage excel-export"></div>
<div class="txt">excel-export</div>
</td>
<td>
<div class="spriteimage powerpoint-export"></div>
<div class="txt">powerpoint-export</div>
</td>
<td>
<div class="spriteimage ie"></div>
<div class="txt">ie</div>
</td>
<td>
<div class="spriteimage exit"></div>
<div class="txt">exit</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage document"></div>
<div class="txt">document</div>
</td>
<td>
<div class="spriteimage documents"></div>
<div class="txt">documents</div>
</td>
<td>
<div class="spriteimage question"></div>
<div class="txt">question</div>
</td>
<td>
<div class="spriteimage film"></div>
<div class="txt">film</div>
</td>
<td>
<div class="spriteimage volume-up"></div>
<div class="txt">volume-up</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage circle-one"></div>
<div class="txt">circle-one</div>
</td>
<td>
<div class="spriteimage circle-two"></div>
<div class="txt">circle-two</div>
</td>
<td>
<div class="spriteimage circle-three"></div>
<div class="txt">circle-three</div>
</td>
<td>
<div class="spriteimage circle-four"></div>
<div class="txt">circle-four</div>
</td>
<td>
<div class="spriteimage arrow-right"></div>
<div class="txt">arrow-right</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage arrow-left"></div>
<div class="txt">arrow-left</div>
</td>
<td>
<div class="spriteimage arrow-left_01"></div>
<div class="txt">arrow-left_01</div>
</td>
<td>
<div class="spriteimage arrow-up"></div>
<div class="txt">arrow-up</div>
</td>
<td>
<div class="spriteimage arrow-down"></div>
<div class="txt">arrow-down</div>
</td>
<td>
<div class="spriteimage arrow-down_01"></div>
<div class="txt">arrow-down_01</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage sync"></div>
<div class="txt">sync</div>
</td>
<td>
<div class="spriteimage sync-disabled"></div>
<div class="txt">sync-disabled</div>
</td>
<td>
<div class="spriteimage paperclip"></div>
<div class="txt">paperclip</div>
</td>
<td>
<div class="spriteimage paperclip_01"></div>
<div class="txt">paperclip_01</div>
</td>
<td>
<div class="spriteimage circle"></div>
<div class="txt">circle</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage circle_01"></div>
<div class="txt">circle_01</div>
</td>
<td>
<div class="spriteimage th-list"></div>
<div class="txt">th-list</div>
</td>
<td>
<div class="spriteimage th-large"></div>
<div class="txt">th-large</div>
</td>
<td>
<div class="spriteimage th"></div>
<div class="txt">th</div>
</td>
<td>
<div class="spriteimage th-small"></div>
<div class="txt">th-small</div>
</td>
</tr>

<tr>
<td>
<div class="spriteimage view-details"></div>
<div class="txt">view-details</div>
</td>
<td>
<div class="spriteimage file-resize-four-direction"></div>
<div class="txt">file-resize-four-direction</div>
</td>
<td>
<div class="spriteimage file-resize-horizontal"></div>
<div class="txt">file-resize-horizontal</div>
</td>
</tr>
</table>

## CDN

In case, if the users need to make use of the CDN links instead of the normal above specified scripts and stylesheet references in their application, then have a look at the link [here](http://help.syncfusion.com/js/cdn).