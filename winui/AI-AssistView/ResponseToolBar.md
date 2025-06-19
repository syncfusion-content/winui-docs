---
layout: post
title: ResponseToolBar in WinUI AI AssistView control | Syncfusion
description: Learn about ResponseToolBar with the Syncfusion WinUI AI AssistView (SfAIAssistView) control with its basic features.
platform: WinUI
control: AI AssistView
documentation: ug
---

# ResponseToolBar in WinUI AI AssistView 

#### ResponseToolBar

The [SfAIAssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) control includes a **Response Toolbar** feature which allows users to customize the response toolbar in chat. By default, the toolbar contains built-in options such as copy, regenerate, like, and dislike. Users can also add custom items, as needed.

#### ResponseToolBarItem

The **ResponseToolbarItem** in [SfAIAssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) can be customized using the ItemTemplate property to define a custom appearance and behavior. This allows you to display icons, buttons, text, or even controls like Path, Image, or TextBlock.

### ItemType

The **ItemType** property in ResponseToolbarItem defines the type of built-in action or interaction displayed on the response toolbar. It helps identify the behavior and icon associated with that toolbar item.

The **ItemType** property includes five types:

**Copy** - Displays a "Copy" icon to allow copying the response content to clipboard.
**Like** - Displays a thumbs-up icon. Used to indicate a positive response or feedback.
**DisLike** - Displays a thumbs-down icon. Used to indicate a negative response or feedback.
**Regenerate** - Used to regenerate a response (if AI is integrated for retry or rephrasing).
**Custom** - Allows you to define a completely customized button with a custom template and behavior.

{% tabs %}

{% highlight xaml %}

 <Grid x:Name="grid1">
    <syncfusion:SfAIAssistView x:Name="aiAssistView" CurrentUser="{Binding CurrentUser}"  
                               Messages="{Binding Chats}" >
        <syncfusion:SfAIAssistView.ResponseToolbarItems>
            <syncfusion:ResponseToolbarItem ItemType="Copy"  Tooltip="Copy"></syncfusion:ResponseToolbarItem>
            <syncfusion:ResponseToolbarItem ItemType="Regenerate" Tooltip="Regenerate"></syncfusion:ResponseToolbarItem>
            <syncfusion:ResponseToolbarItem ItemType="Like" Tooltip="Like" ></syncfusion:ResponseToolbarItem>
            <syncfusion:ResponseToolbarItem ItemType="Dislike" Tooltip="Dislike"></syncfusion:ResponseToolbarItem>
        </syncfusion:SfAIAssistView.ResponseToolbarItems>
    </syncfusion:SfAIAssistView>
</Grid>

{% endhighlight %} 

{% endtabs %}

![ResponseToolBar feature in WinUI SfAIAssistView control](aiassistview_images/winui_aiassistview_responsetoolbar.png)


#### IsResponseToolbarVisible

The **IsResponseToolbarVisible** property of the [SfAIAssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) control determines whether the response toolbar is displayed below each chat message. When set to false, the response toolbar is hidden. By default, this property is set to true.

{% tabs %}

{% highlight xaml %}

<Grid x:Name="grid1">
    <syncfusion:SfAIAssistView CurrentUser="{Binding CurrentUser}"  
                               Messages="{Binding Chats}" IsResponseToolbarVisible="False">
    </syncfusion:SfAIAssistView>
</Grid>

{% endhighlight %} 

{% highlight C# %}

SfAIAssistView aiAssistView = new SfAIAssistView();
aiAssistView.IsResponseToolbarVisible = false;

{% endhighlight %}
{% endtabs %}

![IsResponseToolbarVisible in WinUI SfAIAssistView control](aiassistview_images/winui_aiassistview_isresponsetoolbarvisible.png)

#### ResponseToolbarItemClicked 

The **ResponseToolbarItemClicked** event is triggered whenever a toolbar item (like a button) in the ResponseToolbarItems collection is clicked by the user.

This allows you to centrally handle custom actions for buttons like "Copy", "Like", "Delete", or any other custom tools you define in ResponseToolbarItems.

{% tabs %}

{% highlight xaml %}

<Grid x:Name="grid1">
    <syncfusion:SfAIAssistView x:Name="sfAIAssistView"
                           ResponseToolbarItemClicked="AiAssistView_ResponseToolbarItemClicked"/>
</Grid>

{% endhighlight %} 

{% highlight C# %}

SfAIAssistView sfAIAssistView = new SfAIAssistView();
sfAIAssistView.ResponseToolbarItemClicked += AiAssistView_ResponseToolbarItemClicked;

private void AiAssistView_ResponseToolbarItemClicked(object sender, ResponseToolbarItemClickedEventArgs e)
{
    // Call the logic similar to HandleResponseToolbarItemClick
}

{% endhighlight %}
{% endtabs %}


#### Customized ResponseToolBar Template

The **ResponseToolbarItem** in [SfAIAssistView](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Chat.SfAIAssistView.html) can be customized using the ItemTemplate property to define a custom appearance and behavior. This allows you to display icons, buttons, text, or even controls like Path, Image, or TextBlock
{% tabs %}

{% highlight xaml %}

 <Grid x:Name="grid1">
     <syncfusion:SfAIAssistView x:Name="aiAssistView" CurrentUser="{Binding CurrentUser}"  
                                Messages="{Binding Chats}" >
         <syncfusion:SfAIAssistView.ResponseToolbarItems>
             <syncfusion:ResponseToolbarItem ItemType="Custom" Tooltip="Copy">
                 <syncfusion:ResponseToolbarItem.ItemTemplate>
                     <DataTemplate>
                         <Button ToolTipService.ToolTip="Copy to clipboard"
                                 HorizontalAlignment="Left"
                                 Padding="5,2"
                                 Background="Transparent"
                                 BorderThickness="0">
                             <StackPanel Orientation="Horizontal" VerticalAlignment="Center">
                                 <Path Width="16" Height="16" Fill="Black"
                                       Stretch="Uniform"
                                       Data="M3,1 L10,1 C10.55,1 11,1.45 11,2 L11,3 L12,3 C12.55,3 13,3.45 13,4 L13,14 C13,14.55 12.55,15 12,15 L4,15 C3.45,15 3,14.55 3,14 L3,4 C3,3.45 3.45,3 4,3 L5,3 L5,2 C5,1.45 5.45,1 6,1 Z M5,3 L9,3 L9,2 L5,2 Z M4,5 L12,5 L12,14 L4,14 Z"/>
                                 <TextBlock Text="Copy" Margin="6,0,0,0" VerticalAlignment="Center"/>
                             </StackPanel>
                         </Button>
                     </DataTemplate>
                 </syncfusion:ResponseToolbarItem.ItemTemplate>
             </syncfusion:ResponseToolbarItem>
         </syncfusion:SfAIAssistView.ResponseToolbarItems>
     </syncfusion:SfAIAssistView>
 </Grid>

{% endhighlight %} 

{% endtabs %}

![CustomizedResponseToolBarTemplate feature in WinUI SfAIAssistView control](aiassistview_images/winui_aiassistview_customizedresponsetoolbartemplate.png)
