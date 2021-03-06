---
title: Finding Nodes
page_title: Finding Nodes | UI for WinForms Documentation
description: Finding Nodes
slug: winforms/treeview/working-with-nodes/finding-nodes
tags: finding,nodes
published: True
position: 10
previous_url: treeview-working-with-nodes-finding-nodes
---

# Finding Nodes



## 

When searching for node(s) you have two options that you can use - the *Find* method of RadTreeView which searches for a specific node by __text__ or a predefined __Predicate__ and returns the first node that matches the search criteria, or to use the *FindNodes* method of the control which also provides overloads to search by __text__ or a __Predicate__ and returns an array of nodes as a result. 

The following example demonstrates how to search for a single node by its text and how to get all nodes whose __Tag__ is not null by using a __Predicate__:

{{source=..\SamplesCS\TreeView\WorkingWithNodes\WorkingWithNodes1.cs region=find}} 
{{source=..\SamplesVB\TreeView\WorkingWithNodes\WorkingWithNodes1.vb region=find}} 

````C#
RadTreeNode resultOfSearch = radTreeView1.Find("Child Node");
            
Predicate<RadTreeNode> match = new Predicate<RadTreeNode>(delegate(RadTreeNode node)
{
    return node.Tag != null ? true : false;
});
RadTreeNode[] result = radTreeView1.FindNodes(match);

````
````VB.NET
Dim resultOfSearch As RadTreeNode = RadTreeView1.Find("Child Node")
Dim match As New Predicate(Of RadTreeNode)(Function(node As RadTreeNode) If(node.Tag IsNot Nothing, True, False))
Dim result As RadTreeNode() = RadTreeView1.FindNodes(match)

````

{{endregion}}
