---
layout: post
title: Getting-Started
description: getting started
platform: ejmvc
control: Rating
documentation: ug
---

# Getting Started

This section explains briefly how to create a Rating control in the ASP.NET MVC.

## Create your first Rating control in MVC

Essential Studio ASP.NET MVCRating control provides support to display Rating bar within your webpage, and allows you to rate the products. Refer to the following guidelines to customize the Rating control for a real-time movie download application. You can use Rating control to rate a movie. In this real-time application, Essential Studio ASP.NET MVCTab control is used to display the movies information with rating star.To know more about Tab control, refer to the Getting Started of the Tab control.

The following screenshot demonstrates the functionality of a Rating control with a Rating range of 0 to 5. 



![](Getting-Started_images/Getting-Started_img1.png)



In the above screenshot, you can rate the movie by selecting a corresponding movie.

### Create a Rating 

The Essential Studio ASP.NET MVCRating widget renders with built-in features like Precision, Orientation and flexible APIs. You can easily create the Rating widget by using HTML helper class as follows.

You can create an MVC Project and add the necessary assemblies, styles and scripts to it.
Refer to [MVC-Getting Started](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm).

Add the following code example to the corresponding view page to render Rating inside the Tab control.	

{% highlight html %}

            <div class="frame">  



            @{Html.EJ().Tab("moviesTab").Items(evt=> 

            {                

                 evt.Add().ID("steelman").Text("Man of Steel").ContentTemplate(

                     @<div>

                        <table>

                            <tr>

                                <td class="movies-img" valign="top">                                    

                                    <img src="@Url.Content("~/Images/rating/mos.png")" alt="mos" />

                                </td>

                                <td valign="top">

                                    <div>

                                        <span class="movie-header">Man of Steel</span><br />

                                        Rating :

                                                        <br />



                                         @Html.EJ().Rating("univRating").Value(4)

                                        <span>Movie Info:</span>

                                        <p>

                                            A young boy learns that he has extraordinary powers and is not of this Earth.

                                        </p>

                                    </div>

                                </td>

                            </tr>

                        </table>

                    </div>);



                 evt.Add().ID("woldwar").Text("World War Z").ContentTemplate(

                     @<div>

                    <table>

                        <tr>

                            <td class="movies-img" valign="top">                                

                                <img src="@Url.Content("~/Images/rating/wwz.png")" alt="mos" />

                            </td>

                            <td valign="top">

                                <div>

                                    <span class="movie-header">World War Z</span><br />

                                    Rating :

                                                    <br />                                  

                                    @Html.EJ().Rating("wwzRating"). Value(4)

                                    <span>Movie Info:</span>

                                    <p>

                                        The story revolves around United Nations employee Gerry Lane (Pitt).

                                    </p>

                                </div>

                            </td>

                        </tr>

                    </table>

                </div>);

                 evt.Add().ID("unive").Text("Monsters University").ContentTemplate(

                     @<div>

                    <table>

                        <tr>

                            <td class="movies-img" valign="top">                                

                                <img src="@Url.Content("~/Images/rating/mu.png")" alt="mos" />

                            </td>

                            <td valign="top">

                                <div>

                                    <span class="movie-header">Monsters University</span><br />

                                    Rating :

                                                    <br />



                                    @Html.EJ().Rating("mosRating").Value(3)

                                    <span>Movie Info:</span>

                                    <p>

                                        Mike Wazowski and James P. Sullivan are an inseparable pair, but that wasn't always the case. 

                                    </p>

                                </div>

                            </td>

                        </tr>

                    </table>

                </div>);

            }).Render();}

         </div>


{% endhighlight %}


Add the following styles to the corresponding view page to show the Rating in a horizontal order.

{% highlight css %}

<style type="text/css" class="cssStyles">

        .movies-img {

            width: 125px;

        }



        .movie-header {

            font-size: 20px;

            font-weight: 600;

        }

        .frame {

            width: 600px;

            height: 250px;

        }

    </style>

{% endhighlight %}

Execute the above code to render the following output.





![](Getting-Started_images/Getting-Started_img2.png)



_Note: Add necessary images to the mentioned directory._

> _<project directory>/Images/rating/yourimage.png_

