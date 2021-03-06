---
title: Using Checkboxes
page_title: Using Checkboxes | UI for WinForms Documentation
description: Using Checkboxes
slug: winforms/treeview/working-with-nodes/using-checkboxes
tags: using,checkboxes
published: True
position: 5
previous_url: treeview-working-with-nodes-using-checkboxes
---

# Using Checkboxes

Enable checkboxes by setting the RadTreeView __CheckBoxes__ boolean property to true. By default all nodes display checkboxes if the __Checkboxes__ property is true. To suppress showing a checkbox next to a particular RadTreeNode set the node __CheckType__ property to *None*. To check a node programmatically, use the __Checked__ or __CheckState__ property of RadTreeNode. When the user clicks a checkbox the __NodeCheckChanged__ event fires passing in a RadTreeViewEventArgs that contains the checked Node.

## Tri-State Checkboxes

Tri-state checkboxes in addition to having checked and unchecked states also have a "indeterminate" state. To enable this feature set the __TriStateMode__ property of RadTreeView to true. The screen shot below shows that "Node1" is in __Indeterminate__ state to indicate that its children are not all checked.

![treeview-working-with-nodes-using-checkboxes 001](images/treeview-working-with-nodes-using-checkboxes001.png)

>note When __TriStateMode__ is set to true, the __CheckBoxes__ property is also set to true automatically.
>


To programmatically set the state when __TriStateMode__ is true assign the __CheckState__  property one of the __ToggleState__ enumeration values.

![treeview-working-with-nodes-using-checkboxes 002](images/treeview-working-with-nodes-using-checkboxes002.png)

## Option Tree Support

__RadTreeView__ the supports option trees that allows radio buttons and check boxes to be mixed in order to form an arbitrary complex option tree. The only limitation is that all sibling nodes must have either check boxes or radio buttons. Check boxes and radio buttons can be mixed in a single __RadTreeNodeCollection__. The __RadTreeNode__ property that control the type of option element to be shown (check box or radio button) is __CheckType:__

![treeview-working-with-nodes-using-checkboxes 003](images/treeview-working-with-nodes-using-checkboxes003.png)

{{source=..\SamplesCS\TreeView\WorkingWithNodes\WorkingWithNodes1.cs region=optionList}} 
{{source=..\SamplesVB\TreeView\WorkingWithNodes\WorkingWithNodes1.vb region=optionList}} 

````C#
RadTreeNode Node1 = new RadTreeNode("Node1");
Node1.Expanded = true;
Node1.CheckType = CheckType.RadioButton;
RadTreeNode Node2 = new RadTreeNode("Node2");
RadTreeNode Node3 = new RadTreeNode("Node3");
RadTreeNode Node4 = new RadTreeNode("Node4");
radTreeView1.Nodes.Add(Node1);
radTreeView1.Nodes.Add(Node2);
Node1.Nodes.Add(Node3);
Node1.Nodes.Add(Node4);

````
````VB.NET
Dim Node1 As New RadTreeNode("Node1")
Node1.Expanded = True
Node1.CheckType = ChildListType.OptionList
Dim Node2 As New RadTreeNode("Node2")
Dim Node3 As New RadTreeNode("Node3")
Dim Node4 As New RadTreeNode("Node4")
RadTreeView1.Nodes.Add(Node1)
RadTreeView1.Nodes.Add(Node2)
Node1.Nodes.Add(Node3)
Node1.Nodes.Add(Node4)

````

{{endregion}}
