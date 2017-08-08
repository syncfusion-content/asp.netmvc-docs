---
layout: post
title: Getting Started | RadioButton | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: RadioButton
documentation: ug
---

# Getting Started

This section briefly describes you on how to create a QuizApp and RegistrationApp using ASP.NET MVC RadioButton control and use the features available in it.

## Create your first RadioButton in MVC

ASP.NET MVC RadioButton provides support to display the RadioButton within your web page, and allows you to pick your choice. Using the following guidelines, you can customize RadioButton for a real-time QuizApp and RegistrationApp scenarios. This allows you to select the corresponding choice for each question.

![](Getting-Started_images/Getting-Started_img1.png)


### Create your QuizApp

Essential Studio ASP.NET MVCRadioButton widget has a built-in feature to select a single option from the QuizApp. You can create the RadioButton widget using the following steps.

1. Create an MVC Project and add necessary assemblies and scripts to it.
2. Refer [MVC-Getting Started.](https://help.syncfusion.com/aspnetmvc/getting-started)
3. Add the following code example to the corresponding view page to render RadioButton.



{% highlight CSHTML %}

<div class="frame">

	<div>

		<div >

			<br />

		   1. What is the Expansion for MVC<br />



			<table>

				<tr>

					<td >

						@Html.EJ().RadioButton("Radio1").Name("rad1").Size(RadioButtonSize.Small).Checked(false).Enabled(true)<!--Creates a small Radio Button-->

						<label for="Radio1" class="clslab">

							Model View Controller

						</label>

					</td>

					<td  >

						@Html.EJ().RadioButton("Radio2").Name("rad1").Size(RadioButtonSize.Small).Checked(false).Enabled(true)

						<label for="Radio2" class="clslab">

							Model Virtual Container

						</label>

					</td>

					<td >

						@Html.EJ().RadioButton("Radio3").Name("rad1").Size(RadioButtonSize.Small).Checked(false).Enabled(true)

						<label for="Radio3" class="clslab">

							Model Visual Controller

						</label>

					</td>

				</tr>

			</table>

			<br />

			<br />

		   2.What is the Expansion for USB<br />



			<table>

				<tr>

					<td >

						@Html.EJ().RadioButton("Radio4").Name("rad2").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)<!--Creates a Medium size Radio Button-->

						<label for="Radio4" class="clslab">

							Universal Serial Bus

						</label>

					</td>

					<td >

						@Html.EJ().RadioButton("Radio5").Name("rad2").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)

						<label for="Radio5" class="clslab">

							Universal Serial Buffer

						</label>

					</td>

					<td>

						@Html.EJ().RadioButton("Radio6").Name("rad2").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)

						<label for="Radio6" class="clslab">

							Universal Serialized Buffer

						</label>

					</td>

				</tr>

			</table>

			<br/>

			<br />

			3.What is the Expansion for JS<br />



			<table>

				<tr>

					<td >

						@Html.EJ().RadioButton("Radio7").Name("rad3").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)

						<label for="Radio7" class="clslab">

							Jquery Script

						</label>

					</td>

					<td >

						@Html.EJ().RadioButton("Radio8").Name("rad3").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)

						<label for="Radio8" class="clslab">

							Java Script

						</label>

					</td>

					<td>



						@Html.EJ().RadioButton("Radio9").Name("rad3").Size(RadioButtonSize.Medium).Checked(false).Enabled(true)

						<label for="Radio9" class="clslab">

							Json Script

						</label>

					</td>

				</tr>



			</table>

			<center>

				<table>

					@Html.EJ().Button("Submit").Width("100px").Size(ButtonSize.Large).Text("Submit").ClientSideEvents(s => s.Click("button"))

			</center> 

				  </table> 



			<br />

		</div>

	</div>

</div>

{% endhighlight %}

### Add Script



{% highlight js %}

<script type="text/javascript">

    function button()

    {

        var checkedItem = [];

            $(".e-radiobtn:checked").each(function (index, Element) {

                //if ($(this).ejRadioButton('isChecked')) {

                    checkedItem.push($(this).parent().siblings().html());

                //}

            });

            alert(checkedItem);

    }

</script>

{% endhighlight %}

### Configure Style

Add the following code example in the index page.

{% highlight css %}

<style>

	.frame 
	{

		width: 80%;

	}

</style>



{% endhighlight %}


 Execute the above code example to render the following output.


