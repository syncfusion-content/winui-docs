---
layout: post
title: Editing in WinUI TreeGrid control | Syncfusion
description: Learn here all about Editing feature of Syncfusion WinUI TreeGrid(SfTreeGrid) control with cursor placement support and more.
platform: winui
control: SfTreeGrid
documentation: ug
---

# Editing in WinUI TreeGrid

SfTreeGrid provides support for editing and it can be enabled or disabled by setting [SfTreeGrid.AllowEditing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_AllowEditing) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid Name="treeGrid"
                        ChildPropertyName="ReportsTo"
                        ColumnWidthMode="Star"
                        AutoGenerateColumns="False"
                        AllowEditing="True"
                        ItemsSource="{Binding Employees}"
                        ParentPropertyName="ID"
                        SelfRelationRootValue="-1" >
    <treeGrid:SfTreeGrid.Columns>
        <treeGrid:TreeGridTextColumn HeaderText="First Name" MappingName="FirstName"/>
        <treeGrid:TreeGridTextColumn HeaderText="Last Name" MappingName="LastName" />
        <treeGrid:TreeGridNumericColumn HeaderText="Employee ID" MappingName="ID" />
        <treeGrid:TreeGridTextColumn HeaderText="Title" MappingName="Title" />
        <treeGrid:TreeGridNumericColumn HeaderText="Salary" MappingName="Salary" DisplayNumberFormat="C2"/>
        <treeGrid:TreeGridNumericColumn HeaderText="Reports To" MappingName="ReportsTo" />
    </treeGrid:SfTreeGrid.Columns>
</treeGrid:SfTreeGrid>

