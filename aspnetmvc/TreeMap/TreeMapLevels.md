---
layout: post
title: TreeMapLevels in treeMap control
description: Learn how to apply the levels in treeMap control
platform: ejmvc
control: TreeMap
documentation: ug
---

# TreeMapLevels

The `Levels` of TreeMap can be categorized into two types as,

* FlatLevel
* Hierarchical Level

Following customization options are available to customize the treemap level as per your requirements.

* To specify the background color for the group, you can use `GroupBackground` property.

* To specify the border color for the group, you can use `GroupBorderColor` property.

* To maintain the border thickness for the group, you can use `GroupBorderThickness` property.

* You can specify the gaps between groups using `GroupGap` property.

* You can specify the padding using `GroupPadding` property.

* For specifying the header height, you can use `HeaderHeight` property.

* You can customize the header template using `HeaderTemplate` property.

* To specify the label position, you can use `LabelPosition` property.

* To specify the label template for treemap, you can use `LabelTemplate` property.

* You can specify the label visibility using `LabelVisibilityMode` property.

* You can control the label visibility using `ShowLabels` property.

* For controlling text overflow, you can use `TextOverflow` property.

## Flat Level

### Group Path

You can use `GroupPath` property for every flat level of the **TreeMap** control. It is a path to a field on the source object that serves as the **“Group”** for the level specified. You can group the data based on the `GroupPath` in the **TreeMap** control. When the `GroupPath` is not specified, then the items are not grouped and the data is displayed in the order specified in the `DataSource`.

### Group Gap

You can use `GroupGap` property to separate the items from every flat level and to differentiate the levels mentioned in the **TreeMap** control.

{% highlight CSHTML %}

	@(Html.EJ().TreeMap("treemap")

		.DataSource(datasource)

		.ColorValuePath("Growth")

		.WeightValuePath("Population")               

		.Levels(lv =>

		{

			lv.GroupPath("Continent")

				.GroupGap(5).Add();

		})

		.Render())


{% endhighlight %}



![](TreeMapLevels_images/TreeMapLevels_img1.png)

## Hierarchical Level

**TreeMap** Hierarchical level is used to define levels for hierarchical data collection that contains tree-structured data.

{% tabs %}

{% highlight CSHTML %}
 
	@(Html.EJ().TreeMap("treemap")

		.DataSource(datasource)

		.WeightValuePath("Population")               

		.Render())

{% endhighlight %}

{% highlight C# %}

	public class ContinentData

	{

		public string Region { get; set; }

		public double Growth { get; set; }

		public long Population { get; set; }

		public static List<ContinentData> GetAsiaData()

		{

			List<ContinentData> Asia = new List<ContinentData>();

			Asia.Add(new ContinentData() { Region = "Southern Asia", Growth = 1.32, Population = 1749046000 });

			Asia.Add(new ContinentData() { Region = "Eastern Asia", Growth = 0.57, Population = 1620807000 });

			Asia.Add(new ContinentData() { Region = "South-Eastern Asia", Growth = 1.20, Population = 618793000 });

			Asia.Add(new ContinentData() { Region = "Western Asia", Growth = 1.98, Population = 245707000 });

			Asia.Add(new ContinentData() { Region = "Central Asia", Growth = 1.43, Population = 64370000 });

			return Asia;

		}

		public static List<ContinentData> GetEuropeData()

		{

			List<ContinentData> Europe = new List<ContinentData>();

			Europe.Add(new ContinentData() { Region = "Europe", Growth = 0.10, Population = 742452000 });

			return Europe;

		}

		public static List<ContinentData> GetAmericaData()

		{

			List<ContinentData> America = new List<ContinentData>();

			America.Add(new ContinentData() {  Region = "South America", Growth = 1.06, Population = 406740000 });

			America.Add(new ContinentData() {  Region = "Northern America", Growth = 0.85, Population = 355361000 });

			America.Add(new ContinentData() {  Region = "Central America", Growth = 1.40, Population = 167387000 });

			return America;

		}

		public static List<ContinentData> GetAfricaData()

		{

			List<ContinentData> Africa = new List<ContinentData>();

			Africa.Add(new ContinentData() { Region = "Eastern Africa", Growth = 2.89, Population = 373202000 });

			Africa.Add(new ContinentData() { Region = "Western Africa", Growth = 2.78, Population = 331255000 });

			Africa.Add(new ContinentData() { Region = "Northern Africa", Growth = 1.70, Population = 210002000 });

			Africa.Add(new ContinentData() { Region = "Middle Africa", Growth = 2.79, Population = 135750000 });

			Africa.Add(new ContinentData() { Region = "Southern Africa", Growth = 0.91, Population = 60425000 });

			return Africa;

		}

	}

	public class TreeMapPopulationData

	{

		public string Continent { get; set; }

		public List<ContinentData> Data { get; set; }

		public static List<TreeMapPopulationData> GetData()

		{

			List<TreeMapPopulationData> population = new List<TreeMapPopulationData>();

			population.Add(new TreeMapPopulationData() { Continent = "Asia", Data = ContinentData.GetAsiaData()});

			population.Add(new TreeMapPopulationData() { Continent = "Europe", Data = ContinentData.GetEuropeData()});

			population.Add(new TreeMapPopulationData() { Continent = "America", Data = ContinentData.GetAmericaData()});

			population.Add(new TreeMapPopulationData() { Continent = "Africa", Data = ContinentData.GetAfricaData() });

			return population;

		}

	}

{% endhighlight %}
{% endtabs %}  


![](TreeMapLevels_images/TreeMapLevels_img2.png)
