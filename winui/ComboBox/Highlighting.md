---
layout: post
title: Highlighting Feature in WinUI ComboBox control | Syncfusion
description: Learn here all about Highlighting Feature in Syncfusion WinUI ComboBox control in a WinUI application.
platform: winui
control: SfComboBox
documentation: UG
---

# Highlighting in WinUI ComboBox (SfComboBox)

Highlight matching characters in the suggestion list to pick an item with more clarity. There are two ways to highlight the matching text:

* **Highlight beginning text**
* **Highlight all occurrences of the search text**

N> The [Syncfusion.Editors.WinUI](https://www.nuget.org/packages/Syncfusion.Editors.WinUI) NuGet package is required to use the `SfComboBox` control. Refer to [Getting Started](https://help.syncfusion.com/winui/combobox/getting-started) for setup details.

N> Text highlighting requires `IsEditable="true"` and `IsFilteringEnabled="True"`. Add `using Syncfusion.UI.Xaml.Editors;` in C# to access the `ComboBoxTextHighlightMode` and `ComboBoxTextSearchMode` enums.

The text highlight can be customized using the following properties:

* **HighlightedTextForeground** - Sets the color of the highlighted text for differentiating the highlighted characters.
* **HighlightedTextFontStyle** - Sets the font style of the highlighted text.
* **HighlightedTextFontWeight** - Sets the font weight of the highlighted text.
* **HighlightedTextFontSize** - Sets the font size of the highlighted text.

{% tabs %}
{% highlight xaml %}
    <editors:SfComboBox 
                            x:Name="comboBox"
                            DisplayMemberPath="Name"
                            IsEditable="true"
                            IsFilteringEnabled="True"                       
                            TextHighlightMode="Matched"                                
                            TextSearchMode="StartsWith"                               
                            HighlightedTextFontSize="15"                               
                            HighlightedTextFontStyle="Italic"                               
                            HighlightedTextFontWeight="Medium"                                
                            HighlightedTextForeground="Red"                                
                            ItemsSource="{Binding SocialMedias}">       
    </editors:SfComboBox>

{% endhighlight %}
{% highlight c# %}
        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled = true;
        comboBox.IsFilteringEnabled = true;          
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Unmatched;
        comboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;
        comboBox.HighlightedTextFontSize = 10;
        comboBox.HighlightedTextFontStyle = FontStyle.Normal;
        comboBox.HighlightedTextFontWeight = FontWeights.ExtraLight;
        comboBox.HighlightedTextForeground = Color.Red;
{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text highlighting properties](Highlighting_images/winui-combobox-highlightingproperties.png)



### **Highlight beginning text**
It highlights the matches that start with the typed characters in the suggestion list.

{% tabs %}
{% highlight xaml %}

<editors:SfComboBox     x:Name="comboBox"                        
                        DisplayMemberPath="Name" 
                        IsEditable="true"
                        IsFilteringEnabled="True"                            
                        TextHighlightMode="Matched"
                        TextSearchMode="StartsWith"                           
                        HighlightedTextForeground="Red"                               
                        ItemsSource="{Binding Countries}">
</editors:SfComboBox>
{% endhighlight %}
{% highlight c# %}

comboBox.DisplayMemberPath = "Name";
comboBox.IsEnabled=true;
comboBox.IsFilteringEnabled = true;
comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Matched;
comboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;
comboBox.HighlightedTextForeground = Color.Red;


{% endhighlight %}
{% endtabs %}

### Searching with one character

![WinUI ComboBox text highlighting based on beginning text one character](Highlighting_images/winui-combobox-textsearchmode-startswith-onecharacter.png)

### Searching with more than one character

![WinUI ComboBox text highlighting based on beginning text more than one character](Highlighting_images/winui-combobox-textsearchmode-startswith-morethanonecharacter.png)




### **Highlight all occurrences of the search text**
It highlights all the matches that contain the typed characters in the suggestion list. 



{% tabs %}
{% highlight xaml %}

<editors:SfComboBox  x:Name="comboBox"                         
                DisplayMemberPath="Name" 
                IsEditable="true"
                IsFilteringEnabled="True"                             
                TextHighlightMode="Matched"
                TextSearchMode="Contains"                           
                HighlightedTextForeground="Red"                               
                ItemsSource="{Binding Wonders}">
</editors:SfComboBox>

{% endhighlight %}
{% highlight c# %}

        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
        comboBox.IsFilteringEnabled = true;
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Matched;
        comboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;
        comboBox.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

### Searching with one character
![WinUI ComboBox text highlighting based on contains one character](Highlighting_images/winui-combobox-textsearchmode-contains-one.png)

### Searching with more than one character

![WinUI ComboBox text highlighting based on contains more than one character](Highlighting_images/winui-combobox-textsearchmode-contains-morethanone.png)


## Highlighting search text mode
The [TextHighlightMode](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Editors.SfComboBox.html#Syncfusion_UI_Xaml_Editors_SfComboBox_TextHighlightMode) property controls which portion of the text is highlighted. The default value is `None`. The available modes are:
* **None** - This mode does not highlight any text.
* **Matched** - This mode highlights the text that matches the user input.
* **Unmatched** - This mode highlights the text that does not match the user input.

###  TextSearchMode="StartsWith"
{% tabs %}
{% highlight xaml %}
               <editors:SfComboBox  x:Name="comboBox"                          
                                DisplayMemberPath="Name"  
                                IsEditable="true"
                                IsFilteringEnabled="True"                             
                                TextHighlightMode="Unmatched"
                                TextSearchMode="StartsWith"                              
                                HighlightedTextForeground="Red"                                
                                ItemsSource="{Binding OlympicGames}">
              </editors:SfComboBox>
{% endhighlight %}
{% highlight c# %}

        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
        comboBox.IsFilteringEnabled = true;
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Unmatched;
        comboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;
        comboBox.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text highlighting based on unmatched mode with one character](Highlighting_images/winui-combobox-texthighlightmode-unmatched-startswith.png)

###  TextSearchMode="Contains"
{% tabs %}
{% highlight xaml %}
               <editors:SfComboBox   x:Name="comboBox"                         
                                DisplayMemberPath="Name" 
                                IsEditable="true"
                                IsFilteringEnabled="True"                              
                                TextHighlightMode="Unmatched"
                                TextSearchMode="Contains"                              
                                HighlightedTextForeground="Red"                                
                                ItemsSource="{Binding OlympicGames}">
              </editors:SfComboBox>
{% endhighlight %}
{% highlight c# %}

        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
        comboBox.IsFilteringEnabled = true;
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Unmatched;
        comboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;
        comboBox.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text highlighting based on unmatched mode with one character](Highlighting_images/winui-combobox-texthighlightmode-unmatched-contains.png)