![](Getting-Started_images/Getting-Started_img2.png)



### Create RegistrationApp

![](Getting-Started_images/Getting-Started_img3.png)



{% highlight CSHTML %}

<div class="frame">

        <div>

            <div >

                <br />

               1. Are you a Fresher ?<br />



                <table>

                    <tr>

                        <td >

                            @Html.EJ().RadioButton("Radio1").Name("rad1").Size(RadioButtonSize.Small).Checked(false).Enabled(true)<!--Creates a small Radio Button-->

                            <label for="Radio1" class="clslab">

                               Yes

                            </label>

                        </td>

                        <td  >

                            @Html.EJ().RadioButton("Radio2").Name("rad1").Size(RadioButtonSize.Small).Checked(false).Enabled(true)

                            <label for="Radio2" class="clslab">

                                No

                            </label>

                        </td>

                    </tr>

                </table>

                <br />

                <br />



                2. Do you complete any .NET certification courses ?<br />



                <table>

                    <tr>

                        <td>

                            @Html.EJ().RadioButton("Radio3").Name("rad2").Size(RadioButtonSize.Small).Checked(false).Enabled(true)<!--Creates a small Radio Button-->

                            <label for="Radio1" class="clslab">

                                Yes

                            </label>

                        </td>

                        <td>

                            @Html.EJ().RadioButton("Radio4").Name("rad2").Size(RadioButtonSize.Small).Checked(false).Enabled(true)

                            <label for="Radio2" class="clslab">

                                No

                            </label>

                        </td>

                    </tr>

                </table>

                <br />

                <br />



                3. Are you interested to work in .NET platform ?<br />



                <table>

                    <tr>

                        <td>

                            @Html.EJ().RadioButton("Radio5").Name("rad3").Size(RadioButtonSize.Small).Checked(false).Enabled(true)<!--Creates a small Radio Button-->

                            <label for="Radio1" class="clslab">

                                Yes

                            </label>

                        </td>

                        <td>

                            @Html.EJ().RadioButton("Radio6").Name("rad3").Size(RadioButtonSize.Small).Checked(false).Enabled(true)

                            <label for="Radio2" class="clslab">

                                No

                            </label>

                        </td>

                    </tr>

                </table>

                <br />

                <br />

                <center>

                    <table>

                        @Html.EJ().Button("Submit").Width("100px").Size(ButtonSize.Large).Text("Submit").ClientSideEvents(s => s.Click("button"))

                </center> 

                      </table> 



                <br />

            </div>

        </div>

    </div>



{% endhighlight %}

### Add Script



{% highlight js%}

<script type="text/javascript">

	function button() 
	{

		var checkedItem = [];

		var result = "";

		$(".e-radiobtn:checked").each(function (index, Element) 
		{

			quest = index + 1;

			checkedItem.push("Question" + quest + ":" + $(this).parent().siblings().html().trim()+" ");             

		});

		alert(checkedItem);

	}

</script>

{% endhighlight %}

### Add Style



{% highlight css %}

<style>

	.frame 
	{

		width: 80%;

	}

</style>

{% endhighlight %}



Execute the above code example to render the following outputs.

![](Getting-Started_images/Getting-Started_img4.png)

![](Getting-Started_images/Getting-Started_img5.png)

The whole purpose of Radio Button is to enable you to make one selection, only one, from a list. When you want to make multiple selections, you do not require a Radio Button, you need to use a CheckBox.

You can make only one selection from the group of radio buttons. All radio buttons in that group need to share the same name. This tells the form handler, the name of the group, and the value of the selected Radio Button.

Radio Button is [mutually exclusive](http://en.wikipedia.org/wiki/Mutually_exclusive_events); that is, when you select a radio button, any previously selected radio buttons in the same group become deselected. 

For example, when you want to choose between a groups of colors, you can create Radio Buttons for each color. You can give all the radio buttons the same name, for example, "preferred_color", but you must give each radio button a different value, for example, "red".

1. All radio buttons within a group must share the same name. That is, the value of the name attribute has to be the same. For example, all three radio buttons in the "Preferred Color" group have the name "preferred_color".
2. All radio buttons within a group must have a different value for the value attribute. For example, when one radio button has value as "red", none of the others in that group can have a value of red, as this would defeat the purpose of having the extra radio button.
3. The label for each radio button is determined by the text next to the radio button and not by the value attribute. The value attribute is used by the form handler.



