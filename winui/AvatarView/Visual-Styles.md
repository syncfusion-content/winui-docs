---
layout: post
title: Visual Style in WinUI AvatarView control | Syncfusion
description: This section will explain about the different types of visual style that exists in WinUI SfAvatarView.
platform: WinUI
control: AvatarView
documentation: ug
---

# Visual Style in WinUI Avatar View(SfAvatarView)

## Visual styles in WinUI Avatar View(SfAvatarView)
The `SfAvatarView` control supports customization using the following built-in visual styles:

* Custom
* Circle
* Square

## Custom

Custom type allows you to customize the control, where you can handle the size, font size, corner radius, etc. of the control.

## Circle

You can directly set value to the circle in the `SfAvatarView` using the following styles:

* ExtraLargeCircle
* LargeCircle
* MediumCircle
* SmallCircle
* ExtraSmallCircle

The following code sample demonstrates how to define visual style of circle AvatarView.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <ResourceDictionary>
    <Style x:Key="AvatarViewStyle"  TargetType="syncfusion:SfAvatarView">
        <Setter Property="ContentType" Value="CustomImage"/>
        <Setter Property="ImageSource" Value="ellanaa.png"/>
    </Style>
    </ResourceDictionary>
</Page.Resources>

<Page.Content>
<StackPanel Orientation="Vertical" HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
    <Grid >
            <Grid.RowDefinitions>
                <RowDefinition Height="*"/>
                <RowDefinition Height="*"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
            </Grid.ColumnDefinitions>

            <syncfusion:SfAvatarView AvatarShape="Circle" AvatarSize="ExtraLarge" Grid.Row="0" Grid.Column="4" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="ExtraLargeCircle" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="4" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Circle" AvatarSize="Large" Grid.Row="0" Grid.Column="3" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="LargeCircle" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="3" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Circle" AvatarSize="Medium" Grid.Row="0" Grid.Column="2" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="MediumCircle" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="2" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Circle" AvatarSize="Small" Grid.Row="0" Grid.Column="1" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="SmallCircle" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="1" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Circle" AvatarSize="ExtraSmall" Grid.Row="0" Grid.Column="0" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="ExtraSmallCircle" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="0" FontSize="10"/>
    </Grid>
</StackPanel>
</Page.Content>

{% endhighlight %}

{% highlight c# %}

StackPanel stack = new StackPanel();
stack.Orientation = Orientation.Vertical;
stack.HorizontalAlignment = HorizontalAlignment.Stretch; 
stack.VerticalAlignment = VerticalAlignment.Stretch;

Grid mainGrid = new Grid();
mainGrid.RowDefinitions.Add(new RowDefinition { Height = new GridLength(1, GridUnitType.Star) });
mainGrid.RowDefinitions.Add(new RowDefinition { Height = new GridLength(1, GridUnitType.Star) });

mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });

TextBlock XLargeCircleTextBlock = new TextBlock();
XLargeCircleTextBlock.Text = "ExtraLargeCircle";
XLargeCircleTextBlock.FontSize = 12;
XLargeCircleTextBlock.FontWeight = FontWeights.Bold;
XLargeCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XLargeCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
XLargeCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XLargeCircleTextBlock.TextAlignment = TextAlignment.Center;
XLargeCircleTextBlock.FontSize = 10;

SfAvatarView avatarview1 = new SfAvatarView();
avatarview1.AvatarShape = AvatarShape.Circle;
avatarview1.AvatarSize = AvatarSize.ExtraLarge;
avatarview1.ContentType = AvatarContentType.Default;
avatarview1.ImageSource = new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock LargeCircleTextBlock = new TextBlock();
LargeCircleTextBlock.Text = "LargeCircle";
LargeCircleTextBlock.FontSize = 12;
LargeCircleTextBlock.FontWeight = FontWeights.Bold;
LargeCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
LargeCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
LargeCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
LargeCircleTextBlock.TextAlignment = TextAlignment.Center;
LargeCircleTextBlock.FontSize = 10;

