---
layout: post 
title: Content Types in WinUI AvatarView control | Syncfusion
description: Learn about the available content types and how to set values for them in the WinUI AvatarView control.
platform: WinUI
control: AvatarView
documentation: ug
---

# Content Types in WinUI AvatarView

The [SfAvatarView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html) control supports five types of content: [Default](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_Default), [Initials](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_Initials), [CustomImage](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_CustomImage), [AvatarCharacter](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_AvatarCharacter), and [GroupView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_Group).

## Default

The default content type displays the [Avatar1](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarCharacter.html#Syncfusion_UI_Xaml_Core_AvatarCharacter_Avatar1) character image when initializing the control without the initials, custom image, or group source.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView />

{% endhighlight %} 
{% highlight C# %}

SfAvatarView avatarView = new SfAvatarView();
           
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control](avatarview_images/winui_avatarview.png)

## Initials 

The Initials content type displays initials in the AvatarView. To use this content type, you must provide a value for the [AvatarName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_AvatarName) property, which sets the initials to be displayed in the avatar view. The initials will be formatted accordingly depending on the specified [InitialsType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_InitialsType) property.

### InitialsType

The [InitialsType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_InitialsType) property includes two types:

[SingleCharacter](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarInitialsType.html#Syncfusion_UI_Xaml_Core_AvatarInitialsType_SingleCharacter) - Used to display a single character in the avatar.
[DoubleCharacter](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarInitialsType.html#Syncfusion_UI_Xaml_Core_AvatarInitialsType_DoubleCharacter) - Used to display two characters in the avatar.

**Single character**

The single character initials type displays the first character of the [AvatarName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_AvatarName) property value as the avatar.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="Initials"
                         AvatarSize="ExtraLarge"
                         AvatarName="Alex"
                         Background="Bisque">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}
             
SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarName = "Alex";
avatarView.ContentType = AvatarContentType.Initials;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.Background = new SolidColorBrush(Colors.Bisque);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with SingleCharacter](avatarview_images/winui_single_character_initialstype_avatarview.png)

**Double character**

The double character initials type displays a two-character text as an avatar set in the [AvatarName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_AvatarName) property. If the AvatarName consists of a single word, that word's first and last letters will be displayed. However, if the [AvatarName](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_AvatarName) contains two or more words, the first letter of the first word and the first letter of the second word will be displayed.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="Initials"
                         AvatarSize="ExtraLarge"
                         AvatarName="Alex"
                         InitialsType="DoubleCharacter"
                         Background="Bisque">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}
          
SfAvatarView avatarView = new SfAvatarView();
avatarView.AvatarName = "Alex";
avatarView.ContentType = AvatarContentType.Initials;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.InitialsType = AvatarInitialsType.DoubleCharacter;
avatarView.Background = new SolidColorBrush(Colors.Bisque);

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with DoubleCharacter](avatarview_images/winui_double_character_initialstype_avatarview.png)

## Custom image

Add any custom image as the avatar by using the [ImageSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_ImageSource) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="CustomImage"
                         AvatarSize="ExtraLarge"
                         ImageSource="Images\person.png">
</syncfusion:SfAvatarView>

{% endhighlight %} 
{% highlight C# %}

SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.CustomImage;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.ImageSource = new BitmapImage(new Uri("ms-appx:///Images\\person.png"));
           
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with custom image](avatarview_images/winui_imagesource_avatarview.png)

## Avatar character

Set the pre-defined avatar character images as avatar by using the [AvatarCharacter](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_AvatarCharacter) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAvatarView ContentType="AvatarCharacter"
                         AvatarSize="ExtraLarge"
                         AvatarCharacter="Avatar15">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}
            
SfAvatarView avatarView = new SfAvatarView();
avatarView.ContentType = AvatarContentType.AvatarCharacter;
avatarView.AvatarSize = AvatarSize.ExtraLarge;
avatarView.AvatarCharacter = AvatarCharacter.Avatar15;
            
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with avatar character](avatarview_images/winui_avatar_character_avatarview.png)

## Group view 

The [Group](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.AvatarContentType.html#Syncfusion_UI_Xaml_Core_AvatarContentType_Group) content type allows you to display up to three images or initials within a single avatar view. To use this content type, you must set the following properties.

[GroupSource](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_GroupSource): Used to set the ItemsSource for the group view.
[InitialsMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_InitialsMemberPath): Used to set the initials for the group view.
[InitialsColorMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_InitialsColorMemberPath): Used to set the initials color for the group view.
[BackgroundColorMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_BackgroundColorMemberPath): Used to set the background color for the group view.
[ImageSourceMemberPath](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Core.SfAvatarView.html#Syncfusion_UI_Xaml_Core_SfAvatarView_ImageSourceMemberPath): Used to set the image source for the group view.

The following code example illustrates how to create an ItemsSource for a group avatar view.

{% tabs %}
{% highlight c# %}

public class Employee
{
   public string Name { get; set; }

   public string ImageSource { get; set; }

   public Color Background { get; set; }

   public Color InitialsColor { get; set; }
}

public class EmployeeViewModel
{
   public ObservableCollection<Employee> CollectionImage { get; set; }

   public EmployeeViewModel()
   {
      CollectionImage = new ObservableCollection<Employee>();
      CollectionImage.Add(new Employee { ImageSource="mike.png" });
      CollectionImage.Add(new Employee {  Name="Alex", Background=ColorHelper.FromArgb(0xFF, 0xD6, 0xE8, 0xD7), InitialsColor=ColorHelper.FromArgb(0xFF, 0x24, 0x4F, 0x23) });
      CollectionImage.Add(new Employee { ImageSource="ellanaa.png" });
   }    
}

{% endhighlight %}
{% endtabs %}

The following code example illustrates how to set the group source and member paths for the avatar view.

{% tabs %}
{% highlight xaml %}

<Page.DataContext>
    <local:EmployeeViewModel/>
</Page.DataContext>

<syncfusion:SfAvatarView ContentType="Group"   
                         GroupSource="{Binding CollectionImage}"
                         InitialsMemberPath="Name"
                         BackgroundColorMemberPath="Background"
                         ImageSourceMemberPath="ImageSource"
                         InitialsColorMemberPath="InitialsColor"
                         AvatarSize="ExtraLarge">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}

public partial class MainWindow : Window
{
   public MainPage()
   {
      Grid grid = new Grid();
      EmployeeViewModel employeeViewModel = new EmployeeViewModel();
      grid.DataContext = employeeViewModel;
      SfAvatarView avatarView = new SfAvatarView();
      avatarView.ContentType = AvatarContentType.Group;
      avatarView.GroupSource = employee.CollectionImage;
      avatarView.ImageSourceMemberPath = "ImageSource";
      avatarView.InitialsMemberPath = "Name";
      avatarView.BackgroundColorMemberPath = "Background";
      avatarView.InitialsColorMemberPath = "InitialsColor";
      avatarView.AvatarSize = AvatarSize.ExtraLarge;
      grid.Children.Add(avatarView);
   }
}

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with Group Content Type](avatarview_images/winui_group_contenttype_avatarview.png)
