---
title: Setting Filters Programmatically (composite descriptors)
page_title: Setting Filters Programmatically (composite descriptors) | UI for WinForms Documentation
description: Setting Filters Programmatically (composite descriptors)
slug: winforms/gridview/filtering/setting-filters-programmatically-(composite-descriptors)
tags: setting,filters,programmatically,(composite,descriptors)
published: True
position: 3
previous_url: gridview-filtering-setting-filters-programmatically-composite-descriptors
---

# Setting Filters Programmatically (composite descriptors)



## Using CompositeFilterDescriptor

To filter a single data field by multiple values, you have to use the __CompositeFilterDescriptor__ object. It contains a collection of filter descriptors objects and the logical operator for that filters.

#### Setting composite filter descriptors

{{source=..\SamplesCS\GridView\Filtering\Filtering.cs region=settingCompositeFilterDescriptors}} 
{{source=..\SamplesVB\GridView\Filtering\Filtering.vb region=settingCompositeFilterDescriptors}} 

````C#
CompositeFilterDescriptor compositeFilter = new CompositeFilterDescriptor();
compositeFilter.FilterDescriptors.Add(new FilterDescriptor("UnitsInStock", FilterOperator.IsGreaterThan, 100));
compositeFilter.FilterDescriptors.Add(new FilterDescriptor("ProductName", FilterOperator.StartsWith, "G"));
compositeFilter.LogicalOperator = FilterLogicalOperator.And;
this.radGridView1.FilterDescriptors.Add(compositeFilter);

````
````VB.NET
Dim compositeFilter As New CompositeFilterDescriptor()
compositeFilter.FilterDescriptors.Add(New FilterDescriptor("UnitsInStock", FilterOperator.IsGreaterThan, 100))
compositeFilter.FilterDescriptors.Add(New FilterDescriptor("ProductName", FilterOperator.StartsWith, "G"))
compositeFilter.LogicalOperator = FilterLogicalOperator.[And]
Me.RadGridView1.FilterDescriptors.Add(compositeFilter)

````

{{endregion}} 

The composite FilterDescriptors supports *__And__* and *__Or__* logical operators. Result of the above example using *__And__* logical operator:<BR>![gridview-filtering-setting-filters-programmatically-composite-descriptors 001](images/gridview-filtering-setting-filters-programmatically-composite-descriptors001.png)

Result of the above example using *__Or__* logical operator:<br>![gridview-filtering-setting-filters-programmatically-composite-descriptors 002](images/gridview-filtering-setting-filters-programmatically-composite-descriptors002.png)

## More Complex Composite Filters

The composite filters allow you to create more complex filtering expressions. Such a complex filtering expression might include filters for multiple fields combined with different logical operators, like __(UnitsOnOrder= 0 AND (UnitsInStock> 100 OR ProductName.StartsWith(“G”)))__.

#### Setting complex composite filter descriptors

{{source=..\SamplesCS\GridView\Filtering\Filtering.cs region=settingComplexCompositeFilterDescriptors}} 
{{source=..\SamplesVB\GridView\Filtering\Filtering.vb region=settingComplexCompositeFilterDescriptors}} 

````C#
CompositeFilterDescriptor compositeFilter1 = new CompositeFilterDescriptor();
compositeFilter1.FilterDescriptors.Add(new FilterDescriptor("UnitsInStock", FilterOperator.IsGreaterThan, 100));
compositeFilter1.FilterDescriptors.Add(new FilterDescriptor("ProductName", FilterOperator.StartsWith, "G"));
compositeFilter1.LogicalOperator = FilterLogicalOperator.Or;
FilterDescriptor filter2 = new FilterDescriptor("UnitsOnOrder", FilterOperator.IsEqualTo, 0);
CompositeFilterDescriptor filterDescriptor2 = new CompositeFilterDescriptor();
filterDescriptor2.FilterDescriptors.Add(compositeFilter);
filterDescriptor2.FilterDescriptors.Add(filter2);
filterDescriptor2.LogicalOperator = FilterLogicalOperator.And;
this.radGridView1.FilterDescriptors.Add(filterDescriptor2);

````
````VB.NET
Dim compositeFilter1 As New CompositeFilterDescriptor()
compositeFilter1.FilterDescriptors.Add(New FilterDescriptor("UnitsInStock", FilterOperator.IsGreaterThan, 100))
compositeFilter1.FilterDescriptors.Add(New FilterDescriptor("ProductName", FilterOperator.StartsWith, "G"))
compositeFilter1.LogicalOperator = FilterLogicalOperator.[Or]
Dim filter2 As New FilterDescriptor("UnitsOnOrder", FilterOperator.IsEqualTo, 0)
Dim filterDescriptor2 As New CompositeFilterDescriptor()
filterDescriptor2.FilterDescriptors.Add(compositeFilter)
filterDescriptor2.FilterDescriptors.Add(filter2)
filterDescriptor2.LogicalOperator = FilterLogicalOperator.[And]
Me.RadGridView1.FilterDescriptors.Add(filterDescriptor2)

````

{{endregion}} 



