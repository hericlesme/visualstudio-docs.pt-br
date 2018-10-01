---
title: Provedor de símbolo | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464897"
---
# <a name="symbol-provider"></a>Provedor de símbolo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [provedor de símbolos](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider).  
  
Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólica geradas pelo compilador de linguagem para avaliar as variáveis e expressões. Ele faz isso consome as interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornece o SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados do programa (PDB). A menos que haja uma forte necessário para o seu programa usar símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] esperam de mecanismos de depuração conversar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP que estará trabalhando com os mecanismos de depuração do Visual Studio deve dar suporte o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Se sua SP trabalhar somente com o mecanismo de depuração personalizado, você pode implementar o SP como achar melhor dependendo das necessidades do seu mecanismo de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)

