---
layout: post
title: Grouping in WinUI AutoComplete control | Syncfusion
description: Learn here all about Grouping support in Syncfusion WinUI AutoComplete (multi-select AutoComplete) control with UI grouping and more.
platform: winui
control: SfAutoComplete
documentation: ug
---

# Grouping in WinUI AutoComplete (SfAutoComplete)

This section explains about the grouping support available in [AutoComplete](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfAutoComplete.html).

## Enable grouping

To display grouped data in `AutoComplete` control, set the [ItemsSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_ItemsSource) property to a [CollectionViewSource](https://docs.microsoft.com/en-us/windows/winui/api/microsoft.ui.xaml.data.collectionviewsource?view=winui-3.0) with the `IsSourceGrouped` property set to `true`. The `CollectionViewSource` acts as a proxy over the collection class to enable grouping support. We should use the Custom Filter for customize the grouping of `AutoComplete` control.

Also, the appearance of groups in a drop-down list can be defined by using the [GroupStyle](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfDropDownListBase.html#Syncfusion_UI_Xaml_Editors_SfDropDownListBase_GroupStyle) property. The default value of `GroupStyle` is `null`.

In the following example, define a `CollectionViewSource` that wraps a collection of vegetable objects and specifies a property to group on (the vegetable category). Then, bind the `View` property of `CollectionViewSource` to the `ItemsSource` property of `AutoComplete` control.

{% tabs %}
{% highlight c# %}

//Model.cs
public class Vegetable
{
    public string Name { get; set; }
    public string Category { get; set; }
}

//ViewModel.cs
public class VegetablesViewModel
{
    public object Vegetables { get; set; }

    public VegetablesViewModel()
    {
        var vegetables = new ObservableCollection<Vegetable>();
        vegetables.Add(new Vegetable {
            Name = "Cabbage",
            Category = "Leafy and Salad",
        });
        vegetables.Add(new Vegetable {
            Name = "Chickpea",
            Category = "Beans",
        });
        vegetables.Add(new Vegetable {
            Name = "Garlic",
            Category = "Bulb and Stem",
        });
        vegetables.Add(new Vegetable {
            Name = "Green bean",
            Category = "Beans",
        });
        vegetables.Add(new Vegetable {
            Name = "Horse gram",
            Category = "Beans",
        });
        vegetables.Add(new Vegetable {
            Name = "Nopal",
            Category = "Bulb and Stem",
        });
        vegetables.Add(new Vegetable {
            Name = "Onion",
            Category = "Bulb and Stem",
        });
        vegetables.Add(new Vegetable {
            Name = "Pumpkins",
            Category = "Leafy and Salad",
        });
        vegetables.Add(new Vegetable {
            Name = "Spinach",
            Category = "Leafy and Salad",
        });

        //Groups the elements based on value of Vegetable's Category.
        this.Vegetables = vegetables.GroupBy(item => item.Category);
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight C# %}

public class CustomGroupFilter : IAutoCompleteFilterBehavior
{
    public async Task<object> GetMatchingItemsAsync(SfAutoComplete source, AutoCompleteFilterInfo filterInfo)
    {
        List<Vegetable> list = new List<Vegetable>();
        IEnumerable itemsSource = source.ItemsSource as IEnumerable;

        list.AddRange(from item in itemsSource.Cast<Vegetable>()
                      let filteritem = this.GetStringFromMemberPath(item, "Name")
                      where filteritem.Contains(filterInfo.Text, StringComparison.CurrentCultureIgnoreCase)
                      select item);

        var collectionViewSource = new CollectionViewSource();
        collectionViewSource.Source = list.GroupBy(item => item.Category);
        collectionViewSource.IsSourceGrouped = true;

        return collectionViewSource.View;
    }

    private string GetStringFromMemberPath(object item, string path)
    {
        string value = item.ToString();
        if (!string.IsNullOrEmpty(path))
        {
            value = item.GetType()?.GetRuntimeProperty(path)?.GetValue(item).ToString();
        }

        return value;
    }
}


{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete
    PlaceholderText="Select a Vegetable"
    ItemsSource="{Binding Vegetables}">
    <editors:SfAutoComplete.FilteringBehavior>
        <local:CustomGroupFilter/>
    </editors:SfAutoComplete.FilteringBehavior>
    <editors:SfAutoComplete.GroupStyle>
        <GroupStyle>
            <GroupStyle.HeaderTemplate>
                <DataTemplate>
                    <Grid>
                        <TextBlock
                            Grid.Column="1"
                            Margin="8,0,0,0"
                            FontWeight="SemiBold"
                            FontSize="14"
                            FontFamily="{ThemeResource ContentControlThemeFontFamily}"
                            VerticalAlignment="Center"
                            Text="{Binding Key}" />
                    </Grid>
                </DataTemplate>
            </GroupStyle.HeaderTemplate>
        </GroupStyle>
    </editors:SfAutoComplete.GroupStyle>
    
</editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![Grouping the vegetables based on its category.](Grouping_images/winui-autocomplete-groupStyle.png)
