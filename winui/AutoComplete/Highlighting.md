---
layout: post
title: Highlighting Feature in WinUI AutoComplete control | Syncfusion
description: Learn here all about Highlighting Feature in Syncfusion WinUI AutoComplete control into WinUI application.
platform: winui
control: SfAutoComplete
documentation: UG
---

# Highlighting in WinUI AutoComplete(SfAutoComplete)

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
    <editors:SfAutoComplete DisplayMemberPath="Name"                       
                            TextHighlightMode="Matched"                                
                            TextSearchMode="StartsWith"                               
                            HighlightedTextFontSize="15"                               
                            HighlightedTextFontStyle="Italic"                               
                            HighlightedTextFontWeight="Medium"                                
                            HighlightedTextForeground="Red"                                
                            ItemsSource="{Binding SocialMedias}">       
    </editors:SfAutoComplete>

{% endhighlight %}
{% highlight C# %}
        autoComplete.DisplayMemberPath = "Name";
        autoComplete.TextMemberPath = "Name";
        autoComplete.TextHighlightMode = AutoCompleteTextHighlightMode.Unmatched;
        autoComplete.TextSearchMode = AutoCompleteTextSearchMode.Contains;
        autoComplete.HighlightedTextFontSize = 10;
        autoComplete.HighlightedTextFontStyle = FontStyle.Normal;
        autoComplete.HighlightedTextFontWeight = FontWeights.ExtraLight;
        autoComplete.HighlightedTextForeground = Color.Red;
{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete text highlighting properties](Highlighting_images/winui-autocomplete-highlightingproperties.png)



### **Highlight beginning text**
It highlights the matches that starts with the typed characters in suggestion list.

{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete                             
                        DisplayMemberPath="Name"                             
                        TextHighlightMode="Matched"
                        TextSearchMode="StartsWith"                           
                        HighlightedTextForeground="Red"                               
                        ItemsSource="{Binding Countries}">
</editors:SfAutoComplete>
{% endhighlight %}
{% highlight C# %}

autoComplete.DisplayMemberPath = "Name";
autoComplete.TextHighlightMode = AutoCompleteTextHighlightMode.Matched;
autoComplete.TextSearchMode = AutoCompleteTextSearchMode.StartsWith;
autoComplete.HighlightedTextForeground = Color.Red;


{% endhighlight %}
{% endtabs %}

### Searching with one character

![WinUI AutoComplete text highlighting based on begining text one character](Highlighting_images/winui-autocomplete-textsearchmode-startswith-onecharacter.png)

### Searching with more than one character

![WinUI AutoComplete text highlighting based on begining text more than one character](Highlighting_images/winui-autocomplete-textsearchmode-startswith-morethanonecharacter.png)




### **Highlight all occurance of search text**
It highlights all the matches that contains the typed characters in suggestion list. 



{% tabs %}
{% highlight XAML %}

<editors:SfAutoComplete                           
                DisplayMemberPath="Name”                              
                TextHighlightMode="Matched"
                TextSearchMode="Contains"                           
                HighlightedTextForeground="Red"                               
                ItemsSource="{Binding Wonders}">
</editors:SfAutoComplete>

{% endhighlight %}
{% highlight C# %}

        autoComplete.DisplayMemberPath = "Name";
        autoComplete.TextHighlightMode = AutoCompleteTextHighlightMode.Matched;
        autoComplete.TextSearchMode = AutoCompleteTextSearchMode.Contains;
        autoComplete.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

### Searching with one character
![WinUI AutoComplete text highlighting based on contains one character](Highlighting_images/winui-autocomplete-textsearchmode-contains-one.png)

### Searching with more than one character

![WinUI AutoComplete text highlighting based on contains more than one character](Highlighting_images/winui-autocomplete-textsearchmode-contains-morethanone.png)


## **Highlighting search text mode** 
 The SfAutoComplete provides the following modes.
* **None** - This mode doesnot highlight any text.
* **Matched** - This mode highlights the text that matches the user input.
* **Unmatched** - This mode highlights the text that doesnot matches the user input.

###  TextSearchMode="StartsWith"          
{% tabs %}
{% highlight XAML %}
               <editors:SfAutoComplete                            
                                DisplayMemberPath="Name"                               
                                TextHighlightMode="Unmatched"
                                TextSearchMode="StartsWith"                              
                                HighlightedTextForeground="Red"                                
                                ItemsSource="{Binding OlympicGames}">
              </editors:SfAutoComplete>
{% endhighlight %}
{% highlight C# %}

        autoComplete.DisplayMemberPath = "Name";
        autoComplete.TextHighlightMode = AutoCompleteTextHighlightMode.Unmatched;
        autoComplete.TextSearchMode = AutoCompleteTextSearchMode.StartsWith;
        autoComplete.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete text highlighting based on unmatched mode with one character](Highlighting_images/winui-autocomplete-texthighlightmode-unmatched-startswith.png)

###  TextSearchMode="Contains"           
{% tabs %}
{% highlight XAML %}
               <editors:SfAutoComplete                            
                                DisplayMemberPath="Name"                               
                                TextHighlightMode="Unmatched"
                                TextSearchMode="Contains"                              
                                HighlightedTextForeground="Red"                                
                                ItemsSource="{Binding OlympicGames}">
              </editors:SfAutoComplete>
{% endhighlight %}
{% highlight C# %}

        autoComplete.DisplayMemberPath = "Name";
        autoComplete.TextHighlightMode = AutoCompleteTextHighlightMode.Unmatched;
        autoComplete.TextSearchMode = AutoCompleteTextSearchMode.Contains;
        autoComplete.HighlightedTextForeground = Color.Red;

{% endhighlight %}
{% endtabs %}

![WinUI AutoComplete text highlighting based on unmatched mode with one character](Highlighting_images/winui-autocomplete-texthighlightmode-unmatched-contains.png)





