---
layout: post
title: Scrolling with Spreadsheet widget for Syncfusion Essential ASP.NET MVC
description: How to enable Scrolling and its functionalities
platform: ejmvc
control: Spreadsheet
documentation: ug
--- 

# Scrolling

Scrolling helps you to move quickly to different areas of worksheet. Scrolling can be enabled by setting `AllowScrolling` as `true` in `ScrollSettings`. 
  
You can scroll through worksheet using one of the following ways,

* Using the arrow keys
* Using the scroll bars
* Using the mouse

## Set height and width for Scrolling

To set height and width in spreadsheet use `Height` and `Width` property in `ScrollSettings`. The default value for `Height` and `Width` is `100%`.
The height and width can be set in percentage or pixel.

The following code example describes the above behavior.

{% highlight cshtml %}
@(Html.EJ().Spreadsheet<object>("Spreadsheet")
    .ScrollSettings(scroll =>
    {
        scroll.AllowScrolling(true);
        scroll.Height(400); // Height in pixel
        scroll.Width("50%"); // Width in percentage
    })
)
{% endhighlight %}

The following output is displayed as a result of the above code example.

![](Scrolling_images/Scrolling_img1.png)

## Responsive

Spreadsheet has support for responsive behavior based on client browser's width and height. To enable responsive, set `IsResponsive` property in `ScrollSettings` as `true`. The three modes of responsive layout available in Spreadsheet based on client width are,

* Mobile(<420px)
* Tablet (420px to 617px)
* Desktop(>617px)

N> Default value of `IsResponsive` property is `true`.

### Mobile Mode

If client width is less than 420px, the spreadsheet will render in mobile mode. In which, you can see that spreadsheet user interface is customized and redesigned for best view in small screens. The customized feature includes filter dialog, format dialog, chart type dialog and ribbon.

![](Scrolling_images/Scrolling_img2.png)

Ribbon in mobile layout
{:.caption}

![](Scrolling_images/Scrolling_img3.png)

Format cell dialog in mobile layout.
{:.caption}

### Tablet Layout

If the client width is between 420px and 617px, then the spreadsheet will render in tablet mode. Also it has customized the dialogs to match tablet screen size.

![](Scrolling_images/Scrolling_img4.png)

Ribbon in tablet layout.
{:.caption}

## Scroll Mode

Spreadsheet supports two type of modes in scrolling. You can use `ScrollMode` property in `ScrollSettings` to specify the mode of scrolling.

* Normal - This mode doesn't create new row/column when the scrollbar reaches the end.
* Infinite - This mode creates new row/column when the scrollbar reaches the end.

N> Default value of `ScrollMode` property is `Infinite` mode.

## Virtual Scrolling

Spreadsheet has support for virtual scrolling. This allows you to load data that you require (load data based on viewport size) without buffering the entire huge database. You can set `AllowVirtualScrolling` property in `ScrollSettings` as `true` to enable virtual scrolling.

N> Default value of `AllowVirtualScrolling` property is true.

