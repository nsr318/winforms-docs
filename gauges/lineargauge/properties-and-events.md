---
title: Properties and Events
page_title: Properties and Events | UI for WinForms Documentation
description: Properties and Events
slug: winforms/gauges/lineargauge/properties-and-events
tags: properties,and,events
published: True
position: 5
previous_url: lineargauge-properties-and-events
---

# Properties and Events



## Properties

* __Value:__ With this property you ca get/set all bound elements value. 

* __RangeStart:__ Indicates the start value – the minimum value that will be shown.

* __RangeEnd:__ Indicates the end value – the maximum value that will be displayed.

* __Vertical:__ This is a Boolean property which gets/set the orientation of the gauge. This property should be set before the control is added to the controls collection.

* __Items__ – this property allows you to access the items collection and add/remove elements.

## Events

The __ValueChanged__ event fires when the __Value__ of the control is changed. For example you can use this event to alert the user that the current value is close to the maximum: 

{{source=..\SamplesCS\Gauges\LinearGauge\LinearGuageGettingStarted.cs region=value}} 
{{source=..\SamplesVB\Gauges\LinearGauge\LinearGuageGettingStarted.vb region=value}} 

````C#
void radLinearGauge2_ValueChanged(object sender, EventArgs e)
{
    if ( radLinearGauge2.Value > radLinearGauge2.RangeEnd - 10)
    {
        RadMessageBox.Show("Detected value that is close to the maximum!");
    }
}

````
````VB.NET
Private Sub radLinearGauge1_ValueChanged(ByVal sender As Object, ByVal e As EventArgs)
    If radLinearGauge2.Value > radLinearGauge2.RangeEnd - 10 Then
        RadMessageBox.Show("Detected value that is close to the maximum!")
    End If
End Sub

````

{{endregion}} 



