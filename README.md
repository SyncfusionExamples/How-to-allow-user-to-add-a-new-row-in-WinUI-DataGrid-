# How to allow user to add a new row in WinUI DataGrid?

## About the sample

This example describes how to allow user to add a new row in WinUI DataGrid.

[WinUI DataGrid](https://www.syncfusion.com/winui-controls/datagrid) (SfDataGrid) provides built-in row called AddNewRow. It allows user to add a new row to underlying collection. You can enable or disable by setting [SfDataGrid.AddNewRowPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_AddNewRowPosition) property. You can also set the position of built-in AddNewRow through AddNewRowPosition property.

When you start editing in AddNewRow, the WinUI DataGrid control creates an instance for the underlying data object and adds it to underlying collection when editing completed. So, the underlying data object must be defined with default constructor.

You can commit or cancel a new row from being added by pressing the **Enter** and **Esc** key respectively.

``` Xaml

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AddNewRowPosition="Top"
                       AllowEditing="True"
                       ItemsSource="{Binding ProductInfo}">

```

![Shows the new row added in SfDataGrid](AddNewRow.gif)

#### Note: The underlying data object must be defined with default constructor.

## Add a new row programmatically to WinUI DataGrid

You can add a new row by using [SfDataGrid.View.AddNew](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.CollectionViewAdv.html#Syncfusion_UI_Xaml_Data_CollectionViewAdv_AddNew) and [SfDataGrid.View.CommitNew](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Data.CollectionViewAdv.html#Syncfusion_UI_Xaml_Data_CollectionViewAdv_CommitNew) methods.

``` C#

private void Button_Click(object sender, RoutedEventArgs e)
{
     this.dataGrid.View.AddNew();
     this.dataGrid.View.CommitNew();
}

```

## Customize default string of built-in AddNewRow

WinUI DataGrid enables you to customize the watermark text of AddNewRow by changing value of AddNewRowText in Resource Designer.

You can go through this [user guide](https://help.syncfusion.com/winui/datagrid/crud-operations#customizing-addnewrow-text-using-default-resource-file) to know more about customizing default string of AddNewRow’s text.

## Initializing default values for AddNewRow

WinUI DataGrid allows you to set the default values for AddNewRow while initiating through [AddNewRowInitiatingEventArgs.NewObject](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.AddNewRowInitiatingEventArgs.html#Syncfusion_UI_Xaml_DataGrid_AddNewRowInitiatingEventArgs_NewObject) property in [SfDataGrid.AddNewRowInitiating](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.DataGrid.SfDataGrid.html#Syncfusion_UI_Xaml_DataGrid_SfDataGrid_AddNewRowInitiating) event.

``` C#

dataGrid.AddNewRowInitiating += OnAddNewRowInitiating;

private void OnAddNewRowInitiating(object sender, Syncfusion.UI.Xaml.DataGrid.AddNewRowInitiatingEventArgs e)
{
     var data = e.NewObject as ProductSalesDetails;
     data.Product = "Car";
     data.Country = "UK";
     data.State = "Scotland";
     data.Quantity = 5;
     data.Discount = 12;
     data.Amount = 200000;
}

```


![Shows the default values while AddNewRow initiating in SfDataGrid](DefaultValuesAddNewRow.png)

Take a moment to peruse the [WinUI DataGrid - Add new rows](https://help.syncfusion.com/winui/datagrid/crud-operations#add-new-rows) documentation, where you can find about add new rows with code examples.

## Requirements to run the demo
Visual Studio 2019 and above versions
