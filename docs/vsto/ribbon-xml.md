---
title: "XML da faixa de opções | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
ms.assetid: a5945667-40e8-4191-9f1e-71c18ec30a2e
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c0a4dd8bb577ddc52ed6a97b2e412109c214335
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ribbon-xml"></a>XML da faixa de opções
  O item da faixa de opções (XML) permite que você personalize uma faixa de opções usando XML. Se você quiser personalizar a faixa de opções de forma que não é suportada pelo item da faixa de opções (Visual Designer), use o item de faixa de opções (XML). Para obter uma comparação de que você pode fazer com cada item, consulte [visão geral da faixa de opções](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="adding-a-ribbon-xml-item-to-a-project"></a>Adicionar um Item de faixa de opções (XML) a um projeto  
 Você pode adicionar uma **da faixa de opções (XML)** item a qualquer projeto do Office do **Adicionar Novo Item** caixa de diálogo. O Visual Studio adiciona automaticamente os arquivos a seguir ao seu projeto:  
  
-   Um arquivo XML da faixa de opções. Esse arquivo define a interface do usuário da faixa de opções (IU). Use esse arquivo para adicionar elementos de interface do usuário, como guias, grupos e controles. Para obter detalhes, consulte [referência do arquivo XML da faixa de opções](#RibbonDescriptorFile) mais adiante neste tópico.  
  
-   Um arquivo de código da faixa de opções. Este arquivo contém o *faixa classe*. Essa classe tem o nome que você especificou para o **da faixa de opções (XML)** item o **Adicionar Novo Item** caixa de diálogo. Aplicativos do Microsoft Office usam uma instância dessa classe para carregar a faixa de opções personalizada. Para obter detalhes, consulte [referência de classe da faixa de opções](#RibbonExtensionClass) mais adiante neste tópico.  
  
 Por padrão, esses arquivos adicionar um grupo personalizado para o **Add-Ins** guia na faixa de opções.  
  
## <a name="displaying-the-custom-ribbon-in-a-microsoft-office-application"></a>Exibindo a faixa de opções personalizada em um aplicativo do Microsoft Office  
 Depois de adicionar um **da faixa de opções (XML)** item ao seu projeto, você deve adicionar o código para o **ThisAddin**, **ThisWorkbook**, ou **ThisDocument** classe que substitui o método CreateRibbonExtensibilityObject e retorna a classe de XML da faixa de opções para o aplicativo do Office.  
  
 O exemplo de código a seguir substitui o método CreateRibbonExtensibilityObject e retorna uma classe de XML da faixa de opções chamada MyRibbon.  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="defining-the-behavior-of-the-custom-ribbon"></a>Definir o comportamento da faixa de opções personalizada  
 Você pode responder a ações do usuário, como clicar em um botão na faixa de opções, criando *métodos de retorno de chamada*. Métodos de retorno de chamada de eventos em controles de formulários do Windows são semelhantes, mas são identificados por um atributo no XML do elemento de interface do usuário. Escrever métodos na classe da faixa de opções e um controle chama o método que tem o mesmo nome que o valor do atributo. Por exemplo, você pode criar um método de retorno de chamada que é chamado quando um usuário clica em um botão na faixa de opções. São necessárias duas etapas para criar um método de retorno de chamada:  
  
-   Atribua um atributo a um controle no arquivo XML da faixa de opções que identifica um método de retorno de chamada no seu código.  
  
-   Defina o método de retorno de chamada na classe da faixa de opções.  
  
> [!NOTE]  
>  O Outlook requer uma etapa adicional. Para obter mais informações, consulte [Personalizando uma faixa de opções para Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
 Para uma explicação passo a passo que demonstra como automatizar um aplicativo da faixa de opções, consulte [passo a passo: Criando uma guia personalizada usando XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).  
  
### <a name="assigning-callback-methods-to-controls"></a>Atribuir métodos de retorno de chamada para controles  
 Para atribuir um método de retorno de chamada para um controle no arquivo XML da faixa de opções, adicione um atributo que especifica o tipo do método de retorno de chamada e o nome do método. Por exemplo, o elemento a seguir define um botão de alternância que tem um **onAction** chamado de método de retorno de chamada `OnToggleButton1`.  
  
```  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** é chamado quando o usuário executa a tarefa principal associada a um controle específico. Por exemplo, o **onAction** método de retorno de chamada de um botão de alternância é chamado quando o usuário clica no botão.  
  
 O método que você especificar no atributo pode ter qualquer nome. No entanto, ele deve corresponder ao nome do método que você definir no arquivo de código da faixa de opções.  
  
 Há muitos tipos diferentes de métodos de retorno de chamada que você pode atribuir a controles de faixa de opções. Para obter uma lista completa dos métodos de retorno de chamada disponíveis para cada controle, consulte o artigo técnico [Personalizando a Interface de usuário de faixa de opções do Office (2007) para desenvolvedores (parte 3 de 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15).  
  
###  <a name="CallBackMethods"></a>Define os métodos de retorno de chamada  
 Define os métodos de retorno de chamada na classe da faixa de opções no arquivo de código da faixa de opções. Um método de retorno de chamada tem vários requisitos:  
  
-   Ele deve ser declarado como público.  
  
-   O nome deve corresponder ao nome de um método de retorno de chamada que é atribuída a um controle no arquivo XML da faixa de opções.  
  
-   Sua assinatura deve corresponder à assinatura de um tipo de método de retorno de chamada que está disponível para o controle de faixa de opções associado.  
  
 Para obter uma lista completa das assinaturas de método de retorno de chamada para controles de faixa de opções, consulte o artigo técnico [Personalizando a Interface de usuário de faixa de opções do Office (2007) para desenvolvedores (parte 3 de 3)](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15). O Visual Studio não oferece suporte ao IntelliSense para os métodos de retorno de chamada que você criar no arquivo de código da faixa de opções. Se você criar um método de retorno de chamada que não corresponde a uma assinatura válida, o código será compilado, mas nada ocorrerá quando o usuário clica no controle.  
  
 Todos os métodos de retorno de chamada tem um <xref:Microsoft.Office.Core.IRibbonControl> parâmetro que representa o controle que chamou o método. Você pode usar esse parâmetro para reutilizar o mesmo método de retorno de chamada para vários controles. O exemplo de código a seguir demonstra um **onAction** método de retorno de chamada que executa tarefas diferentes, dependendo de qual controle o usuário clica.  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a>Referência do arquivo XML da faixa de opções  
 Você pode definir a faixa de opções personalizada pela adição de elementos e atributos para o arquivo XML da faixa de opções. Por padrão, o arquivo XML da faixa de opções contém o XML a seguir.  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 A tabela a seguir descreve os elementos padrão no arquivo XML da faixa de opções.  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|**customUI**|Representa a faixa de opções personalizada no projeto de suplemento do VSTO.|  
|**Faixa de opções**|Representa a faixa de opções.|  
|**guias**|Representa um conjunto de guias da faixa de opções.|  
|**guia**|Representa uma única guia de faixa de opções.|  
|**group**|Representa um grupo de controles na guia de faixa de opções.|  
  
 Esses elementos têm atributos que especificam a aparência e o comportamento da faixa de opções personalizada. A tabela a seguir descreve os atributos padrão no arquivo XML da faixa de opções.  
  
|Atributo|Elemento pai|Descrição|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|Identifica um método que é chamado quando o aplicativo carrega a faixa de opções.|  
|**idMso**|**guia**|Identifica uma guia interna para exibir na faixa de opções.|  
|**id**|**group**|Identifica o grupo.|  
|**rótulo**|**group**|Especifica o texto que aparece no grupo.|  
  
 Os elementos de padrão e atributos no arquivo XML da faixa de opções são um pequeno subconjunto dos elementos e atributos que estão disponíveis. Para obter uma lista completa dos atributos e elementos disponíveis, consulte o artigo técnico [Personalizando a Interface de usuário de faixa de opções do Office (2007) para desenvolvedores (parte 2 de 3)](http://msdn.microsoft.com/en-us/6b904f55-525f-4520-9b81-a017db65657b).  
  
##  <a name="RibbonExtensionClass"></a>Referência de classe da faixa de opções  
 Visual Studio gera a classe de faixa de opções no arquivo de código da faixa de opções. Adicione os métodos de retorno de chamada para controles da faixa de opções para essa classe. Essa classe implementa o <xref:Microsoft.Office.Core.IRibbonExtensibility> interface.  
  
 A tabela a seguir descreve os métodos padrão nesta classe.  
  
|Método|Descrição|  
|------------|-----------------|  
|`GetCustomUI`|Retorna o conteúdo do arquivo XML da faixa de opções. Aplicativos do Microsoft Office chamam este método para obter uma cadeia de caracteres XML que define a interface do usuário de sua faixa de opções personalizada. Esse método implementa o <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> método. **Observação:** `GetCustomUI` devem ser implementadas apenas para retornar o conteúdo do arquivo XML da faixa de opções; ele não deve ser usado para inicializar o suplemento do VSTO.   Em particular, você não deve tentar exibir caixas de diálogo ou outras janelas na sua `GetCustomUI` implementação. Caso contrário, a faixa de opções personalizada pode não funcionar corretamente. Se você precisar executar o código que inicializa o suplemento do VSTO, adicione o código para o `ThisAddIn_Startup` manipulador de eventos.|  
|`OnLoad`|Atribui o <xref:Microsoft.Office.Core.IRibbonControl> parâmetro para o `ribbon` campo. Aplicativos do Microsoft Office chamam este método quando eles carregam a faixa de opções personalizada. Você pode usar esse campo para atualizar dinamicamente a faixa de opções personalizada. Para obter mais informações, consulte o artigo técnico [Personalizando a Interface de usuário de faixa de opções do Office (2007) para desenvolvedores (parte 1 de 3)](http://msdn.microsoft.com/en-us/a4fd6d18-d4a8-4e64-bd89-f437208573d3).|  
|`GetResourceText`|Chamado pelo `GetCustomUI` método para obter o conteúdo do arquivo XML da faixa de opções.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da faixa de opções](../vsto/ribbon-overview.md)   
 [Passo a passo: Criando uma guia usando o XML da faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)  
  
  