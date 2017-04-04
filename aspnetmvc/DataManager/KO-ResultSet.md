---
layout: post
title: KO ResultSet | DataManager | ASP.NET MVC | Syncfusion
description: ko resultset
platform: ejmvc
control: DataManager
documentation: ug
keywords: KO ResultSet
---

# KO ResultSet

The DataManager contains a default method to subscribe the view model properties as KO observable. This is done at the success of the executeQuery by using the getKnockoutModel. You can also provide computed properties to the view model by using the getKnockoutModel.

The following code example illustrates how the model is made observable and updated.

{% highlight CSHTML %}

	<div class="datatable" style="padding:10px">
		<div class="row">
			<div class="col-md-7">
				<table id="table1" class="table table-striped table-bordered" style="width:700px">
					<thead>
						<tr>
							<th>EmployeeID</th>
							<th>Full Name</th>
						</tr>
					</thead>
					<tbody data-bind="foreach: employees">
						<tr>
							<td data-bind="text: EmployeeID"></td>
							<td data-bind="text: FullName"></td>
						</tr>
					</tbody>
				</table>
			</div>
			<div class="col-md-5">
				<form class="form-horizontal" role="form">
					<div class="form-group">
						<label class="col-sm-4 control-label">EmployeeID</label>
						<div class="col-sm-8">
							<input type="text" class="form-control" id="empId">
						</div>
					</div>
					<div class="form-group">
						<label class="col-sm-4 control-label">FirstName</label>
						<div class="col-sm-8">
							<input type="text" class="form-control" id="first">
						</div>
					</div>
					<div class="form-group">
						<label class="col-sm-4 control-label">LastName</label>
						<div class="col-sm-8">
							<input type="text" class="form-control" id="last">
						</div>
					</div>
					<div class="form-group">
						<div class="col-sm-offset-4 col-sm-4">
							<button type="button" id="formsubmit" class="btn btn-default">Change</button>
						</div>
					</div>
				</form>
			</div>
		</div>
	</div>

	@(Html.EJ().DataManager("FlatData").Json((IEnumerable<object>)ViewBag.datasource).Adaptor(AdaptorType.JsonAdaptor))


	<script src="~/Scripts/knockout.min.js"></script>
	<script src="~/Scripts/ej/ej.widget.ko.min.js"></script>

	<script type="text/javascript">
		setTimeout( function (){

				window.pageModel = {
					employees: []
				};
			
				var query = ej.Query();
			var promise = window.FlatData.executeQuery(query);
			
				promise.done(function (e) {
					pageModel.employees = e.getKnockoutModel({
						FullName: function () {
							return this.FirstName() + " " + this.LastName();
						}
					});
					ko.applyBindings(pageModel);
				});
			}, 1000);
			$("#formsubmit").click(function (e) {
				var empId = parseInt($("#empId").val(), 10);
				var fName = $("#first").val();
				var lName = $("#last").val();
				employee = window.pageModel.employees()[empId - 1];
				employee.FirstName(fName);
				employee.LastName(lName);
			});
	</script>

{% endhighlight %}

The result of the above code example is illustrated as follows.

Before changing the model, EmployeeID 1 has FullName value as Nancy Davolio. After changing, the result is as follows.


![](KO-ResultSet_images/KO-ResultSet_img1.png)

Knockout ResultSet
{:.caption}
