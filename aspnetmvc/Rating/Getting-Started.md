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



{ ![](Getting-Started_images/Getting-Started_img1.png) | markdownify }
{:.image }


In the above screenshot, you can rate the movie by selecting a corresponding movie.

### Create a Rating 

The Essential Studio ASP.NET MVCRating widget renders with built-in features like Precision, Orientation and flexible APIs. You can easily create the Rating widget by using HTML helper class as follows.

You can create an MVC Project and add the necessary assemblies, styles and scripts to it.
Refer to [MVC-Getting Started](http://help.syncfusion.com/ug/js/Documents/gettingstartedwithmv.htm).

Add the following code example to the corresponding view page to render Rating inside the Tab control.	



            &lt;div class="frame"&gt;  



            @{Html.EJ().Tab("moviesTab").Items(evt=> 

            {                

                 evt.Add().ID("steelman").Text("Man of Steel").ContentTemplate(

                     @&lt;div&gt;

                        &lt;table&gt;

                            &lt;tr&gt;

                                &lt;td class="movies-img" valign="top"&gt;                                    

                                    &lt;img src="@Url.Content("~/Images/rating/mos.png")" alt="mos" /&gt;

                                &lt;/td&gt;

                                &lt;td valign="top"&gt;

                                    &lt;div&gt;

                                        <span class="movie-header">Man of Steel</span>&lt;br /&gt;

                                        Rating :

                                                        &lt;br /&gt;



                                         @Html.EJ().Rating("univRating").Value(4)

                                        <span>Movie Info:&lt;/span&gt;

                                        &lt;p&gt;

                                            A young boy learns that he has extraordinary powers and is not of this Earth.

                                        &lt;/p&gt;

                                    &lt;/div&gt;

                                &lt;/td&gt;

                            &lt;/tr&gt;

                        &lt;/table&gt;

                    &lt;/div&gt;);



                 evt.Add().ID("woldwar").Text("World War Z").ContentTemplate(

                     @&lt;div&gt;

                    &lt;table&gt;

                        &lt;tr&gt;

                            &lt;td class="movies-img" valign="top"&gt;                                

                                &lt;img src="@Url.Content("~/Images/rating/wwz.png")" alt="mos" /&gt;

                            &lt;/td&gt;

                            &lt;td valign="top"&gt;

                                &lt;div&gt;

                                    <span class="movie-header">World War Z</span>&lt;br /&gt;

                                    Rating :

                                                    &lt;br /&gt;                                  

                                    @Html.EJ().Rating("wwzRating"). Value(4)

                                    <span>Movie Info:&lt;/span&gt;

                                    &lt;p&gt;

                                        The story revolves around United Nations employee Gerry Lane (Pitt).

                                    &lt;/p&gt;

                                &lt;/div&gt;

                            &lt;/td&gt;

                        &lt;/tr&gt;

                    &lt;/table&gt;

                &lt;/div&gt;);

                 evt.Add().ID("unive").Text("Monsters University").ContentTemplate(

                     @&lt;div&gt;

                    &lt;table&gt;

                        &lt;tr&gt;

                            &lt;td class="movies-img" valign="top"&gt;                                

                                &lt;img src="@Url.Content("~/Images/rating/mu.png")" alt="mos" /&gt;

                            &lt;/td&gt;

                            &lt;td valign="top"&gt;

                                &lt;div&gt;

                                    <span class="movie-header">Monsters University</span>&lt;br /&gt;

                                    Rating :

                                                    &lt;br /&gt;



                                    @Html.EJ().Rating("mosRating").Value(3)

                                    <span>Movie Info:&lt;/span&gt;

                                    &lt;p&gt;

                                        Mike Wazowski and James P. Sullivan are an inseparable pair, but that wasn't always the case. 

                                    &lt;/p&gt;

                                &lt;/div&gt;

                            &lt;/td&gt;

                        &lt;/tr&gt;

                    &lt;/table&gt;

                &lt;/div&gt;);

            }).Render();}

         &lt;/div&gt;





Add the following styles to the corresponding view page to show the Rating in a horizontal order.


&lt;style type="text/css" class="cssStyles"&gt;

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

    &lt;/style&gt;



Execute the above code to render the following output.





{ ![](Getting-Started_images/Getting-Started_img2.png) | markdownify }
{:.image }


{ ![C:/Users/ApoorvahR/Desktop/Note.png](Getting-Started_images/Getting-Started_img3.png) | markdownify }
{:.image }
_Note: Add necessary images to the mentioned directory._

> _&lt;project directory&gt;/Images/rating/yourimage.png_

