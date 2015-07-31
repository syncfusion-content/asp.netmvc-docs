---
layout: post
title: Overview
description: overview
platform: ejmvc
control: Presentation
documentation: ug
---

# Overview

Essential Presentation is a native .NET class library that is used by developers to easily create, read, write and convert Microsoft PowerPoint files by using C#, VB.NET and managed C++ code from any of the following .NET platforms – Windows Forms, WPF, ASP.NET and ASP.NET MVC. It is a non-UI component that provides a full-fledged document instance which that is easy to access & manipulate the contents without any dependency of Microsoft Office COM libraries & Microsoft Office. It supports only *.PPTX format documentst only; also it provides support to render the PowerPoint files (*.pptx) as an image and PDF files.

Key Features

Important features of Essential Presentation are as follows.

* Creates a new Presentations (PowerPoint files)
* Support to modify existing Microsoft PowerPoint documents.
* Support to read and write Built-In and custom document properties
* Support to create and modify Charts
* Support to export the entire Presentation or particular slide as image.
* Support to export the Presentation as PDF file.



> {{ '![](Overview_images/Overview_img1.jpeg)' | markdownify }}
{:.image }
_The current version of Essential Presentation is in preview. It does not support some features in MS PowerPoint such as Word Art, Smart Art, Notes slide, editing Master slides, Animations, Transitions, Comment, Header & Footer, Ole Object, creation & editing of Handsouts, equations, built-in themes & its variants._ 

## System Requirement

<table>
<tr>
<td>
Supported .NET Frameworks versions</td><td>
* .NET 2.0* .NET 3.5* .NET 4.0* .NET 4.5 * .NET 4.5.1</td></tr>
<tr>
<td>
<br>Compatible MS PowerPoint versions</td><td>
* MS PowerPoint 2007* MS PowerPoint 2010* MS PowerPoint 2013</td></tr>
</table>



## Required Assemblies

In order to create and& manipulation a Presentation file, the following assemblies are needed.



* Syncfusion.Core
* Syncfusion.Compression.Base
* Syncfusion.OfficeChart.Base
* Syncfusion.Presentation.Base



For converting a Presentation or a Slide to Image, the following assemblies need to be referenced.



* Syncfusion.Core
* Syncfsuion.Compression.Base
* Syncfusion.OfficeChart.Base
* Syncfusion.Presentation.Base
* Syncfusion.OfficeChartToImageConverter.WPF
* Syncfusion.SfChart.WPF
* Syncfusion.Shared.WPF



For converting a Presentation file into PDF, the following assemblies need to be referenced.

* Syncfusion.Core
* Syncfsuion.Compression.Base
* Syncfusion.OfficeChart.Base
* Syncfusion.Presentation.Base
* Syncfusion.OfficeChartToImageConverter.WPF
* Syncfusion.SfChart.WPF
* Syncfusion.Shared.WPF
* Syncfusion.Pdf.Base
* Syncfusion.PresentationToPDFConverter.Base



<table>
<tr>
<td>
Assembly Name</td><td>
Short Description</td></tr>
<tr>
<td>
Syncfusion.Presentation.Base</td><td>
This assembly contains the core features needed for creating, reading, manipulating a Presentation file.</td></tr>
<tr>
<td>
Syncfusion.Compression.Base</td><td>
This assembly is used to package the Presentation contents.</td></tr>
<tr>
<td>
Syncfusion.Core</td><td>
Serves a licensing component.</td></tr>
<tr>
<td>
Syncfusion.OfficeChart.Base</td><td>
This assembly contains the Office Chart Object model and core features needed for chart creation.</td></tr>
<tr>
<td>
Syncfusion.OfficeChartToImageConverter.WPF</td><td>
This assembly is an optional one. It is meant used for to converting Office Chart into Image. This assembly depends on Syncfusion.SfChart.WPF and Syncfusion.Shared.WPF for chart conversion.</td></tr>
<tr>
<td>
Syncfusion.Pdf.Base</td><td>
This assembly is an optional one. It is meant used for for PDF file creation. The user has toYou can add this assembly into their your project if he/she would like to convert Presentation file to PDF.</td></tr>
<tr>
<td>
Syncfusion.PresentationToPDFConverter.Base</td><td>
This assembly is an optional one. It is meant used for to converting Presentation file into PDF. The user hasYou can to add this assembly into their your project if he/she would like to convert Presentation file to PDF.</td></tr>
<tr>
<td>
Syncfusion.SfChart.WPF</td><td>
Supporting assembly for Syncfusion.OfficeChartToImageConverter.WPF</td></tr>
<tr>
<td>
Syncfusion.Shared.WPF</td><td>
Supporting assembly for Syncfusion.OfficeChartToImageConverter.WPF</td></tr>
</table>


