---
title: Criar visualizadores personalizados de dados | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2a1602808cb21bd247d2bb1d249ab7ddea81524
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-visualizers-of-data"></a>Criar visualizadores personalizados de dados
 Os visualizadores são componentes do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] interface de usuário do depurador. Um *visualizador* cria uma caixa de diálogo ou outra interface para exibir uma variável ou um objeto de forma que seja apropriada para seu tipo de dados. Por exemplo, um visualizador de HTML interpreta uma cadeia de caracteres de HTML e exibe o resultado como seria exibido em uma janela do navegador; um visualizador de bitmap interpreta uma estrutura de bitmap e exibe o gráfico que o representa. Alguns visualizadores permitem modificar assim como exibir os dados.

 O [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] depurador inclui seis visualizadores padrão. Esses são o texto, os visualizadores HTML, XML e JSON, que funcionam em objetos de cadeia de caracteres. o Visualizador de árvore WPF, para exibir as propriedades de uma árvore visual do objeto WPF; e o Visualizador de conjunto de dados, o que funciona para objetos de conjunto de dados, DataView e DataTable. Visualizadores adicionais podem estar disponíveis para download da Microsoft Corporation no futuro e estão disponíveis por meio de terceiros e da comunidade. Além disso, você pode escrever seus próprios visualizadores e instalá-los no [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] depurador.

 > [!NOTE]
 > Para criar um visualizador personalizado para código nativo, consulte o [Visualizador de depurador nativo SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) exemplo. Em aplicativos da UWP e Windows 8. x, não há suporte para os visualizadores personalizados.

 No depurador, os visualizadores são representados por um ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone visualizador"). Quando você vir o ícone de lupa em uma **DataTip**, em uma janela de depurador, como o **inspecionar** janela, ou o **QuickWatch** caixa de diálogo, você pode clicar na lupa para Selecione um visualizador apropriado para o tipo de dados do objeto correspondente.

## <a name="overview-of-custom-visualizers"></a>Visão geral dos visualizadores personalizados

Você pode escrever um visualizador personalizado para um objeto de qualquer classe gerenciada com exceção de <xref:System.Object> ou <xref:System.Array>.  
  
 A arquitetura de um visualizador de depurador tem duas partes:  
  
-   O *do lado do depurador* executa com o depurador do Visual Studio. O código do lado depurador cria e exibe a interface do usuário para o visualizador.  
  
-   O *lado a ser depurado* é executado no processo do Visual Studio está depurando (o *depurado*).  
  
 O objeto de dados que você deseja visualizar (um objeto String, por exemplo) existe no processo a ser depurado. Assim, o lado a ser depurado precisa enviar esse objeto de dados para o lado do depurador, que pode então exibi-lo usando uma interface de usuário que você cria.  
  
 O lado do depurador recebe esse objeto de dados para ser visualizado de um *provedor objeto* que implementa o <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interface. O lado a ser depurado envia o objeto de dados por meio de *objeto de fonte de*, que é derivada de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. O provedor do objeto também pode enviar dados de volta para a origem do objeto, que permite escrever um visualizador que edita, além de exibir, dados. O provedor do objeto pode ser substituído para se comunicar com o avaliador de expressão e, consequentemente, com a origem do objeto  
  
 O lado a ser depurado e o lado do depurador comunicam-se por meio do <xref:System.IO.Stream>. Os métodos são fornecidos para serializar um objeto de dados em um <xref:System.IO.Stream> e desserializar o <xref:System.IO.Stream> de volta para um objeto de dados.  
  
 O código do lado a ser depurado é especificado usando o atributo DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Para criar a interface do usuário do visualizador no lado do depurador, você deverá criar uma classe que herda de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> e substitui o método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para exibir a interface.  
  
 Você pode usar <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para exibir formulários, caixas de diálogo e os controles do Windows a partir do visualizador.  
  
 O suporte para tipos genéricos é limitado. Você poderá escrever um visualizador para um destino que é um tipo genérico somente se o tipo genérico for um tipo aberto. Essa restrição é a mesma que a restrição ao usar o atributo `DebuggerTypeProxy`. Para obter detalhes, consulte [Using DebuggerTypeProxy Attribute](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Os visualizadores personalizados podem ter considerações de segurança. Consulte [considerações de segurança do visualizador](../debugger/visualizer-security-considerations.md).  
  
 Os procedimentos a seguir dão uma exibição de alto nível do que você precisa fazer para criar um visualizador. Para obter uma explicação mais detalhada, consulte [passo a passo: escrevendo um visualizador em c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Para criar o lado do depurador  
  
1.  Use os métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> para obter o objeto visualizado no lado do depurador.  
  
2.  Crie uma classe que herda de <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Substitua o método <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> para exibir sua interface. Use os métodos <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> para exibir os formulários, as caixas de diálogo e os controles do Windows como parte da interface.  
  
4.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, permitindo que você tenha um visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Para criar o lado a ser depurado  
  
1.  Aplique <xref:System.Diagnostics.DebuggerVisualizerAttribute>, permitindo que você tenha um visualizador (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) e uma origem do objeto (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). Se você omitir a origem do objeto, uma fonte do objeto padrão será usada  
  
2.  Se você quiser que o visualizador edite objetos de dados, bem como exibi-los, precisará substituir os métodos `TransferData` ou `CreateReplacementObject` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>Nesta seção
  
 [Passo a passo: escrevendo um visualizador em C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Passo a passo: escrevendo um visualizador em Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Como instalar um visualizador](../debugger/how-to-install-a-visualizer.md)  
  
 [Como testar e depurar um visualizador](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referência de API do visualizador](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Exibir dados no depurador](../debugger/viewing-data-in-the-debugger.md)