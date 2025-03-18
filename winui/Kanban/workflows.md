---
layout: post
title: Workflows in .NET WinUI Kanban Board control | Syncfusion<sup>®</sup>
description: Learn here all about Workflows support in Syncfusion<sup>®</sup> .NET WinUI Kanban Board (SfKanban) control and more.
platform: WinUI
control: SfKanban
documentation: ug
---

# Workflows in WinUI Kanban (SfKanban) control

The WinUI Kanban `Workflow` allows to set the flow of cards between the columns. It provides restriction on columns when the card is moved from one column to another column. It provides support to prevent the drag and drop action on the column.

To define the flow of card transitions between different states, create an instance of the KanbanWorkflow class and add it to the Workflows property of the SfKanban to define the `Workflow` for each column. The KanbanWorkflow class contains the following properties to specify the source and target categories.

* [`Category`](https://help.syncfusion.com/cr/winui/Syncfusion.UI.Xaml.Kanban.KanbanModel.html#:~:text=System.String-,Category,-Gets%20or%20sets) – Used to define the source category/state..

* `AllowedTransitions` – Used to define the list of categories/states to which a card can be moved from the current category.
 
{% tabs %}
{% highlight xaml tabtitle="MainWindow.xaml" hl_lines="12 13 14 15 16 17 18 20 21 22 23 24  26 27 28 29 30 31 32 " %}
     
     <kanban:SfKanban
          x:Name="kanban"
          AutoGenerateColumns="False"
          CardDragEnd="kanban_DragEnd"
          CardDragStart="kanban_DragStart"
          ItemsSource="{Binding PizzaShop}">

            <kanban:SfKanban.DataContext>
                <local:MenuDetails/>
            </kanban:SfKanban.DataContext>

            <kanban:SfKanban.Workflows>
                <kanban:WorkflowCollection>
                    <kanban:KanbanWorkflow Category="Menu">
                        <kanban:KanbanWorkflow.AllowedTransitions>
                            <system:String>Dining</system:String>
                            <system:String>Delivery</system:String>
                        </kanban:KanbanWorkflow.AllowedTransitions>
                    </kanban:KanbanWorkflow>

                    <kanban:KanbanWorkflow Category="Dining">
                        <kanban:KanbanWorkflow.AllowedTransitions>
                            <system:String>Ready to Serve</system:String>
                        </kanban:KanbanWorkflow.AllowedTransitions>
                    </kanban:KanbanWorkflow>

                    <kanban:KanbanWorkflow Category="Delivery">
                        <kanban:KanbanWorkflow.AllowedTransitions>
                            <system:String>Ready to Delivery</system:String>
                        </kanban:KanbanWorkflow.AllowedTransitions>
                    </kanban:KanbanWorkflow>
                </kanban:WorkflowCollection>
            </kanban:SfKanban.Workflows>

            <kanban:KanbanColumn Title="Menu" Categories="Menu" />
            <kanban:KanbanColumn Title="Order" Categories="Dining,Delivery" />
            <kanban:KanbanColumn
            Title="Ready to Serve"  
            AllowDrag="False"
            Categories="Ready to Serve" />
            <kanban:KanbanColumn
            Title="Ready to Delivery"
            AllowDrag="False"
            Categories="Ready to Delivery"/>
        </kanban:SfKanban>

{% endhighlight %}
{% highlight c# tabtitle="MainWindow.xaml.cs" hl_lines="1 2 3 4" %}
            var workflow = new WorkflowCollection();
            workflow.Add(new KanbanWorkflow() { Category = "Menu", AllowedTransitions = { "Dining", "Delivery" } });
            workflow.Add(new KanbanWorkflow() { Category = "Dining", AllowedTransitions = { "Ready to Serve" } });
            workflow.Add(new KanbanWorkflow() { Category = "Delivery", AllowedTransitions = { "Ready to Delivery" } });

    private void kanban_DragStart(object sender, KanbanDragStartEventArgs e)
            {
                if (e.SelectedColumn.Title.ToString() == "Menu")
                {
                    e.KeepCard = true;
                }
            }

    private void kanban_DragEnd(object sender, KanbanDragEndEventArgs e)
            {
                if (e.SelectedColumn.Title.ToString() == "Menu" && e.SelectedColumn != e.TargetColumn &&
                    e.TargetColumn.Title.ToString() == "Order")
                {
                    e.IsCancel = true;

                    KanbanModel selectedCard = e.SelectedCard.Content as KanbanModel;

                    KanbanModel model = new KanbanModel();
                    model.Category = e.TargetKey;
                    model.Description = selectedCard.Description;
                    model.ImageURL = selectedCard.ImageURL;
                    model.ColorKey = selectedCard.ColorKey;
                    model.Tags = selectedCard.Tags;
                    model.ID = selectedCard.ID;
                    model.Title = selectedCard.Title;

                    (kanban.ItemsSource as ObservableCollection<KanbanModel>).Add(model);
                }
            }
{% endhighlight %}
{% highlight C# tabtitle="ViewModel.cs" %} 

     public class MenuDetails
    {
        public ObservableCollection<KanbanModel> PizzaShop
        {
            get;
            set;
        }

        public MenuDetails()
        {
            PizzaShop = new ObservableCollection<KanbanModel>();

            KanbanModel item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Double Cheese Margherita";
            item.Description = "The minimalist classic with a double helping of cheese";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/DoubleCheeseMargherita.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Bucolic Pie";
            item.Description = "The pizza you daydream about to escape city life. Onions, peppers, and tomatoes";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Bucolicpie.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Bumper Crop";
            item.Description = "Can't get enough veggies? Eat this. Carrots, mushrooms, potatoes, and way more";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Bumpercrop.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Spice of Life";
            item.Description = "Thrill-seeking, heat-seeking pizza people only.  It's hot. Trust us";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Spiceoflife.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Order";
            item.Title = "Very Nicoise";
            item.Description = "Anchovies, Dijon vinaigrette, shallots, red peppers, and potatoes";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Verynicoise.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Margherita";
            item.Description = "The classic. Fresh tomatoes, garlic, olive oil, and basil. For pizza purists and minimalists only";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Margherita.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Very Nicoise";
            item.Description = "Anchovies, Dijon vinaigrette, shallots, red peppers, and potatoes";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Verynicoise.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Ready to Serve";
            item.Title = "Margherita";
            item.Description = "The classic. Fresh tomatoes, garlic, olive oil, and basil. For pizza purists and minimalists only";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Margherita.png", UriKind.RelativeOrAbsolute);
            item.ColorKey = "Ready";
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Ready to Delivery";
            item.Title = "Salad Daze";
            item.Description = "Pretty much salad on a pizza. Broccoli, olives, cherry tomatoes, red onion";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Saladdaze.png", UriKind.RelativeOrAbsolute);
            item.ColorKey = "Delivery";
            PizzaShop.Add(item);

            item = new KanbanModel();
            item.Category = "Menu";
            item.Title = "Salad Daze";
            item.Description = "Pretty much salad on a pizza. Broccoli, olives, cherry tomatoes, red onion";
            item.Tags = new string[] { "Onions", "Bell Pepper", "Pork", "Cheese" };
            item.ImageURL = new Uri(@"syncfusion.kanbandemos.wpf;component/Assets/Kanban/Saladdaze.png", UriKind.RelativeOrAbsolute);
            PizzaShop.Add(item);
        }
    }
{% endhighlight %}
{% endtabs %}

By following the code snippet, you will notice that the card picked from the Open state is not allowed to be dropped in the Review state because we have defined that the card can only move from the Open state to the In Progress, Closed, Closed No Changes, Won't Fix states and not to any other states.
