---
layout: post
title: Visual Styles in WinUI AvatarView control | Syncfusion
description: This section will explain about the different types of visual styles that exists in WinUI AvatarView.
platform: WinUI
control: AvatarView
documentation: ug
---

# Visual Styles in WinUI AvatarView

The `AvatarView` control supports visual style customization using the following built-in visual styles:

* Custom
* Circle
* Square

## Custom

Custom type allows you to customize the control, where you can handle the size, font size, corner radius, etc. of the control. Refer to the Customization Documentation in SfAvatarView.

## Circle

You can directly set value to the circle in the `AvatarView` using the following styles:

* ExtraLarge
* Large
* Medium
* Small
* ExtraSmall

The following code sample demonstrates how to define visual style of circle AvatarView.

{% tabs %}
{% highlight xaml %}

<Page.Resources>
    <ResourceDictionary>
    <Style x:Key="AvatarViewStyle"  TargetType="syncfusion:SfAvatarView">
        <Setter Property="ContentType" Value="CustomImage"/>
        <Setter Property="ImageSource" Value="person.png"/>
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

SfAvatarView avatarView1 = new SfAvatarView();
avatarView1.AvatarShape = AvatarShape.Circle;
avatarView1.AvatarSize = AvatarSize.ExtraLarge;
avatarView1.ContentType = AvatarContentType.Default;
avatarView1.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock LargeCircleTextBlock = new TextBlock();
LargeCircleTextBlock.Text = "LargeCircle";
LargeCircleTextBlock.FontSize = 12;
LargeCircleTextBlock.FontWeight = FontWeights.Bold;
LargeCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
LargeCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
LargeCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
LargeCircleTextBlock.TextAlignment = TextAlignment.Center;
LargeCircleTextBlock.FontSize = 10;

SfAvatarView avatarView2 = new SfAvatarView();
avatarView2.AvatarShape = AvatarShape.Circle;
avatarView2.AvatarSize = AvatarSize.Large;
avatarView2.ContentType = AvatarContentType.Default;
avatarView2.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock MediumCircleTextBlock = new TextBlock();
MediumCircleTextBlock.Text = "MediumCircle";
MediumCircleTextBlock.FontSize = 12;
MediumCircleTextBlock.FontWeight = FontWeights.Bold;
MediumCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
MediumCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
MediumCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
MediumCircleTextBlock.TextAlignment = TextAlignment.Center;
MediumCircleTextBlock.FontSize = 10;

SfAvatarView avatarView3 = new SfAvatarView();
avatarView3.AvatarShape = AvatarShape.Circle;
avatarView3.AvatarSize = AvatarSize.Medium;
avatarView3.ContentType = AvatarContentType.Default;
avatarView3.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock SmallCircleTextBlock = new TextBlock();
SmallCircleTextBlock.Text = "SmallCircle";
SmallCircleTextBlock.FontSize = 12;
SmallCircleTextBlock.FontWeight = FontWeights.Bold;
SmallCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
SmallCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
SmallCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
SmallCircleTextBlock.TextAlignment = TextAlignment.Center;
SmallCircleTextBlock.FontSize = 10;

SfAvatarView avatarView4 = new SfAvatarView();
avatarView4.AvatarShape = AvatarShape.Circle;
avatarView4.AvatarSize = AvatarSize.Small;
avatarView4.ContentType = AvatarContentType.Default;
avatarView4.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock XSmallCircleTextBlock = new TextBlock();
XSmallCircleTextBlock.Text = "ExtraSmallCircle";
XSmallCircleTextBlock.FontSize = 12;
XSmallCircleTextBlock.FontWeight = FontWeights.Bold;
XSmallCircleTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XSmallCircleTextBlock.VerticalAlignment = VerticalAlignment.Center;
XSmallCircleTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XSmallCircleTextBlock.TextAlignment = TextAlignment.Center;
XSmallCircleTextBlock.FontSize = 10;

SfAvatarView avatarView5 = new SfAvatarView();
avatarView5.AvatarShape = AvatarShape.Circle;
avatarView5.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));
avatarView5.AvatarSize = AvatarSize.ExtraSmall;
avatarView5.ContentType = AvatarContentType.Default;

mainGrid.Children.Add(XLargeCircleTextBlock);
mainGrid.Children.Add(avatarView1);
mainGrid.Children.Add(LargeCircleTextBlock);
mainGrid.Children.Add(avatarView2);
mainGrid.Children.Add(MediumCircleTextBlock);
mainGrid.Children.Add(avatarView3);
mainGrid.Children.Add(SmallCircleTextBlock);
mainGrid.Children.Add(avatarView4);
mainGrid.Children.Add(XSmallCircleTextBlock);
mainGrid.Children.Add(avatarView5);

Grid.SetRow(avatarView5, 0);
Grid.SetRow(avatarView4, 0);
Grid.SetRow(avatarView3, 0);
Grid.SetRow(avatarView2, 0);
Grid.SetRow(avatarView1, 0);

Grid.SetColumn(avatarView5, 0);
Grid.SetColumn(avatarView4, 1);
Grid.SetColumn(avatarView3, 2);
Grid.SetColumn(avatarView2, 3);
Grid.SetColumn(avatarView1, 4);

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

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with circle visual style](avatarview_images/winui_circle_visualstyle_avatarview.png)