SfAvatarView avatarview2 = new SfAvatarView();
avatarview2.AvatarShape = AvatarShape.Circle;
avatarview2.AvatarSize = AvatarSize.Large;
avatarview2.ContentType = AvatarContentType.Default;
avatarview2.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock MediumCircleTextBlock = new TextBlock();
MediumCircleTextBlock.Text = "MediumCircle";
MediumCircleTextBlock.FontSize = 12;
MediumCircleTextBlock.FontWeight = FontWeights.Bold;
MediumCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
MediumCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
MediumCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
MediumCircleTextBlock.TextAlignment = TextAlignment.Center;
MediumCircleTextBlock.FontSize = 10;

SfAvatarView avatarview3 = new SfAvatarView();
avatarview3.AvatarShape = AvatarShape.Circle;
avatarview3.AvatarSize = AvatarSize.Medium;
avatarview3.ContentType = AvatarContentType.Default;
avatarview3.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock SmallCircleTextBlock = new TextBlock();
SmallCircleTextBlock.Text = "SmallCircle";
SmallCircleTextBlock.FontSize = 12;
SmallCircleTextBlock.FontWeight = FontWeights.Bold;
SmallCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
SmallCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
SmallCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
SmallCircleTextBlock.TextAlignment = TextAlignment.Center;
SmallCircleTextBlock.FontSize = 10;

SfAvatarView avatarview4 = new SfAvatarView();
avatarview4.AvatarShape = AvatarShape.Circle;
avatarview4.AvatarSize = AvatarSize.Small;
avatarview4.ContentType = AvatarContentType.Default;
avatarview4.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock XSmallCircleTextBlock = new TextBlock();
XSmallCircleTextBlock.Text = "ExtraSmallCircle";
XSmallCircleTextBlock.FontSize = 12;
XSmallCircleTextBlock.FontWeight = FontWeights.Bold;
XSmallCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XSmallCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
XSmallCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XSmallCircleTextBlock.TextAlignment = TextAlignment.Center;
XSmallCircleTextBlock.FontSize = 10;

SfAvatarView avatarview5 = new SfAvatarView();
avatarview5.AvatarShape = AvatarShape.Circle;
avatarview5.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));
avatarview5.AvatarSize = AvatarSize.ExtraSmall;
avatarview5.ContentType = AvatarContentType.Default;

mainGrid.Children.Add(XLargeCircleTextBlock);
mainGrid.Children.Add(avatarview1);
mainGrid.Children.Add(LargeCircleTextBlock);
mainGrid.Children.Add(avatarview2);
mainGrid.Children.Add(MediumCircleTextBlock);
mainGrid.Children.Add(avatarview3);
mainGrid.Children.Add(SmallCircleTextBlock);
mainGrid.Children.Add(avatarview4);
mainGrid.Children.Add(XSmallCircleTextBlock);
mainGrid.Children.Add(avatarview5);

Grid.SetRow(avatarview5, 0);
Grid.SetRow(avatarview4, 0);
Grid.SetRow(avatarview3, 0);
Grid.SetRow(avatarview2, 0);
Grid.SetRow(avatarview1, 0);

Grid.SetColumn(avatarview5, 0);
Grid.SetColumn(avatarview4, 1);
Grid.SetColumn(avatarview3, 2);
Grid.SetColumn(avatarview2, 3);
Grid.SetColumn(avatarview1, 4);

Grid.SetRow(XSmallCircleTextBlock, 1);
Grid.SetRow(SmallCircleTextBlock, 1);
Grid.SetRow(MediumCircleTextBlock, 1);
Grid.SetRow(LargeCircleTextBlock, 1);
Grid.SetRow(XLargeCircleTextBlock, 1);

Grid.SetColumn(XSmallCircleTextBlock, 0);
Grid.SetColumn(SmallCircleTextBlock, 1);
Grid.SetColumn(MediumCircleTextBlock, 2);
Grid.SetColumn(LargeCircleTextBlock, 3);
Grid.SetColumn(XLargeCircleTextBlock, 4);
stack.Children.Add(mainGrid);
page.Content = stack;

{% endhighlight %}

{% endtabs %}

![SfAvatarView control with square visual style](AvatarView_images/winui_avatarview_circle_visualstyle.png)

## Square

You can directly set value to the square in the `SfAvatarView` using the following styles:

