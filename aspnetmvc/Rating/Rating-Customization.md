---
layout: post
title: Rating Customization | Rating | ASP.NET MVC | Syncfusion
description: rating customization
platform: ejmvc
control: Rating
documentation: ug
---

# Rating Customization

## Setting Value

The Value property sets the display value of the Rating. For example, when the Value property is set to 4, the Rating control renders 4 ratings. By default, Value property’s value is one.

The following code example is used to render the Rating control with the customized value.

Add the following code in your view page to render the Rating with the customized value.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with customized value.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").Value(4)

            </td>

        </tr>

    </table>

</div>

{% endhighlight %}



The following screenshot illustrates the Rating with custom defined value.



![](Rating-Customization_images/Rating-Customization_img1.png)' 



## Min Value

Rating control provides support for setting the MinimumValue. This is achieved by adding the MinValue property. When the MinValue property is set, the Rating value starts with MinValue+1.

The following code example is used to render the Rating control with minimumrating value specfied.

Add the following code in your view page to render the Rating with Minimumvalue.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with customized minimum value.

<div id="container" style="width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").MinValue(3)

            </td>

        </tr>

    </table>

</div>

{% endhighlight %}



The following screenshot Rating value starts with 4 since MinValuevalue is set as 3.

![](Rating-Customization_images/Rating-Customization_img2.png)

Rating with minimum value as 4
{:.caption}

## Max Value

Rating controlprovides support for setting Maximumvalue. This is achieved by adding the MaxValue property. By default, MaxValue is five.

The following code example is used to render the Rating control with maximumrating value spefied

Add the following code in your view pageto render the Rating with maximumvalue.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with customized maximum value.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").MaxValue(10)

            </td>

        </tr>

    </table>

</div>

{% endhighlight %}



The following screenshot illustrates the Rating with maximumvalue.



![](Rating-Customization_images/Rating-Customization_img3.png)


## Set Precision

You can set Precision in Rating value between two whole numbers such as 2.5 or 3.7 and it is done by using the property Precision by changing the value to Precision.Half or Precision.Exact. By default, value of Precision is Full.

The following code example is used to render the Rating control with Precision.

Add the following code in your view page to render the Rating with Precision.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with Precison.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("FullRating").Precision(Precision.Full).Value(4)

            </td>

        </tr>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("HalfRating").Precision(Precision.Half).Value(3.5)

            </td>

        </tr>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("ExactRating").Precision(Precision.Exact).Value(4.7)

            </td>

        </tr>

    </table>

</div>

{% endhighlight %}

The following screenshot illustrates the Rating with Precision.



![](Rating-Customization_images/Rating-Customization_img4.png)



## Increment Step

Rating control supports customized increment value for Rating. This is achieved by adding the IncrementStep property.

The following code example is used to render the Rating control with customized increment.

Add the followingcode in your view page to render the Rating with customized increment.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with customized increment.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

	<table>

		<tr>

			<td valign="top">Rating:

			</td>

			<td>

				@Html.EJ().Rating("Rating").IncrementStep(2).MaxValue(10)

			</td>

		</tr>      

	</table>

</div>

{% endhighlight %}



The following screenshot illustrates the Rating with customized increment.

![](Rating-Customization_images/Rating-Customization_img5.png)

![](Rating-Customization_images/Rating-Customization_img6.png)



## Resetting values

Rating control provides support for value reset at runtime. This is achieved by enabling the AllowReset property to True. By default, the property value is set to True.

The following code example is used to render the Rating control with AllowReset.

Add the following code in your view page to render the Rating with AllowReset.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with allowReset.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("ResetRating").AllowReset(true)

            </td>

        </tr>  

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").AllowReset(false)

            </td>

        </tr>    

    </table>

</div> 

{% endhighlight %}

The following illustrates the Rating with allowReset.



![](Rating-Customization_images/Rating-Customization_img7.png)



## Read only

Rating control provides support for changeable or unchangeable values for Rating control. This is achieved by the ReadOnly property. When this property is set to True, the Rating value becomes unchangeable. By default, this property value is set to False.

The following code example is used to render the Rating control with ReadOnly.

Add the following code in your view page to render Rating with readOnly.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with readOnly.

<div id="container" style="width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").ReadOnly(true).Value(2).MaxValue(10) 

            </td>

        </tr>  


    </table>

</div>

{% endhighlight %}

The following screenshot illustrates the Rating with ReadOnly.



![](Rating-Customization_images/Rating-Customization_img8.png)



## Enable or Disable

Rating control provides support to Enable or Disable the control. This is achieved by the Enabled property. By default the property value is True.

The following code example is used to render the Rating control with Enable or Disable support.

Add the following code in your view page to render the Rating with enable or disable support.



{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Rating with Enable/Disable support.

<div id="container" style="border: 1px solid black; width: 300px; padding: 2px">

    <table>

        <tr>

            <td valign="top">Rating:

            </td>

            <td>

                @Html.EJ().Rating("Rating").Enabled(false)

            </td>

        </tr>

    </table>

</div>
{% endhighlight %}


The following screenshot illustrates the Rating in a disabled form.



![](Rating-Customization_images/Rating-Customization_img9.png)



