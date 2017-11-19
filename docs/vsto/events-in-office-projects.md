---
title: Eventos em projetos do Office | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48670b03444a8701dc3c23fe591a962e01f51f31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="events-in-office-projects"></a>Eventos em projetos do Office
  Cada modelo de projeto do Office automaticamente gera vários manipuladores de eventos. Manipuladores de eventos para personalizações no nível do documento são ligeiramente diferentes de manipuladores de eventos para suplementos do VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="document-level-projects"></a>Projetos no nível de documento  
 O Visual Studio fornece código gerado por trás de documentos novos ou existentes ou planilhas em personalizações no nível do documento. Esse código gera dois eventos diferentes: **inicialização** e **desligamento**.  
  
### <a name="startup-event"></a>Evento de inicialização  
 O **inicialização** é gerado para cada um dos itens de host (documento, pasta de trabalho ou planilha) depois que o documento está em execução e todo o código de inicialização no assembly foi executado. É a última coisa a executar no construtor da classe que seu código está sendo executado no. Para obter mais informações sobre itens de host, consulte [itens de Host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md).  
  
 Quando você cria um projeto no nível do documento, o Visual Studio cria manipuladores de eventos para o **inicialização** eventos nos arquivos de código gerado:  
  
-   Para projetos do Microsoft Office Word, o manipulador de eventos é chamado de `ThisDocument_Startup`.  
  
-   Para projetos do Microsoft Office Excel, os manipuladores de eventos com os seguintes nomes:  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### <a name="shutdown-event"></a>Eventos de desligamento  
 O **desligamento** é gerado para cada um dos itens de host (documento ou planilha) quando o domínio do aplicativo que seu código é carregado no está prestes a descarregar. É a última coisa a ser chamado na classe conforme ele descarrega.  
  
 Quando você cria um projeto no nível do documento, o Visual Studio cria manipuladores de eventos para o **desligamento** eventos nos arquivos de código gerado:  
  
-   Para projetos do Microsoft Office Word, o manipulador de eventos é chamado de `ThisDocument_Shutdown`.  
  
-   Para projetos do Microsoft Office Excel, os manipuladores de eventos com os seguintes nomes:  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  Não remover programaticamente controles durante o **desligamento** manipulador de eventos do documento. Os elementos de interface do usuário do documento não estão mais disponíveis quando o **desligamento** evento ocorre. Se você quiser remover controles antes do aplicativo for fechado, adicione seu código para outro manipulador de eventos, como **BeforeClose** ou **BeforeSave**.  
  
### <a name="event-handler-method-declarations"></a>Declarações de método do manipulador de eventos  
 Cada declaração de método do manipulador de eventos tem os mesmos argumentos passados para ele: *remetente* e *e*. No Excel, o *remetente* argumento se refere à planilha, como `Sheet1` ou `Sheet2`; no Word, o *remetente* argumento refere-se ao documento. O *e* argumento refere-se aos argumentos padrão para um evento, que não são usados nesse caso.  
  
 O exemplo de código a seguir mostra os manipuladores de eventos padrão no nível de documento para Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]  
  
 O exemplo de código a seguir mostra os manipuladores de eventos padrão no nível de documento para Excel.  
  
> [!NOTE]  
>  O exemplo de código a seguir mostra os manipuladores de eventos de `Sheet1` classe. Os nomes dos manipuladores de eventos em outras classes de item de host correspondem ao nome da classe. Por exemplo, o `Sheet2` classe, o **inicialização** manipulador de eventos é chamado `Sheet2_Startup`. No `ThisWorkbook` classe, o **inicialização** manipulador de eventos é chamado `ThisWorkbook_Startup`.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]  
  
### <a name="order-of-events-in-document-level-excel-projects"></a>Ordem de eventos em projetos do Excel de nível de documento  
 O **inicialização** manipuladores de eventos em projetos do Excel são chamados nesta ordem:  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  Outras planilhas em ordem.  
  
 O **desligamento** manipuladores de eventos em uma solução de pasta de trabalho são chamados nesta ordem:  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  Outras planilhas em ordem.  
  
 A ordem é determinada quando o projeto é compilado. Se o usuário reorganiza as folhas de tempo de execução, ele não altera a ordem que os eventos são gerados na próxima vez em que a pasta de trabalho é aberta ou fechada.  
  
## <a name="vsto-add-in-projects"></a>Projetos de suplemento do VSTO  
 O Visual Studio fornece código gerado nos suplementos do VSTO. Esse código gera dois eventos diferentes: <xref:Microsoft.Office.Tools.AddInBase.Startup> e <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.  
  
### <a name="startup-event"></a>Evento de inicialização  
 O <xref:Microsoft.Office.Tools.AddIn.Startup> é gerado depois que o suplemento do VSTO é carregado e todo o código de inicialização no assembly foi executado. Esse evento é manipulado pelo `ThisAddIn_Startup` método no arquivo de código gerado.  
  
 Código de `ThisAddIn_Startup` manipulador de eventos é o primeiro código de usuário para ser executado, a menos que seu suplemento do VSTO substitui o <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> método. Nesse caso, o `ThisAddIn_Startup` manipulador de eventos é chamado após <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.  
  
 Não adicione o código a `ThisAdd-In_Startup` manipulador de eventos se o código requer um documento a ser aberto. Em vez disso, adicione esse código para um evento que o aplicativo do Office emite quando um usuário cria ou abre um documento. Para obter mais informações, consulte [acessar um documento quando o Office aplicativo inicia](../vsto/programming-vsto-add-ins.md#AccessingDocuments).  
  
 Para obter mais informações sobre a sequência de inicialização de suplementos do VSTO, consulte [suplementos da arquitetura do VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="shutdown-event"></a>Eventos de desligamento  
 O <xref:Microsoft.Office.Tools.AddInBase.Shutdown> é gerado quando o domínio de aplicativo que seu código é carregado no está prestes a ser descarregado. Esse evento é manipulado pelo `ThisAddIn_Shutdown` método no arquivo de código gerado. Este manipulador de eventos é o último código de usuário para ser executado quando o suplemento do VSTO é descarregado.  
  
#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Eventos de desligamento no Outlook VSTO suplementos  
 O <xref:Microsoft.Office.Tools.AddInBase.Shutdown> é gerado somente quando o usuário desativa o suplemento do VSTO usando a caixa de diálogo Suplementos COM no Outlook. Ele não é gerado quando o Outlook é fechado. Se você tiver código que deve ser executado quando o Outlook é fechado, lidar com qualquer um dos seguintes eventos:  
  
-   O <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> evento o <xref:Microsoft.Office.Interop.Outlook.Application> objeto.  
  
-   O <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> evento o <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto.  
  
> [!NOTE]  
>  Você pode forçar o Outlook para gerar o <xref:Microsoft.Office.Tools.AddInBase.Shutdown> quando ele sai modificando o registro de evento. No entanto, se um administrador reverte essa configuração, qualquer código que você adicione o `ThisAddIn_Shutdown` método não é executado quando o Outlook é fechado. Para obter mais informações, consulte [alterações de desligamento para o Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo soluções do Office](../vsto/developing-office-solutions.md)   
 [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)  
  
  