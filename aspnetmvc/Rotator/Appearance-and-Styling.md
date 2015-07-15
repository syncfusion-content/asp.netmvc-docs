---
layout: post
title: Appearance-and-Styling
description: appearance and styling
platform: ejmvc
control: Rotator
documentation: ug
---

## Appearance and Styling

Adjusting rotator item size

SlideWidth

This property sets the Width of a Rotator Item. The value set to this property is string or number.



[CSHTML]

@Html.EJ().Rotator("slidercontent").Datasource((IEnumerable<Localdata>)ViewBag.datasource).RotatorFields(t => t.Text("Text").Url("Url")).SlideWidth("600px").SlideHeight("350px")





SlideHeight

This property sets the Height of a Rotator Item. The value set to this property is string or number.



[CSHTML]

@Html.EJ().Rotator("slidercontent").Datasource((IEnumerable<Localdata>)ViewBag.datasource).RotatorFields(t => t.Text("Text").Url("Url")).SlideWidth("600px").SlideHeight("350px")