* ExtraLargeSquare
* LargeSquare
* MediumSquare
* SmallSquare
* ExtraSmallSquare

The following code sample demonstrates how to define visual style of square AvatarView.

{% tabs %}

{% highlight xaml %}

<Page.Resources>
    <ResourceDictionary>
    <Style x:Key="AvatarViewStyle"  TargetType="syncfusion:SfAvatarView">
        <Setter Property="ContentType" Value="CustomImage"/>
        <Setter Property="ImageSource" Value="ellanaa.png"/>
    </Style>
    </ResourceDictionary>
</Page.Resources>

<Page.Content>
<StackPanel Orientation="Vertical" HorizontalAlignment="Stretch" VerticalAlignment="Stretch">
    <Grid >
            <Grid.RowDefinitions>
                <RowDefinition Height="*"/>
                <RowDefinition Height="*"/>
            </Grid.RowDefinitions>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
                <ColumnDefinition Width="*"/>
            </Grid.ColumnDefinitions>

            <syncfusion:SfAvatarView AvatarShape="Square" AvatarSize="ExtraLarge" Grid.Row="0" Grid.Column="4" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="ExtraLargeSquare" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="4" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Square" AvatarSize="Large" Grid.Row="0" Grid.Column="3" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="LargeSquare" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="3" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Square" AvatarSize="Medium" Grid.Row="0" Grid.Column="2" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="MediumSquare" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="2" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Square" AvatarSize="Small" Grid.Row="0" Grid.Column="1" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="SmallSquare" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="1" FontSize="10"/>
            <syncfusion:SfAvatarView AvatarShape="Square" AvatarSize="ExtraSmall" Grid.Row="0" Grid.Column="0" Style="{StaticResource AvatarViewStyle}"/>
            <TextBlock Text="ExtraSmallSquare" FontWeight="Bold" Grid.Row="1" HorizontalAlignment="Center" VerticalAlignment="Center" HorizontalTextAlignment="Center" TextAlignment="Center" Grid.Column="0" FontSize="10"/>
    </Grid>
</StackPanel>
</Page.Content>

{% endhighlight %}

{% highlight c# %}

StackPanel stack = new StackPanel();
stack.Orientation = Orientation.Vertical;
stack.HorizontalAlignment = HorizontalAlignment.Stretch; 
stack.VerticalAlignment = VerticalAlignment.Stretch;

Grid mainGrid = new Grid();
mainGrid.RowDefinitions.Add(new RowDefinition { Height = new GridLength(1, GridUnitType.Star) });
mainGrid.RowDefinitions.Add(new RowDefinition { Height = new GridLength(1, GridUnitType.Star) });

mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });
mainGrid.ColumnDefinitions.Add(new ColumnDefinition { Width = new GridLength(1, GridUnitType.Star) });

TextBlock XLargeSquareTextBlock = new TextBlock();
XLargeSquareTextBlock.Text = "ExtraLargeSquare";
XLargeSquareTextBlock.FontSize = 12;
XLargeSquareTextBlock.FontWeight = FontWeights.Bold;
XLargeSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XLargeSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
XLargeSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XLargeSquareTextBlock.TextAlignment = TextAlignment.Center;
XLargeSquareTextBlock.FontSize = 10;

SfAvatarView avatarview1 = new SfAvatarView();
avatarview1.AvatarShape = AvatarShape.Square;
avatarview1.AvatarSize = AvatarSize.ExtraLarge;
avatarview1.ContentType = AvatarContentType.Default;
avatarview1.ImageSource = new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock LargeSquareTextBlock = new TextBlock();
LargeSquareTextBlock.Text = "LargeSquare";
LargeSquareTextBlock.FontSize = 12;
LargeSquareTextBlock.FontWeight = FontWeights.Bold;
LargeSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
LargeSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
LargeSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
LargeSquareTextBlock.TextAlignment = TextAlignment.Center;
LargeSquareTextBlock.FontSize = 10;

