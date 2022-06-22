---
layout: post
title: Highlighting Feature in WinUI Combobox control | Syncfusion
description: Learn here all about Highlighting Feature in Syncfusion WinUI Combobox control into WinUI application.
platform: winui
control: SfComboBox
documentation: UG
---

# Highlighting in WinUI ComboBox(SfComboBox)

Highlight matching characters in a suggestion list to pick an item with more clarity. There are two ways to highlight the matching text:

* **Highlight beginning text**
* **Highlight all occurance of search text**


The text highlight can be indicated with various customizing styles by enabling the below properties. They are

* **HighlightedTextColor** - sets the color of the highlighted text for differentiating the highlighted characters.

* **HighlightedTextFontStyle** - sets the font style of the highlighted text.
        
* **HighlightedTextFontWeight** - sets the font weight of the highlighted text.

* **HightlightedTextFontSize** - sets the font size of the highlighted text.

{% tabs %}
{% highlight XAML %}
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
{% highlight C# %}
        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
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
It highlights the matches that starts with the typed characters in suggestion list.

{% tabs %}
{% highlight XAML %}

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
{% highlight C# %}

comboBox.DisplayMemberPath = "Name";
comboBox.IsEnabled=true;
comboBox.IsFilteringEnabled = true;
comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Matched;
comboBox.TextSearchMode = ComboBoxTextSearchMode.StartsWith;
comboBox.HighlightedTextForeground = Color.Red;


{% endhighlight %}
{% endtabs %}

### Searching with one character

![WinUI ComboBox text highlighting based on begining text one character](Highlighting_images/winui-combobox-textsearchmode-startswith-onecharacter.png)

### Searching with more than one character

![WinUI ComboBox text highlighting based on begining text more than one character](Highlighting_images/winui-combobox-textsearchmode-startswith-morethanonecharacter.png)




### **Highlight all occurance of search text**
It highlights all the matches that contains the typed characters in suggestion list. 



{% tabs %}
{% highlight XAML %}

<editors:SfComboBox  x:Name="comboBox"                         
                DisplayMemberPath="Name” 
                IsEditable="true"
                IsFilteringEnabled="True"                             
                TextHighlightMode="Matched"
                TextSearchMode="Contains"                           
                HighlightedTextForeground="Red"                               
                ItemsSource="{Binding Wonders}">
</editors:SfComboBox>

{% endhighlight %}
{% highlight C# %}

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


## **Highlighting search text mode** 
 The SfComboBox provides the following modes.
* **None** - This mode doesnot highlight any text.
* **Matched** - This mode highlights the text that matches the user input.
* **Unmatched** - This mode highlights the text that doesnot matches the user input.

###  TextSearchMode="StartsWith"          
{% tabs %}
{% highlight XAML %}
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
{% highlight C# %}

        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
        comboBox.IsFilteringEnabled = true;
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Unmatched;
        comboBox.TextSearchMode = AComboBoxTextSearchMode.StartsWith;
        comboBox.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text highlighting based on unmatched mode with one character](Highlighting_images/winui-combobox-texthighlightmode-unmatched-startswith.png)

###  TextSearchMode="Contains"           
{% tabs %}
{% highlight XAML %}
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
{% highlight C# %}

        comboBox.DisplayMemberPath = "Name";
        comboBox.IsEnabled=true;
        comboBox.IsFilteringEnabled = true;
        comboBox.TextHighlightMode = ComboBoxTextHighlightMode.Unmatched;
        comboBox.TextSearchMode = ComboBoxTextSearchMode.Contains;
        comboBox.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI ComboBox text highlighting based on unmatched mode with one character](Highlighting_images/winui-combobox-texthighlightmode-unmatched-contains.png)





