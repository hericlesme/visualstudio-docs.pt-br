---
title: "Inserindo um diagrama em um formulário do Windows | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 695d2bc18486cb50c85c0490c59e714aca087ad4
ms.lasthandoff: 02/22/2017

---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Inserindo um diagrama em um formulário do Windows Forms
Você pode incorporar um diagrama DSL em um controle do Windows, que aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela.  
  
## <a name="embedding-a-diagram"></a>Inserindo um diagrama  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Para inserir um diagrama DSL em um controle do Windows  
  
1.  Adicione um novo **controle de usuário** arquivo no projeto DslPackage.  
  
2.  Adicione um controle de painel ao controle de usuário. Este painel contém o diagrama DSL.  
  
     Adicione outros controles que você precisa.  
  
     Defina as propriedades de ancoragem de controles.  
  
3.  No Solution Explorer, clique no arquivo de controle de usuário e clique em **Exibir código**. Adicione esse construtor e a variável no código:  
  
    ```c#  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Adicione um novo arquivo ao projeto DslPackage, com o seguinte conteúdo:  
  
    ```  
    using System.Windows.Forms;  
    namespace Company.MyDSL  
    {  
      partial class MyDSLDocView  
      {  
        private UserControl1 container;  
        public override IWin32Window Window  
        {  
          get  
          {  
            if (container == null)  
            {  
              // Put our own form inside the DSL window:  
              container = new UserControl1(this,  
                (Control)base.Window);  
            }  
            return container;  
    } } } }  
  
    ```  
  
5.  Para testar o DSL, pressione F5 e abrir um arquivo de modelo de exemplo. O diagrama é exibido dentro do controle. A caixa de ferramentas e outros recursos funcionam normalmente.  
  
#### <a name="updating-the-form-using-store-events"></a>Atualizando o formulário usando eventos de armazenamento  
  
1.  No designer de formulário, adicione um **ListBox** chamado `listBox1`. Isso exibirá uma lista dos elementos no modelo. Seja mantido em synchronism com o modelo usando *armazenar eventos*. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  No arquivo de código personalizado, mais substitua métodos à classe DocView:  
  
    ```  
  
    partial class MyDSLDocView  
    {  
     /// <summary>  
     /// Register store event listeners.  
     /// This method is called when the model and diagram    
     /// have completed loading.   
     /// </summary>  
     protected override bool LoadView()  
      {  
        bool result = base.LoadView();  
        Store store = this.DocData.Store;  
        EventManagerDirectory emd = store.EventManagerDirectory;  
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));  
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));  
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));  
  
        // Do the initial parts list:  
        container.SetUpFormFromModel();  
        return result;  
      }  
     /// <summary>  
     /// Listener method called on creation of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void AddElement(object sender, ElementAddedEventArgs e)  
     {  
       container.Add(e.ModelElement as ExampleElement);  
     }  
     /// <summary>  
     /// Listener method called after deletion of each instance of   
     /// the ExampleElement class or its subclasses.  
     /// </summary>  
     private void RemoveElement(object sender, ElementDeletedEventArgs e)  
     {  
       container.Remove(e.ModelElement as ExampleElement);  
     }  
  
    ```  
  
3.  No code-behind do controle de usuário, insira métodos para escutar elementos adicionados e removidos:  
  
    ```  
  
          public partial class UserControl1 : UserControl { ...  
  
    private ExampleModel modelRoot;  
  
    internal void Add(ExampleElement e) { UpdatePartsList(); }  
    internal void Remove(ExampleElement e) { UpdatePartsList(); }  
  
    internal void SetUpFormFromModel()  
    {  
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;  
      UpdatePartsList();  
    }  
  
    private void UpdatePartsList()  
    {  
      StringBuilder builder = new StringBuilder();  
      listBox1.Items.Clear();  
      foreach (ExampleElement c in modelRoot.Elements)  
      {  
        listBox1.Items.Add(c.Name);  
      }  
    }  
  
    ```  
  
4.  Para testar o DSL, pressione F5 e na instância experimental do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra um arquivo de modelo de exemplo.  
  
     Observe que a caixa de listagem mostra uma lista dos elementos no modelo e se ela está correta, depois de qualquer adição ou exclusão e desfazer e refazer.  
  
## <a name="see-also"></a>Consulte também  
 [Navegando e atualizando um modelo no código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)