---
title: "Inserindo um diagrama em um formulário do Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c5f77fe45fd4289a442f151ff8d1174e68b353bc
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Inserindo um diagrama em um formulário do Windows Forms
Você pode inserir um diagrama DSL em um controle do Windows, que aparece no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] janela.  
  
## <a name="embedding-a-diagram"></a>Inserindo um diagrama  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Para inserir um diagrama DSL em um controle do Windows  
  
1.  Adicionar um novo **controle de usuário** arquivo ao projeto DslPackage.  
  
2.  Adicione um controle de painel ao controle do usuário. Este painel contém o diagrama de DSL.  
  
     Adicione outros controles que você precisa.  
  
     Defina as propriedades de âncora dos controles.  
  
3.  No Gerenciador de soluções, clique no arquivo de controle de usuário e clique em **Exibir código**. Adicione este construtor e a variável no código:  
  
    ```csharp  
  
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
  
#### <a name="updating-the-form-using-store-events"></a>Atualizando o formulário usando o armazenamento de eventos  
  
1.  No designer de formulário, adicione um **ListBox** chamado `listBox1`. Isso exibirá uma lista dos elementos no modelo. Ele será mantido em synchronism com o modelo usando *armazenar eventos*. Para obter mais informações, consulte [manipuladores de propagar alterações fora do modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  No arquivo de código personalizado, substitua mais métodos na classe DocView:  
  
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
  
3.  No code-behind o controle de usuário, insira os métodos para escutar elementos adicionados e removidos:  
  
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
  
     Observe que a caixa de listagem mostra uma lista dos elementos no modelo, e se ele está correto depois de qualquer adição ou exclusão e desfazer e refazer.  
  
## <a name="see-also"></a>Consulte também  
 [Navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escrevendo código para personalizar uma linguagem específica de domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)