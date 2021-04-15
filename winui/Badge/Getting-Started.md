---
layout: post
title: Getting started with WinUI Badge control | Syncfusion
description: This section describes about how to add the Badge control into WinUI application and its basic features.
platform: WinUI
control: SfBadge
documentation: ug
---

# Getting started with WinUI Badge (SfBadge)

This section explains the steps required to add the [WinUI Badge](https://www.syncfusion.com/winui-controls/badge) control and its elements such as shapes, alignment and predefined colors. This section covers only basic features needed to get started with Syncfusion `Badge` control.

## Structure of Badge control

![Structure of WinUI Badge control](Getting-Started_images/Structure.png)

## Creating an application with WinUI Badge

1. Create a [WinUI 3 desktop app for C# and .NET 5](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-desktop) or [WinUI 3 app in UWP for C#](https://docs.microsoft.com/en-us/windows/apps/winui/winui3/get-started-winui3-for-uwp).
2. Add reference to [Syncfusion.Notifications.WinUI](https://www.nuget.org/packages/Syncfusion.Notifications.WinUI) NuGet. 
3. Import the control namespace `Syncfusion.UI.Xaml.Notifications` in XAML or C# code.
4. Initialize the `SfBadge` control.

{% tabs %}
{% highlight xaml %}

<Page
    x:Class="GettingStarted.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:GettingStarted"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    xmlns:notification="using:Syncfusion.UI.Xaml.Notifications"
    mc:Ignorable="d"
    Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
    <Grid>
        <notification:SfBadge Name="badge"
                              Height="30"
                              Width="30"/>
    </Grid>
</Page>

{% endhighlight %}
{% highlight C# %}

using Syncfusion.UI.Xaml.Notifications;

namespace GettingStarted
{
    /// <summary>
    /// An empty page that can be used on its own or navigated to within a Frame.
    /// </summary>
    public sealed partial class MainPage : Page
    {
        public MainPage()
        {
            this.InitializeComponent();
            // Creating an instance of the Badge control
            SfBadge badge = new SfBadge();

            // Setting height and width to Badge control
            badge.Height = 30;
            badge.Width = 30;
            grid.Children.Add(badge);
        }
    }
}

{% endhighlight %}
{% endtabs %}

## Adding badge for a Button

If you want to assign `Badge` for any objects, create the `Badge` and assign the badge to the `BadgeContainer.Badge` property. Before that you need to create a `BadgeContainer` and add that object to the `BadgeContainer.Content` property.

Here, `Badge` control added for the `Button` control.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge Name="badge" 
                              Content="10"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

//Creating Badge control
SfBadge badge = new SfBadge();
badge.Content = "10";

BadgeContainer badgeContainer = new BadgeContainer();
badgeContainer.Content = new Button(){ Content="Inbox" };

//Assigning Badge control to the content of BadgeContainer
badgeContainer.Badge = badge;

{% endhighlight %}
{% endtabs %}

![Badge added to the Button control](Getting-Started_images/Adding_Badge.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Getting_Started)

## Setting Badge display content

If you want to set or change the display content of the `Badge`, use the `Content` property. The default value of `Content` property is `null`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge Name="badge" 
                              Content="99+"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

SfBadge badge = new SfBadge();
//Setting Badge display content
badge.Content = "99+";

BadgeContainer badgeContainer = new BadgeContainer();
badgeContainer.Content = new Button(){ Content="Inbox" };

//Assigning Badge control to the content of BadgeContainer
badgeContainer.Badge = badge;

{% endhighlight %}
{% endtabs %}

![Badge display content changed](Getting-Started_images/Change_BadgeContent.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Content_CustomUI)

## Alignment of Badge

you can align the `Badge` either horizontally or vertically by using the `Badge.HorizontalAlignment` or `VerticalAlignment` properties. The default value of `HorizontalAlignment` property is `Right` and `VerticalAlignment` property is `Top`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge HorizontalAlignment="Left"
                              VerticalAlignment="Center"
                              Content="99+"
                              Name="badge"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalAlignment = HorizontalAlignment.Left;
badge.VerticalAlignment = VerticalAlignment.Center;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Alignment of the Badge control is changed](Getting-Started_images/Alignment.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

## Positioning of Badge

You can change the horizontal or vertical position of the `Badge` either inside, outside or in the middle by using the [HorizontalAnchor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_HorizontalAnchor) and [VerticalAnchor](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_VerticalAnchor) properties. The default value of `HorizontalAnchor` and `VerticalAnchor` properties is `Center`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge HorizontalAnchor="Outside"
                              VerticalAnchor="Center"
                              Content="99+"
                              Name="badge"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalAnchor = BadgeAnchor.Outside;
badge.VerticalAnchor = BadgeAnchor.Center;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Position of the Badge control is changed](Getting-Started_images/Anchor.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

## Place the Badge any where on the container

If you want to place the `Badge` anywhere on the container, use the [HorizontalPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_HorizontalPosition) or [VerticalPosition](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_VerticalPosition) properties. The value range for `HorizontalPosition` and `VerticalPosition` properties is `0` to `1`. The default value of `HorizontalPosition` property is `1` and `VerticalPosition` property is `0`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer>
    <notification:BadgeContainer.Content> 
        <PersonPicture Width="100"
                       Height="100"
                       ProfilePicture="/Images/avatar.png"/>    
    </notification:BadgeContainer.Content>
    <notification:BadgeContainer.Badge>
        <notification:SfBadge x:Name="badge3"
                              Shape="None"
                              HorizontalPosition="0.9"
                              VerticalPosition="0.8">
            <Ellipse Width="20" Height="20" Fill="LimeGreen"/>
        </notification:SfBadge>
    </notification:BadgeContainer.Badge>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.HorizontalPosition = 0.9;
badge.VerticalPosition = 0.8;

{% endhighlight %}
{% endtabs %}

![Displaying the customized alignment of the Badge control](Getting-Started_images/Custom_Alignment.png)

## Adding badge without BadgeContainer

You can directly add the `Badge` to any objects without using the `BadgeContainer`.

N> By default, `Badge` will automatically aligned and positioned inside the container based on its content. If you use `Badge` control without `BadgeContainer`, alignment and positioning options are not applicable.

{% tabs %}
{% highlight C# %}

public class ListItem {
    public string ItemName { get; set; }
    public int? UnreadMessageCount { get; set; }
}

public class ViewModel {
    public List<ListItem> MailItems { get; set; }

    public ViewModel() {
        MailItems = new List<ListItem>();
        MailItems.Add(new ListItem() { ItemName = "Inbox", 
            UnreadMessageCount = 20 });
        MailItems.Add(new ListItem() { ItemName = "Drafts", 
            UnreadMessageCount = null });
        MailItems.Add(new ListItem() { ItemName = "Sent Items", 
            UnreadMessageCount = 5 });
        MailItems.Add(new ListItem() { ItemName = "Deleted Items",
            UnreadMessageCount = null });
        MailItems.Add(new ListItem() { ItemName = "Junk Email",
            UnreadMessageCount = null });
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Page.DataContext>
    <local:ViewModel/>
</Page.DataContext>
<Grid>
    <ListView BorderThickness="1"
              BorderBrush="LightGray"
              ItemsSource="{Binding MailItems}" 
              SelectedIndex="0"
              VerticalAlignment="Center" 
              HorizontalAlignment="Center">
        <ListView.ItemTemplate>
            <DataTemplate>
                <Grid>
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="150"/>
                        <ColumnDefinition Width="100"/>
                    </Grid.ColumnDefinitions>
                    <ContentPresenter 
                                       Grid.Column="0" 
                                       Content="{Binding ItemName}" 
                                       VerticalAlignment="Center"/>
                    <notification:SfBadge 
                                       x:Name="badge4"
                                       Grid.Column="1" 
                                       Height="20" 
                                       Width="40" 
                                       Content="{Binding UnreadMessageCount}"
                                       Shape="Oval"
                                       Fill="Warning">
                    </notification:SfBadge>
                </Grid>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</Grid>

{% endhighlight %}
{% endtabs %}

![Badge added for ListView Items](Getting-Started_images/badge_withoutBadgeContainer.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_without_BadgeContainer)

## Predefined colors for displaying the badges

You can change background color of the `Badge` by using the [Fill](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_Fill) property. Based on the value of `Fill` property, respective background color will be applied to the `Badge`. The default value of `Fill` property is `Accent`.

The `Badge` supports the following different essential states :

* Accent - RoyalBlue background will be applied

* Alt - DarkSlateGray background will be applied

* Default - Lavender background will be applied

* Error - OrangeRed background will be applied

* Information - LightSeaGreen background will be applied

* Success - Green background will be applied

* Warning - Orange background will be applied

![Displaying the various state colors for Badge](Getting-Started_images/States.png)

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge Fill="Success"
                              Content="99+"
                              Name="badge"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.Fill = BadgeFill.Success;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Displaying the Success state of Badge](Getting-Started_images/Information_States.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

N> If you want to apply your own customized colors for the background of `Badge`, refer the [Custom colors for displaying the badges](https://help.syncfusion.com/winui/badge/badge-customization#custom-colors-for-displaying-the-badge) page.

## Predefined shapes for displaying the Badge

You can change the default shape to either `Rectangle`, `Oval` or `Ellipse` by using [Shape](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_Shape) property. If you want to display the `Badge` content without any default shapes , use the `Shape` property value as `None`. The default value of `Shape` property is `Oval`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge Shape="Ellipse"
                              Content="99+"
                              Name="badge"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.Shape = BadgeShape.Ellipse;
badge.Content = "99+";

{% endhighlight %}
{% endtabs %}

![Displaying the different default Badge shapes](Getting-Started_images/Default_Shape.png)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

N> If you want to apply your own customized shapes for the `Badge`, refer the [Custom shape for displaying the Badge](https://help.syncfusion.com/winui/badge/badge-customization#custom-shape-for-displaying-the-badge) page.

## Animate when content changes

You can enable the `Scale` or `Opacity` based animation for displaying the `Badge` text by using [AnimationType](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Notifications.SfBadge.html#Syncfusion_UI_Xaml_Notifications_SfBadge_AnimationType) property. You can only see the animation when you change the text of the `Badge`. The default value of `AnimationType` property is `None`.

{% tabs %}
{% highlight XAML %}

<notification:BadgeContainer Name="badgeContainer"  >
    <notification:BadgeContainer.Badge>
        <notification:SfBadge AnimationType="Scale"
                              Background="Red"
                              Content="1"
                              Name="badge"/>
    </notification:BadgeContainer.Badge>
    <notification:BadgeContainer.Content>
        <Button Content="Inbox">
        </Button>
    </notification:BadgeContainer.Content>
</notification:BadgeContainer>

{% endhighlight %}
{% highlight C# %}

badge.AnimationType = BadgeAnimationType.Scale;
badge.Content = "1";

{% endhighlight %}
{% endtabs %}

### Scaling based animation

![Displaying the Badge with scale based animation](Getting-Started_images/Scale_animation.gif)

### Opacity based animation

![Displaying the Badge with opacity based animation](Getting-Started_images/Opacity_animation.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Badge_Features)

## Custom Content Formats

You can format the content which is displayed in the `Badge` content by using the converters. For example, you can display the number as `99+` which is greater than or equal to `100`.

{% tabs %}
{% highlight C# %}

public class CustomNumberConverter : IValueConverter {
    public object Convert(object value, Type targetType, object parameter, string language)
    {
        if (int.TryParse(value.ToString(), out int number)) {
            if (number <= 99) {
                return value;
            }
            else if (number <= 999) {
                return "99+";
            }
            else if (number < 99999) {
                return (number / 1000).ToString("0.#") + "K";
            }
            else if (number < 999999) {
                return (number / 1000).ToString("#,0K");
            }
            else if (number < 9999999) {
                return (number / 1000000).ToString("0.#") + "M";
            }
            else {
                return (number / 1000000).ToString("#,0M");
            }
        }
        return value;
    }

    public object ConvertBack(object value, Type targetType, object parameter, string language) {
        throw new NotImplementedException();
    }
}

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight XAML %}

<Page.Resources>
    <local:CustomNumberConverter x:Key="customNumberConverter"/>
</Page.Resources>

<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition/>
        <ColumnDefinition/>
    </Grid.ColumnDefinitions>
    
    <notification:BadgeContainer Name="badgeContainer">
        <notification:BadgeContainer.Badge>
            <notification:SfBadge  Name="badge"
                                 Background="Red"
                                 Content="{x:Bind badgeContent.Text, 
                                                  Mode=OneWay, 
                                                  Converter={StaticResource 
                                                  customNumberConverter}}"/>
        </notification:BadgeContainer.Badge>
        <notification:BadgeContainer.Content>
            <Button Content="Inbox">
            </Button>
        </notification:BadgeContainer.Content>
    </notification:BadgeContainer>

    <Grid Grid.Column="1">
        <muxc:NumberBox x:Name="badgeContent"
                        Header="BadgeContent"
                        Value="99"
                        SpinButtonPlacementMode="Compact"
                        Minimum="0"
                        Maximum="100000000"/>
    </Grid>
</Grid>

{% endhighlight %}
{% endtabs %}

![Number formatting for the Badge content](Getting-Started_images/number.gif)

N> Download demo application from [GitHub](https://github.com/SyncfusionExamples/syncfusion-winui-badge-control-examples/blob/master/Samples/Content_CustomUI)
