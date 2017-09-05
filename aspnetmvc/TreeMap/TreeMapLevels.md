---
layout: post
title: TreeMapLevels in treeMap control
description: Learn how to apply the levels in treeMap control
platform: ejmvc
control: TreeMap
documentation: ug
---

# TreeMapLevels

The levels of TreeMap can be categorized into two types as,

* FlatLevel
* Hierarchical Level

## Flat Level

### Group Path

You can use `GroupPath` property for every flat level of the TreeMap control. It is a path to a field on the source object that serves as the “Group” for the level specified. You can group the data based on the `GroupPath` in the TreeMap control. When the `GroupPath` is not specified, then the items are not grouped and the data is displayed in the order specified in the `DataSource`.

### Group Gap

You can use `GroupGap` property to separate the items from every flat level and to differentiate the levels mentioned in the TreeMap control.

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

TreeMap `Hierarchical` level is used to define levels for hierarchical data collection that contains tree-structured data.

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

			List<ContinentData> asia = new List<ContinentData>();

			asia.Add(new ContinentData() { Region = "Southern Asia", Growth = 1.32, Population = 1749046000 });

			asia.Add(new ContinentData() { Region = "Eastern Asia", Growth = 0.57, Population = 1620807000 });

			asia.Add(new ContinentData() { Region = "South-Eastern Asia", Growth = 1.20, Population = 618793000 });

			asia.Add(new ContinentData() { Region = "Western Asia", Growth = 1.98, Population = 245707000 });

			asia.Add(new ContinentData() { Region = "Central Asia", Growth = 1.43, Population = 64370000 });

			return asia;

		}

		public static List<ContinentData> GetEuropeData()

		{

			List<ContinentData> europe = new List<ContinentData>();

			europe.Add(new ContinentData() { Region = "Europe", Growth = 0.10, Population = 742452000 });

			return europe;

		}

		public static List<ContinentData> GetAmericaData()

		{

			List<ContinentData> america = new List<ContinentData>();

			america.Add(new ContinentData() {  Region = "South America", Growth = 1.06, Population = 406740000 });

			america.Add(new ContinentData() {  Region = "Northern America", Growth = 0.85, Population = 355361000 });

			america.Add(new ContinentData() {  Region = "Central America", Growth = 1.40, Population = 167387000 });

			return america;

		}

		public static List<ContinentData> GetAfricaData()

		{

			List<ContinentData> africa = new List<ContinentData>();

			africa.Add(new ContinentData() { Region = "Eastern Africa", Growth = 2.89, Population = 373202000 });

			africa.Add(new ContinentData() { Region = "Western Africa", Growth = 2.78, Population = 331255000 });

			africa.Add(new ContinentData() { Region = "Northern Africa", Growth = 1.70, Population = 210002000 });

			africa.Add(new ContinentData() { Region = "Middle Africa", Growth = 2.79, Population = 135750000 });

			africa.Add(new ContinentData() { Region = "Southern Africa", Growth = 0.91, Population = 60425000 });

			return africa;

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
