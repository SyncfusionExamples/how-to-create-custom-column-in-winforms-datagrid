# How to customize the column format in WinForms DataGrid (SfDataGrid)

[SfDataGrid](https://help.syncfusion.com/cr/windowsforms/Syncfusion.WinForms.DataGrid.SfDataGrid.html?_ga=2.113253391.967019853.1668146580-766490130.1650530957&_gl=1*4g8syb*_ga*NzY2NDkwMTMwLjE2NTA1MzA5NTc.*_ga_WC4JKKPHH0*MTY2ODE1ODI2OC4yOTcuMS4xNjY4MTY1NDc3LjAuMC4w) allows you to create and assign custom format for the columns through the [IDataGridFormatProvider](https://help.syncfusion.com/cr/windowsforms/Syncfusion.WinForms.DataGrid.IDataGridFormatProvider.html?_ga=2.154793776.967019853.1668146580-766490130.1650530957&_gl=1*kfpypb*_ga*NzY2NDkwMTMwLjE2NTA1MzA5NTc.*_ga_WC4JKKPHH0*MTY2ODE1ODI2OC4yOTcuMS4xNjY4MTY1NDc3LjAuMC4w) interface. The [GridColumnBase.FormatProvider](https://help.syncfusion.com/cr/windowsforms/Syncfusion.WinForms.DataGrid.GridColumnBase.html?_ga=2.154793776.967019853.1668146580-766490130.1650530957&_gl=1*kfpypb*_ga*NzY2NDkwMTMwLjE2NTA1MzA5NTc.*_ga_WC4JKKPHH0*MTY2ODE1ODI2OC4yOTcuMS4xNjY4MTY1NDc3LjAuMC4w#Syncfusion_WinForms_DataGrid_GridColumnBase_FormatProvider) property can be used to set custom format for the columns.

```
sfDataGrid1.Columns["Value"].Format = "00,00%";
sfDataGrid1.Columns["Value"].FormatProvider = new CustomFormatter();public class CustomFormatter : IDataGridFormatProvider
{
    public object Format(string format, GridColumnBase gridColumn, object record, object value)
    {
        if (value == null)
        {
            throw new ArgumentNullException((value == null) ? "format" : "args");
        }
 
        if (gridColumn is GridColumn && (gridColumn as GridColumn).MappingName == "Value")
        {
            var orderInfo = record as OrderInfo;
                return (Convert.ToDecimal((orderInfo.Value.ToString()))).ToString("0.00%");
        }
        return value.ToString();
    }
    public object GetFormat(Type formatType)
    {
        return this;
    }
    public string Format(string format, object arg, IFormatProvider formatProvider)
    {
        throw new NotImplementedException();
    }
}
```