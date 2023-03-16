---
layout: post 
title: Content Types in WinUI AvatarView control | Syncfusion
description: Learn about the available content types and how to set values for them in the WinUI AvatarView control.
platform: WinUI
control: AvatarView
documentation: ug
---

# Content Types in WinUI AvatarView

The AvatarView control supports five different types of content: `Default`, `Initials`, `CustomImage`, `AvatarCharacter`, and `GroupView`.

## Default

Default content type is used for displaying the `Avatar1` character image when initializing without the initials, custom image, or group view types.

{% tabs %}
{% highlight xaml %}

<Grid>
<syncfusion:SfAvatarView />
</Grid>

{% endhighlight %} 
{% highlight C# %}

// Creating an instance of the AvatarView control.
SfAvatarView avatarView = new SfAvatarView();
           
{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control](avatarview_images/winui_avatarview.png)

## Initials 

Initials content type is used to show initials to the `AvatarView`. When using the `ContentType` as initials, you need to set the initial character using the following properties:

* `InitialsType` - Defines the type of characters to be displayed.  
* `AvatarName` - Defines the initials to be displayed.

### InitialsType

The `InitialsType` contains the following two types:

* SingleCharacter
* DoubleCharacter

You must set the `AvatarName` string property for displaying the initials value in the AvatarView.

**SingleCharacter**

The `SingleCharacter` is used for displaying the first character in the string you have set in the `AvatarName` property.

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

![WinUI AvatarView control with SingleCharacter](avatarview_images/winui_initials_avatarview.png)

**DoubleCharacter**

The `DoubleCharacter` is used for displaying a two-characters text you have set in the `AvatarName` property. If the initials consist of a single word, it will show the first and last letters of that word. If the initials contain two or more words, it will display the first letter of the first word and the first letter of the second word.

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

![WinUI AvatarView control with DoubleCharacter](avatarview_images/winui_doubleinitials_avatarview.png)

## Custom Image

You can add a custom image by setting the `ImageSource` property.

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

![WinUI AvatarView control with custom image.](avatarview_images/winui_imagesource_avatarview.png)

## Avatar Character

You can set the pre-defined images in avatar view by setting the `AvatarCharacter` property.

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

![WinUI AvatarView control with avatar character](avatarview_images/winui_avatarcharacter_avatarview.png)

## Group View 

You can add upto three images or initials in the same view using a GroupView type.

`InitialsMemberPath`: Displays the initials in the group view.
`ImageSourceMemberPath`: Displays the images in the group view.
`BackgroundColorMemberPath`: Sets the background color of the group view.
`InitialsColorMemberPath`: Sets the color for the initials in the group view.

{% tabs %}
{% highlight c# %}

public class Employee
{
   private string name;

   public string Name
   {
      get { return name; }
      set { name = value; }
   }

   private string imagesource;

   public string ImageSource
   {
      get { return imagesource; }
      set { imagesource = value; }
   }

   private Color colors;

   public Color Colors
   {
      get { return colors; }
      set { colors = value; }
   }

   private Color initialsColors;

   public Color InitialsColors
   {
      get { return initialsColors; }
      set { initialsColors = value; }
   }
}

public class EmployeeViewModel
{
   private ObservableCollection<Employee> collectionImage;

   public ObservableCollection<Employee> CollectionImage
   {
      get { return collectionImage; }
      set { collectionImage = value; }
   }

   public EmployeeViewModel()
   {
      CollectionImage = new ObservableCollection<Employee>();
      CollectionImage.Add(new Employee { ImageSource="mike.png" });
      CollectionImage.Add(new Employee {  Name="Alex", Colors=ColorHelper.FromArgb(0xFF, 0xD6, 0xE8, 0xD7), InitialsColors=ColorHelper.FromArgb(0xFF, 0x24, 0x4F, 0x23) });
      CollectionImage.Add(new Employee { ImageSource="ellanaa.png" });
   }    
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight xaml %}

<Page.DataContext>
    <local:EmployeeViewModel/>
</Page.DataContext>

<syncfusion:SfAvatarView ContentType="Group"   
                         GroupSource="{Binding CollectionImage}"
                         InitialsMemberPath="Name"
                         BackgroundColorMemberPath="Colors"
                         ImageSourceMemberPath="ImageSource"
                         InitialsColorMemberPath="InitialsColors"
                         AvatarSize="ExtraLarge">
</syncfusion:SfAvatarView>

{% endhighlight %}
{% highlight c# %}

public partial class MainWindow : Window
{
   EmployeeViewModel emp;
   public MainPage()
   {
      emp = new EmployeeViewModel();
      SfAvatarView avatarView = new SfAvatarView();
      avatarView.ContentType = AvatarContentType.Group;
      avatarView.GroupSource = emp.CollectionImage;
      avatarView.ImageSourceMemberPath = "ImageSource";
      avatarView.InitialsMemberPath = "Name";
      avatarView.BackgroundColorMemberPath = "Colors";
      avatarView.InitialsColorMemberPath = "InitialsColors";
      avatarView.AvatarSize = AvatarSize.ExtraLarge;
      page.DataContext = emp;
   }
}

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with GroupView for both Initials and Images](avatarview_images/winui_groupsource_avatarview.png)