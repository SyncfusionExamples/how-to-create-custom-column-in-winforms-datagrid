# How to create custom column in winforms datagrid

This repositories contains the samples to create custom column in [WinForms DataGrid](https://www.syncfusion.com/winforms-ui-controls/datagrid).

You can create a new column by deriving [GridColumn](https://help.syncfusion.com/cr/windowsforms/Syncfusion.WinForms.DataGrid.GridColumn.html) and create new a cell renderer by overriding the predefined renderer in `SfDataGrid`. The following steps describe how to create a sparkline column as a custom column.

### Creating custom column

You can create a custom column by overriding a new class from the `GridColumn` class.

### Creating renderer

After creating a custom column, you need to create renderer for the custom column. You can create custom renderer by deriving the [GridCellRendererBase](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Windows.Forms.Grid.GridCellRendererBase.html) class.

### Adding the custom renderer to CellRenderers collection

By using the following code, you can add the previous created custom renderer to the [SfDataGrid.CellRenderers](https://help.syncfusion.com/cr/windowsforms/Syncfusion.Windows.Forms.Grid.GridCellRendererCollection.html) collection.

### Loading custom column

By using the following code, you can define the custom column in SfDataGrid.