{% endhighlight %}
{% highlight c# %}

this.treeGrid.AllowEditing = true;
	
{% endhighlight %}
{% endtabs %}

You can enable or disable editing for particular column by setting [TreeGridColumn.AllowEditing](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_AllowEditing) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:TreeGridTextColumn AllowEditing="True"
                                HeaderText="First Name" 
                                MappingName="FirstName" />							
{% endhighlight %}
{% highlight c# %}

this.treeGrid.Columns["FirstName"].AllowEditing = true;
	
{% endhighlight %}
{% endtabs %}

N> `TreeGridColumn.AllowEditing` takes higher priority than `SfTreeGrid.AllowEditing`

<img src="Editing-images/winui-treegrid-editing.png" alt="Editing in WinUI TreeGrid" width="100%" Height="Auto"/>

N> It is mandatory to set the [NavigationMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.NavigationMode.html) to Cell to enable CurrentCell navigation and editing.

## Entering into edit mode

You can enter into edit mode by pressing <kbd>F2</kbd> key or clicking (touch also supported) the cell. You can allow users to edit the cell in single click (OnTap) or double click (OnDoubleTab) by setting [SfTreeGrid.EditTrigger](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_EditTrigger) property.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid Name="treeGrid"
                        ChildPropertyName="ReportsTo"
                        ColumnWidthMode="Star"
                        AutoGenerateColumns="False"
                        AllowEditing="True"
                        EditTrigger="OnTap"
                        ItemsSource="{Binding Employees}"
                        ParentPropertyName="ID"
                        SelfRelationRootValue="-1" />					
{% endhighlight %}
{% highlight c# %}

this.treeGrid.EditTrigger = EditTrigger.OnTap;
	
{% endhighlight %}
{% endtabs %}

## Cursor placement

When the cell enters into edit mode, cursor is placed based on [SfTreeGrid.EditorSelectionBehavior](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_EditorSelectionBehavior) property.

[SelectAll](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.EditorSelectionBehavior.html#Syncfusion_UI_Xaml_Grids_EditorSelectionBehavior_SelectAll) - selects the text of edit element loaded inside cell.

[MoveLast](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.EditorSelectionBehavior.html#Syncfusion_UI_Xaml_Grids_EditorSelectionBehavior_MoveLast) - ֠places the cursor at the last of edit element loaded inside cell.

{% tabs %}
{% highlight xaml %}

<treeGrid:SfTreeGrid Name="treeGrid"
                        ChildPropertyName="ReportsTo"
                        ColumnWidthMode="Star"
                        AutoGenerateColumns="False"
                        AllowEditing="True"
                        EditTrigger="OnTap"
                        EditorSelectionBehavior="SelectAll"
                        ItemsSource="{Binding Employees}"
                        ParentPropertyName="ID"
                        SelfRelationRootValue="-1" />						
{% endhighlight %}
{% highlight c# %}

this.treeGrid.EditorSelectionBehavior = EditorSelectionBehavior.SelectAll;
	
{% endhighlight %}
{% endtabs %}

## Support for IEditableObject

SfTreeGrid supports to commit and roll back the changes in row level when underlying data object implements [IEditableObject](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject?view=net-6.0) interface.

The editing changes in a row will be committed only when user move to next row or pressing enter key in [EndEdit](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.endedit?view=net-6.0). Also when user press <kbd>Esc</kbd> key, then the changes made in a row will be reverted in [CancelEdit](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.canceledit?view=net-6.0). 

`IEditableObject` has the following methods to capture editing,

[BeginEdit](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.beginedit?view=net-6.0) - Gets called to begin edit on underlying data object when cell in a row get into edit mode. 

[CancelEdit](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.canceledit?view=net-6.0https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.canceledit?view=net-6.0) - Gets called when user press the <kbd>Esc</kbd> key to discard the changes in a row since last `BeginEdit` call. 

[EndEdit](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.ieditableobject.endedit?view=net-6.0) - Gets called when user move to the next row or press <kbd>Enter</kbd> key  to commit changes in underlying data object since last `BeginEdit` call. 

The below code snippet explains the simple implementation of IEditableObject.

{% tabs %}
{% highlight c# %}

public class EmployeeInfo : IEditableObject, INotifyPropertyChanged
{      
	int _id;
	/// <summary>
	/// Gets or sets the ID.
	/// </summary>
	/// <value>The ID.</value>
	public int ID
	{
		get
		{
			return _id;
		}
		set
		{
			_id = value;
			RaisePropertyChanged("ID");
		}
	}

	string _firstName;
	/// <summary>
	/// Gets or sets the first name.
	/// </summary>
	/// <value>The first name.</value>   
	public string FirstName
	{
		get { return _firstName; }
		set
		{
			_firstName = value;
			RaisePropertyChanged("FirstName");
		}
	}

	string _lastName;
	/// <summary>
	/// Gets or sets the last name.
	/// </summary>
	/// <value>The last name.</value>
	public string LastName
	{
		get { return _lastName; }
		set
		{
			_lastName = value;
			RaisePropertyChanged("LastName");
		}
	}

	private string _title;
	/// <summary>
	/// Gets or sets the title.
	/// </summary>
	/// <value>The title.</value>
	public string Title
	{
		get
		{
			return _title;
		}
		set
		{
			_title = value;
			RaisePropertyChanged("Title");
		}
	}

	double? _salary;
	/// <summary>
	/// Gets or sets the salary.
	/// </summary>
	/// <value>The salary.</value>
	public double? Salary
	{
		get
		{
			return _salary;
		}
		set
		{
			_salary = value;
			RaisePropertyChanged("Salary");
		}
	}

	int _reportsTo;
	/// <summary>
	/// Gets or sets the reports to.
	/// </summary>
	/// <value>The reports to.</value>
	public int ReportsTo
	{
		get
		{
			return _reportsTo;
		}
		set
		{
			_reportsTo = value;
			RaisePropertyChanged("ReportsTo");
		}
	}
	  
	protected Dictionary<string, object> BackUp()
	{
		var dictionary = new Dictionary<string, object>();
		var itemProperties = this.GetType().GetTypeInfo().DeclaredProperties;

		foreach (var pDescriptor in itemProperties)
		{

			if (pDescriptor.CanWrite)
				dictionary.Add(pDescriptor.Name, pDescriptor.GetValue(this));
		}
		return dictionary;
	}

	private Dictionary<string, object> storedValues;

	public void BeginEdit()
	{
		this.storedValues = this.BackUp();
	}

	public void CancelEdit()
	{
		if (this.storedValues == null)
			return;
		foreach (var item in this.storedValues)
		{
			var itemProperties = this.GetType().GetTypeInfo().DeclaredProperties;
			var pDesc = itemProperties.FirstOrDefault(p => p.Name == item.Key);
			if (pDesc != null)
				pDesc.SetValue(this, item.Value);
		}
	}

	public void EndEdit()
	{           
		if (this.storedValues != null)
		{
			this.storedValues.Clear();
			this.storedValues = null;
		}
	}

	public event PropertyChangedEventHandler PropertyChanged;

	public void RaisePropertyChanged(string propertyName)
	{
		if (PropertyChanged != null)
			PropertyChanged(this, new PropertyChangedEventArgs(propertyName));
	}
}
	
{% endhighlight %}
{% endtabs %}

## Events

SfTreeGrid triggers the following events during editing. 

### CurrentCellBeginEdit Event

[CurrentCellBeginEdit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellBeginEdit) event occurs when the [CurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_CurrentCell) enter into edit mode. [TreeCurrentCellBeginEditEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellBeginEditEventArgs.html) has following members which provides information for `CurrentCellBeginEdit` event.

* [Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel?view=net-6.0) : When set to `true`, the event is canceled and the `CurrentCell` does not enter into the edit mode.

* [RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellBeginEditEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellBeginEditEventArgs_RowColumnIndex) : Gets the current row column index of the TreeGrid.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellBeginEditEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellBeginEditEventArgs_Column) : Gets the Tree Grid Column of the SfTreeGrid.

{% tabs %}
{% highlight c# %}

this.treeGrid.CurrentCellBeginEdit += TreeGrid_CurrentCellBeginEdit;

void TreeGrid_CurrentCellBeginEdit(object sender, TreeGridCurrentCellBeginEditEventArgs args)
{
}
	
{% endhighlight %}
{% endtabs %}

### CurrentCellEndEdit Event

[CurrentCellEndEdit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellEndEdit) event occurs when the [CurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_CurrentCell) exits the edit mode. 
[CurrentCellEndEditEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellEndEdit) has following members which provides information for `CurrentCellEndEdit` event.

* [RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.CurrentCellEndEditEventArgs.html#Syncfusion_UI_Xaml_DataGrid_CurrentCellEndEditEventArgs_RowColumnIndex) : Gets the current row column index of the TreeGrid.


{% tabs %}
{% highlight c# %}

this.treeGrid.CurrentCellEndEdit += TreeGrid_CurrentCellEndEdit;

void TreeGrid_CurrentCellEndEdit(object sender, CurrentCellEndEditEventArgs args)
{
}
	
{% endhighlight %}
{% endtabs %}

### CurrentCellValueChanged Event

[CurrentCellValueChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellValueChanged) event occurs whenever a value changes in TreeGridColumn that supports editing. 
[TreeGridCurrentCellValueChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellValueChangedEventArgs.html) has following members which provides information for `CurrentCellValueChanged` event.

* [Column](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellValueChangedEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellValueChangedEventArgs_Column) : Gets the Grid Column of the SfTreeGrid.

* [Record](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellValueChangedEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellValueChangedEventArgs_Record) : Gets the record of the corresponding cell value.

* [RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellValueChangedEventArgs.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellValueChangedEventArgs_RowColumnIndex) : Gets the value of the current RowColumnIndex.

{% tabs %}
{% highlight c# %}

this.treeGrid.CurrentCellValueChanged += TreeGrid_CurrentCellValueChanged;

void TreeGrid_CurrentCellValueChanged(object sender, TreeGridCurrentCellValueChangedEventArgs args)
{
}
	
{% endhighlight %}
{% endtabs %}

N> For TreeGridComboBoxColumn, you have to use the `CurrentCellDropDownSelectionChanged` event.

### CurrentCellDropDownSelectionChanged Event

[CurrentCellDropDownSelectionChanged](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellDropDownSelectionChanged) event occurs whenever the `SelectedItem` of `TreeGridComboBoxColumn` column changed.
[CurrentCellDropDownSelectionChangedEventArgs](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.CurrentCellDropDownSelectionChangedEventArgs.html) has following members which provides information for `CurrentCellDropDownSelectionChanged` event.

* [RowColumnIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.CurrentCellDropDownSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Grids_CurrentCellDropDownSelectionChangedEventArgs_RowColumnIndex)  - Gets the RowColumnIndex of the corresponding item that were selected from the drop-down control.
* [SelectedIndex](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.CurrentCellDropDownSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Grids_CurrentCellDropDownSelectionChangedEventArgs_SelectedIndex) - Gets the index of the corresponding item that were selected from the drop-down control.
* [SelectedItem](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.CurrentCellDropDownSelectionChangedEventArgs.html#Syncfusion_UI_Xaml_Grids_CurrentCellDropDownSelectionChangedEventArgs_SelectedItem) - Gets the data item that were selected from the drop-down control.

{% tabs %}
{% highlight c# %}

this.treeGrid.CurrentCellDropDownSelectionChanged += TreeGrid_CurrentCellDropDownSelectionChanged;

void TreeGrid_CurrentCellDropDownSelectionChanged(object sender, CurrentCellDropDownSelectionChangedEventArgs args)
{
}
	
{% endhighlight %}
{% endtabs %}

## Programmatically edit the cell

### BeginEdit

SfTreeGrid allows you to edit the cell programmatically by calling the [BeginEdit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_BeginEdit) method. Initially the[CurrentCell](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_CurrentCell) need to set before calling the `BeginEdit` method when the CurrentCell value is null.

{% tabs %}
{% highlight c# %}

this.treeGrid.Loaded += TreeGrid_Loaded;

void TreeGrid_Loaded(object sender, RoutedEventArgs e)
{            
	RowColumnIndex rowColumnIndex = new RowColumnIndex(2, 3);
	treeGrid.SelectionController.MoveCurrentCell(rowColumnIndex);
	treeGrid.SelectionController.CurrentCellManager.BeginEdit();
}

{% endhighlight %}
{% endtabs %}

### EndEdit

You can call the [EndEdit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.TreeGridCurrentCellManager.html#Syncfusion_UI_Xaml_TreeGrid_TreeGridCurrentCellManager_EndEdit_System_Boolean_) method to programmatically end edit. 

{% tabs %}
{% highlight c# %}

this.treeGrid.Loaded += TreeGrid_Loaded;

void TreeGrid_Loaded(object sender, RoutedEventArgs e)
{            
	RowColumnIndex rowColumnIndex = new RowColumnIndex(2, 3);
	treeGrid.SelectionController.MoveCurrentCell(rowColumnIndex);
	treeGrid.SelectionController.CurrentCellManager.EndEdit();
}
	
{% endhighlight %}
{% endtabs %}

### CancelEdit

You can use the [CurrentCellBeginEdit](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.TreeGrid.SfTreeGrid.html#Syncfusion_UI_Xaml_TreeGrid_SfTreeGrid_CurrentCellBeginEdit) event to cancel the editing operation for the corresponding cell.

{% tabs %}
{% highlight c# %}

this.treeGrid.CurrentCellBeginEdit += TreeGrid_CurrentCellBeginEdit;

void TreeGrid_CurrentCellBeginEdit(object sender, TreeGridCurrentCellBeginEditEventArgs args)
{
	var mappingName = treeGrid.Columns[args.RowColumnIndex.ColumnIndex].MappingName;
	var node = treeGrid.View.GetNodeAt(args.RowColumnIndex.RowIndex);

	if (args.RowColumnIndex == new RowColumnIndex(2, 2))
		args.Cancel = true;
}
	
{% endhighlight %}
{% endtabs %}

## ReadOnly

You can prevent users from modifying the contents of a treegrid cell by setting the [SfTreeGrid.IsReadOnly ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_IsReadOnly) property, but the user can able to perform copy and selection operation.

{% tabs %}
{% highlight xaml %}
        <treeGrid:SfTreeGrid Name="treeGrid"
                               ChildPropertyName="ReportsTo"
                               ColumnWidthMode="Star"
                               IsReadOnly="True"
                               AutoGenerateColumns="True"
                               AllowEditing="True"
                               ItemsSource="{Binding Employees}"
                               ParentPropertyName="ID"
                               SelfRelationRootValue="-1" />

{% endhighlight %}
{% highlight c# %}

this.treeGrid.IsReadOnly = true;

{% endhighlight %}
{% endtabs %}

You can enable or disable editing for particular column by setting [TreeGridColumn.IsReadOnly](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_IsReadOnly) property.

{% tabs %}
{% highlight xaml %}
<treeGrid:TreeGridTextColumn IsReadOnly="True" 
                                HeaderText="First Name" 
                                MappingName="FirstName" />
{% endhighlight %}
{% highlight c# %}

this.treeGrid.Columns["FirstName"].IsReadOnly = true;

{% endhighlight %}
{% endtabs %}

N> We should set the AllowEditing property to achieve the IsReadOnly behavior.
[TreeGridColumn.IsReadOnly ](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.GridColumnBase.html#Syncfusion_UI_Xaml_Grids_GridColumnBase_IsReadOnly)takes higher priority than [SfTreeGrid.IsReadOnly](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Grids.SfGridBase.html#Syncfusion_UI_Xaml_Grids_SfGridBase_IsReadOnly).

