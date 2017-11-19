---
title: Modelo de pacotes de controle de origem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a8dacc0a3dfc230085c7575960238711d16d1ef8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="model-for-source-control-packages"></a>Modelo de pacotes de controle de origem
O modelo a seguir representa um exemplo de uma implementação de controle de origem. No modelo, você verá as interfaces que você deve implementar e os serviços de ambiente que você deve chamar. Como todos os serviços, você realmente chamar os métodos de uma interface específica que você pode obter por meio do serviço. Os nomes das classes são identificados para facilitar ainda mais ver como controle de origem é realizado.  
  
 ![SCC &#95; Exemplos TUP](../../extensibility/internals/media/scc_tup.gif "SCC_TUP")  
Exemplo de projeto de controle de origem  
  
## <a name="interfaces"></a>Interfaces  
 Você pode implementar o controle de origem para seus novos tipos de projeto no Visual Studio usando a lista de interfaces mostrado na tabela a seguir.  
  
|Interface|Use|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Chamado por editores antes de eles salvar ou alteração (sujo) arquivos e projetos. Essa interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Chamado por projetos para solicitar permissão para adicionar, remover ou renomear um arquivo ou diretório. Essa interface também é chamada por projetos para informar o ambiente quando aprovado adicionar, remover ou renomear a ação é concluído. Ele é acessado usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementado por qualquer entidade que é registrado para ser notificado quando adicionam projetos, renomear ou remover um arquivo ou diretório. Para registrar a notificação de evento, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Chamado por projetos para registrar com o pacote de controle de origem e para obter informações sobre o status de controle de origem. Essa interface é acessada usando o <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementado pelo projeto para responder a solicitações de controle de origem para obter informações sobre arquivos e obter a fonte de configurações de controle necessárias para o arquivo de projeto.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Oferecer suporte ao controle do código-fonte](../../extensibility/internals/supporting-source-control.md)