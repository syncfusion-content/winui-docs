---
layout: post
title: ScreenTip | WinUI | Ribbon | Syncfusion
description: Learn more about the ScreenTip in the Syncfusion WinUI Ribbon (SfRibbon) control.
platform: winui
control: Ribbon
documentation: ug
---

# ScreenTip in WinUI Ribbon Control

`ScreenTip` is an enhanced ToolTip and it is used to show a popup window when the mouse cursor is hovered over `RibbonItem`. The popup is used to provide details of the `RibbonItem’s` function. The ScreenTip consist of two parts `Title` and `Content`. User can customize the ScreenTip title and content by `TitleTemplate` and `ContentTemplate` properties.

## Adding ScreenTip for ribbon items

ScreenTip can be set to each Ribbon item by using its `ScreenTip` property. The below code shows how to define the ScreenTip for ribbon items in Ribbon control.

{% tabs %}
{% highlight xaml %}

<ribbon:SfRibbon>
    <ribbon:SfRibbon.Tabs>
        <ribbon:RibbonTab Header="Home">
            <ribbon:RibbonGroup Header="Clipboard">
             <ribbon:RibbonSplitButton Content="Paste"
                            Command="{Binding ButtonCommand}" 
                            CommandParameter="Paste"
                    Icon="Paste"
                    AllowedSizeModes="Large">
    <ribbon:RibbonSplitButton.Flyout>
        ...
    </ribbon:RibbonSplitButton.Flyout>
    <ribbon:RibbonSplitButton.ScreenTip>
        <ribbon:ScreenTip Title="Paste" >
            <ribbon:ScreenTip.ContentTemplate>
                <DataTemplate>
                        <StackPanel>
                        <TextBlock Text="Add content on the clipboard to your document." 
                                   Width="180"
                                   TextWrapping="Wrap"/>
                        </StackPanel>
                </DataTemplate>
            </ribbon:ScreenTip.ContentTemplate>
        </ribbon:ScreenTip>
    </ribbon:RibbonSplitButton.ScreenTip>
</ribbon:RibbonSplitButton>
<ribbon:RibbonButton Content="Cut"
                     Icon="Cut" 
                     Command="{Binding ButtonCommand}" 
                     CommandParameter="Cut"
                     AllowedSizeModes="Normal, Small" >
    <ribbon:RibbonButton.ScreenTip>
        <ribbon:ScreenTip Title="Cut" >
            <ribbon:ScreenTip.ContentTemplate>
                <DataTemplate>
                    <StackPanel >
                        <TextBlock Text="Remove the selection and put it on the clipboard so you can paste it somewhere else." 
                                   Width="170"
                                   TextWrapping="Wrap"/>
                    </StackPanel>
                </DataTemplate>
            </ribbon:ScreenTip.ContentTemplate>
        </ribbon:ScreenTip>
    </ribbon:RibbonButton.ScreenTip>
</ribbon:RibbonButton>
<ribbon:RibbonButton Content="Copy"
                     DisplayOptions="Normal,Overflow"
                     Icon="Copy"
                     AllowedSizeModes="Normal, Small"
                     Command="{Binding ButtonCommand}" 
                     CommandParameter="Copy">
    <ribbon:RibbonButton.ScreenTip>
        <ribbon:ScreenTip Title="Copy" >
            <ribbon:ScreenTip.ContentTemplate>
                <DataTemplate>
                    <StackPanel Margin="2">
                        <TextBlock Text="Put a copy of the selection on the clipboard so you can paste it somewhere else." 
                                   Width="170"
                                   TextWrapping="Wrap"/>
                    </StackPanel>
                </DataTemplate>
            </ribbon:ScreenTip.ContentTemplate>
        </ribbon:ScreenTip>
    </ribbon:RibbonButton.ScreenTip>
</ribbon:RibbonButton>
<ribbon:RibbonButton Content="Format Painter"
             DisplayOptions="Normal,Simplified"
             AllowedSizeModes="Normal, Small" 
             Command="{Binding ButtonCommand}" 
             CommandParameter="Format Painter">
    <ribbon:RibbonButton.Icon>
        <FontIcon Glyph="&#xF0E3;" />
    </ribbon:RibbonButton.Icon>
    <ribbon:RibbonButton.ScreenTip>
        <ribbon:ScreenTip>
            <ribbon:ScreenTip.ContentTemplate>
                <DataTemplate>
                    <Grid>
                        <Grid.RowDefinitions>
                            <RowDefinition Height="Auto"/>
                            <RowDefinition/>
                            <RowDefinition Height="Auto"/>
                        </Grid.RowDefinitions>
                        <StackPanel>
                            <TextBlock Text="Like the look of a particular selection? You can apply that look to other content in the document." Width="250"
				       TextWrapping="WrapWholeWords"/>
                            <AppBarSeparator/>
                            <TextBlock Text="To get started:" TextWrapping="Wrap" Width="250"/>
                            <TextBlock Text="1. Select content with the formatting you like" TextWrapping="Wrap" Width="250"/>
                            <TextBlock Text="2. Click Format Painter" TextWrapping="Wrap" Width="250"/>
                            <TextBlock Text="3. Select something else to automatically apply the formatting" TextWrapping="Wrap" Width="250"/>
                            <AppBarSeparator/>
                            <TextBlock Text="FYI: To apply the formatting in multiple places, double-click Format Painter" 
				TextWrapping="WrapWholeWords" Width="250"/>
                        </StackPanel>
                        <Border Name="PART_Seperator" Margin="4"  BorderBrush="{StaticResource ControlStrokeColorDefault}" 
			        BorderThickness="0,0,0,1"  Grid.Row="1"  />
                        <Grid Grid.Row="2">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="20"/>
                                <ColumnDefinition  />
                            </Grid.ColumnDefinitions>
                            <Border  HorizontalAlignment="Left"   Grid.Column="0" Margin="4,4,0,4" x:Name="HelpImage">
                                <SymbolIcon Height="16" x:Name="helpImage" Width="16" Symbol="Help" 
					    Foreground="{StaticResource SystemAccentColor}"/>
                            </Border>
                            <HyperlinkButton Content="Tell me more" FontWeight="Bold" Foreground="{StaticResource SystemAccentColor}" 
					     NavigateUri="http://www.microsoft.com" Grid.Column="1" />
                        </Grid>
                    </Grid>
                </DataTemplate>
            </ribbon:ScreenTip.ContentTemplate>
            <ribbon:ScreenTip.TitleTemplate>
                <DataTemplate>
                    <Grid>
                        <Grid.ColumnDefinitions>
                            <ColumnDefinition Width="Auto"/>
                            <ColumnDefinition Width="Auto"/>
                        </Grid.ColumnDefinitions>
                        <TextBlock Text="Format Painter" Grid.Column="0"/>
                        <TextBlock Text="(Ctrl+w)" Grid.Column="1" />
                    </Grid>
                </DataTemplate>
            </ribbon:ScreenTip.TitleTemplate>
        </ribbon:ScreenTip>
    </ribbon:RibbonButton.ScreenTip>
</ribbon:RibbonButton>
</ribbon:RibbonGroup>
</ribbon:RibbonTab>
</ribbon:SfRibbon.Tabs>
</ribbon:SfRibbon>

{% endhighlight %}
{% endtabs %}

![ScreenTip in Ribbon control](Ribbon-ScreenTip-images/winui-ribbon-screentip.png)

![Customized ScreenTip in Ribbon control](Ribbon-ScreenTip-images/winui-ribbon-customized-screentip.png)