SfAvatarView avatarview2 = new SfAvatarView();
avatarview2.AvatarShape = AvatarShape.Square;
avatarview2.AvatarSize = AvatarSize.Large;
avatarview2.ContentType = AvatarContentType.Default;
avatarview2.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock MediumSquareTextBlock = new TextBlock();
MediumSquareTextBlock.Text = "MediumSquare";
MediumSquareTextBlock.FontSize = 12;
MediumSquareTextBlock.FontWeight = FontWeights.Bold;
MediumSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
MediumSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
MediumSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
MediumSquareTextBlock.TextAlignment = TextAlignment.Center;
MediumSquareTextBlock.FontSize = 10;

SfAvatarView avatarview3 = new SfAvatarView();
avatarview3.AvatarShape = AvatarShape.Square;
avatarview3.AvatarSize = AvatarSize.Medium;
avatarview3.ContentType = AvatarContentType.Default;
avatarview3.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock SmallSquareTextBlock = new TextBlock();
SmallSquareTextBlock.Text = "SmallSquare";
SmallSquareTextBlock.FontSize = 12;
SmallSquareTextBlock.FontWeight = FontWeights.Bold;
SmallSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
SmallSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
SmallSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
SmallSquareTextBlock.TextAlignment = TextAlignment.Center;
SmallSquareTextBlock.FontSize = 10;

SfAvatarView avatarview4 = new SfAvatarView();
avatarview4.AvatarShape = AvatarShape.Square;
avatarview4.AvatarSize = AvatarSize.Small;
avatarview4.ContentType = AvatarContentType.Default;
avatarview4.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));

TextBlock XSmallSquareTextBlock = new TextBlock();
XSmallSquareTextBlock.Text = "ExtraSmallSquare";
XSmallSquareTextBlock.FontSize = 12;
XSmallSquareTextBlock.FontWeight = FontWeights.Bold;
XSmallSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XSmallSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
XSmallSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XSmallSquareTextBlock.TextAlignment = TextAlignment.Center;
XSmallSquareTextBlock.FontSize = 10;

SfAvatarView avatarview5 = new SfAvatarView();
avatarview5.AvatarShape = AvatarShape.Square;
avatarview5.ImageSource =  new BitmapImage(new Uri("ms-appx:///ellanaa.png"));
avatarview5.AvatarSize = AvatarSize.ExtraSmall;
avatarview5.ContentType = AvatarContentType.Default;

mainGrid.Children.Add(XLargeSquareTextBlock);
mainGrid.Children.Add(avatarview1);
mainGrid.Children.Add(LargeSquareTextBlock);
mainGrid.Children.Add(avatarview2);
mainGrid.Children.Add(MediumSquareTextBlock);
mainGrid.Children.Add(avatarview3);
mainGrid.Children.Add(SmallSquareTextBlock);
mainGrid.Children.Add(avatarview4);
mainGrid.Children.Add(XSmallSquareTextBlock);
mainGrid.Children.Add(avatarview5);

Grid.SetRow(avatarview5, 0);
Grid.SetRow(avatarview4, 0);
Grid.SetRow(avatarview3, 0);
Grid.SetRow(avatarview2, 0);
Grid.SetRow(avatarview1, 0);

Grid.SetColumn(avatarview5, 0);
Grid.SetColumn(avatarview4, 1);
Grid.SetColumn(avatarview3, 2);
Grid.SetColumn(avatarview2, 3);
Grid.SetColumn(avatarview1, 4);

Grid.SetRow(XSmallSquareTextBlock, 1);
Grid.SetRow(SmallSquareTextBlock, 1);
Grid.SetRow(MediumSquareTextBlock, 1);
Grid.SetRow(LargeSquareTextBlock, 1);
Grid.SetRow(XLargeSquareTextBlock, 1);

Grid.SetColumn(XSmallSquareTextBlock, 0);
Grid.SetColumn(SmallSquareTextBlock, 1);
Grid.SetColumn(MediumSquareTextBlock, 2);
Grid.SetColumn(LargeSquareTextBlock, 3);
Grid.SetColumn(XLargeSquareTextBlock, 4);
stack.Children.Add(mainGrid);
page.Content = stack;

{% endhighlight %}
{% endtabs %}

![SfAvatarView control with square visual style](AvatarView_images/winui_avatarview_square_visualstyle.png)