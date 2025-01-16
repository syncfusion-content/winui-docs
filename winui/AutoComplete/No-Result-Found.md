---
layout: post
title: No Result Found in WinUI AutoComplete control | Syncfusion&reg;
description: Learn how to use NoResultsFoundTemplate and NoResultsFoundContent in Syncfusion&reg; WinUI AutoComplete control.
platform: winui
control: SfAutoComplete
documentation: ug
---

# No Result Found in WinUI AutoComplete (SfAutoComplete)

When the entered item is not in the suggestion list, SfAutoComplete displays a text indicating there is no search results found. We can set the desire text to be displayed for indicating no results found with the `NoResultsFoundContent` and `NoResultsFoundTemplate` properties. 

## NoResultsFoundContent 

We can customize the desire text to be displayed for indicating no results found by using the `NoResultsFoundContent` property. The below code shows how to include the `NoResultsFoundContent` in AutoComplete.

{% tabs %}
{% highlight xaml %}

 <editors:SfAutoComplete  Header="AutoComplete with No Result Found Text" 
                          PlaceholderText="Search a country" 
                          DisplayMemberPath="Country" 
                          TextMemberPath="Country"
                          Width="300"   
                          NoResultsFoundContent="Not Found"
                          ItemsSource="{Binding ContinentList }">
 </editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with NoResultsFoundContent](No_Results_Found_images\No-Results-Found-Content.png)

## NoResultsFoundTemplate 

We can customize the appearance of the desire text to be displayed for indicating no results found by using the `NoResultsFoundTemplate` property. The below code shows how to include the `NoResultsFoundTemplate` in AutoComplete.

{% tabs %}
{% highlight xaml %}

  <editors:SfAutoComplete  Header="AutoComplete with No Result Found Template"
                           PlaceholderText="Search a country" 
                           DisplayMemberPath="Country" 
                           TextMemberPath="Country"
                           Width="300"    
                           ItemsSource="{Binding ContinentList }">
            <editors:SfAutoComplete.NoResultsFoundTemplate>
                <DataTemplate>
                    <TextBlock Text="Not Found" 
                        Foreground="Red" 
                        FontStyle="Italic" 
                        FontSize="20"  />
                </DataTemplate>
            </editors:SfAutoComplete.NoResultsFoundTemplate>
 </editors:SfAutoComplete>

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete control with NoResultsFoundTemplate](No_Results_Found_images\No-Results-Found-Template.png)

N> While setting `NoResultsFoundContent` and `NoResultsFoundTemplate` properties. High priority is given to `NoResultsFoundTemplate`.