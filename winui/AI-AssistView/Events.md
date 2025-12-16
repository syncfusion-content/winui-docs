---
layout: post
title: Event in WinUI AI AssistView (SfAIAssistView) | Syncfusion
description: Learn here all about Events support in Syncfusion AI AssistView control, its elements and more details.
platform: WinUI
control: SfAIAssistView
documentation: ug
---

# Event in WinUI AI AssistView (SfAIAssistView)

## PromptRequest event

This event notifies users when a prompt is submitted in the control. It can be used to validate user input before processing or trigger custom actions based on the prompt content.The input message and its result are passed through the PromptRequestEventArgs. This argument provides the following details:

InputMessage : Represents the input message value of the AI AssistView.
Handled : Boolean value indicating whether the input message in the Messages collection has been handled by the event.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfAIAssistView x:Name="sfAIAssistView" 
                            CurrentUser="{Binding CurrentUser}"  
                            Messages="{Binding Chats}" PromptRequest="SfAIAssistView_PromptRequest"/>

{% endhighlight %} 
{% highlight C# %}

SfAIAssistView sfAIAssistView = new SfAIAssistView();
sfAIAssistView.PromptRequest += SfAIAssistView_PromptRequest;

private void SfAIAssistView_PromptRequest(object sender, Syncfusion.UI.Xaml.Chat.PromptRequestEventArgs e)
{
    IMessage message = e.InputMessage;
    bool handled = e.Handled;
}

{% endhighlight %}
{% endtabs %}