## Square

You can directly set value to the square in the `SfAvatarView` using the following styles:

* ExtraLarge
* Large
* Medium
* Small
* ExtraSmall

The following code sample demonstrates how to define visual style of square AvatarView.

{% tabs %}
{% highlight xaml %}

<Page.Resources>
    <ResourceDictionary>
    <Style x:Key="AvatarViewStyle"  TargetType="syncfusion:SfAvatarView">
        <Setter Property="ContentType" Value="CustomImage"/>
        <Setter Property="ImageSource" Value="person.png"/>
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

SfAvatarView avatarView1 = new SfAvatarView();
avatarView1.AvatarShape = AvatarShape.Square;
avatarView1.AvatarSize = AvatarSize.ExtraLarge;
avatarView1.ContentType = AvatarContentType.Default;
avatarView1.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock LargeSquareTextBlock = new TextBlock();
LargeSquareTextBlock.Text = "LargeSquare";
LargeSquareTextBlock.FontSize = 12;
LargeSquareTextBlock.FontWeight = FontWeights.Bold;
LargeSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
LargeSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
LargeSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
LargeSquareTextBlock.TextAlignment = TextAlignment.Center;
LargeSquareTextBlock.FontSize = 10;

SfAvatarView avatarView2 = new SfAvatarView();
avatarView2.AvatarShape = AvatarShape.Square;
avatarView2.AvatarSize = AvatarSize.Large;
avatarView2.ContentType = AvatarContentType.Default;
avatarView2.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock MediumSquareTextBlock = new TextBlock();
MediumSquareTextBlock.Text = "MediumSquare";
MediumSquareTextBlock.FontSize = 12;
MediumSquareTextBlock.FontWeight = FontWeights.Bold;
MediumSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
MediumSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
MediumSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
MediumSquareTextBlock.TextAlignment = TextAlignment.Center;
MediumSquareTextBlock.FontSize = 10;

SfAvatarView avatarView3 = new SfAvatarView();
avatarView3.AvatarShape = AvatarShape.Square;
avatarView3.AvatarSize = AvatarSize.Medium;
avatarView3.ContentType = AvatarContentType.Default;
avatarView3.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock SmallSquareTextBlock = new TextBlock();
SmallSquareTextBlock.Text = "SmallSquare";
SmallSquareTextBlock.FontSize = 12;
SmallSquareTextBlock.FontWeight = FontWeights.Bold;
SmallSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
SmallSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
SmallSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
SmallSquareTextBlock.TextAlignment = TextAlignment.Center;
SmallSquareTextBlock.FontSize = 10;

SfAvatarView avatarView4 = new SfAvatarView();
avatarView4.AvatarShape = AvatarShape.Square;
avatarView4.AvatarSize = AvatarSize.Small;
avatarView4.ContentType = AvatarContentType.Default;
avatarView4.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));

TextBlock XSmallSquareTextBlock = new TextBlock();
XSmallSquareTextBlock.Text = "ExtraSmallSquare";
XSmallSquareTextBlock.FontSize = 12;
XSmallSquareTextBlock.FontWeight = FontWeights.Bold;
XSmallSquareTextBlock.HorizontalAlignment = HorizontalAlignment.Center;
XSmallSquareTextBlock.VerticalAlignment = VerticalAlignment.Center;
XSmallSquareTextBlock.HorizontalTextAlignment = TextAlignment.Center;
XSmallSquareTextBlock.TextAlignment = TextAlignment.Center;
XSmallSquareTextBlock.FontSize = 10;

SfAvatarView avatarView5 = new SfAvatarView();
avatarView5.AvatarShape = AvatarShape.Square;
avatarView5.ImageSource = new BitmapImage(new Uri("ms-appx:///person.png"));
avatarView5.AvatarSize = AvatarSize.ExtraSmall;
avatarView5.ContentType = AvatarContentType.Default;

mainGrid.Children.Add(XLargeSquareTextBlock);
mainGrid.Children.Add(avatarView1);
mainGrid.Children.Add(LargeSquareTextBlock);
mainGrid.Children.Add(avatarView2);
mainGrid.Children.Add(MediumSquareTextBlock);
mainGrid.Children.Add(avatarView3);
mainGrid.Children.Add(SmallSquareTextBlock);
mainGrid.Children.Add(avatarView4);
mainGrid.Children.Add(XSmallSquareTextBlock);
mainGrid.Children.Add(avatarView5);

Grid.SetRow(avatarView5, 0);
Grid.SetRow(avatarView4, 0);
Grid.SetRow(avatarView3, 0);
Grid.SetRow(avatarView2, 0);
Grid.SetRow(avatarView1, 0);

Grid.SetColumn(avatarView5, 0);
Grid.SetColumn(avatarView4, 1);
Grid.SetColumn(avatarView3, 2);
Grid.SetColumn(avatarView2, 3);
Grid.SetColumn(avatarView1, 4);

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

{% endhighlight %}
{% endtabs %}

![WinUI AvatarView control with square visual style](avatarview_images/winui_square_visualstyle_avatarview.png)