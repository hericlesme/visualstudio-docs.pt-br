---
title: Hospedagem de IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b101460b3867c89862068d99412cd06edb884ef7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135698"
---
# <a name="intellisense-hosting"></a>Hospedagem do IntelliSense
Visual Studio permite a hospedagem de IntelliSense. IntellSense hospedagem permite que você fornecer o IntelliSense para código não é hospedado pelo editor de texto do Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedagem do IntelliSense  
 No Visual Studio, qualquer código que tenha acesso a um conjunto de conclusão e um buffer de texto pode obter IntelliSense windows de qualquer lugar na interface do usuário (IU). Alguns cenários de exemplo disso são conclusão no **inspecionar** janela ou da condição de uma janela de propriedades do ponto de interrupção.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementação  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualquer componente de interface do usuário que hospeda janelas pop-up do IntelliSense deve oferecer suporte a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface. A exibição de texto do editor de núcleo padrão inclui uma ação <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> implementação para manter a funcionalidade IntelliSense atual de interface. A maior parte do tempo, os métodos do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface que representa um subconjunto do que é implementado o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. O subconjunto inclui IntelliSense UI tratamento de cursor e manipulação de seleção e funcionalidade de substituição de texto simples. Além disso, o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface habilita IntelliSense "subject" e "contexto de" separado para que o IntelliSense pode ser fornecido para assuntos que não existem diretamente no buffer de texto que está sendo usado para o contexto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface provedor deve implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> dá suporte ao método para permitir que um cliente determinar que tipo de IntelliSense recursos do host.  
  
 Os sinalizadores de host definidos em [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), estão resumidas abaixo.  
  
|Sinalizador de Host do IntelliSense|Descrição|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|A configuração desta sinalizador significa que o buffer de contexto é somente leitura e edição ocorrem somente dentro do texto de assunto.|  
|IHF_NOSEPERATESUBJECT|Definir esse sinalizador significa que há não é nenhum assunto IntelliSense separado. O assunto existe no buffer de contexto, como nas tradicional <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense.|  
|IHF_SINGLELINESUBJECT|A configuração desta sinalizador significa que a entidade não for multilinha capaz, como uma única linha Editar no **inspecionar** janela.|  
|IHF_FORCECOMMITTOCONTEXT|Se esse sinalizador é definido e o buffer de contexto deve ser atualizado, o host permite que o sinalizador somente leitura no buffer de contexto para ser ignorado e edições para continuar.|  
|IHF_OVERTYPE|Edição (no assunto ou contexto) deve ser feito no modo sobrescrever.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Esses métodos de retorno de chamada são chamados pela janela de conclusão antes e depois o texto é confirmado, para habilitar o processamento de pré e pós.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interface é uma versão instanciável conjunta da janela de preenchimento padrão que é usada pelo ambiente de desenvolvimento integrado (IDE). Qualquer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface pode implementar rapidamente IntelliSense usando esta interface completor.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.TextManager.Interop>