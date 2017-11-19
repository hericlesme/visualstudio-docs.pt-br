---
title: "Provedor de símbolo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f845e18bbd4c06d5652571ec83270a80d31ec852
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="symbol-provider"></a>Provedor de símbolo
Uma implementação do avaliador de expressão deve acessar as informações de depuração simbólicas geradas pelo compilador de linguagem para avaliar expressões e variáveis. Isso é feito pelo uso de interfaces de um provedor de símbolo (SP), também chamado de um manipulador de símbolo.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Fornece SPs para código gerenciado, bem como código nativo usando o formato de arquivo de símbolo de banco de dados de programa (PDB). A menos que haja um forte necessário para o programa use símbolos armazenados em um formato personalizado, é recomendável que você use os SPs fornecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração esperam para se comunicar com os SPs usando as interfaces do Common Language Runtime (CLR). Como resultado, um SP que trabalhará com os mecanismos de depuração do Visual Studio deve dar suporte o CLR. Uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Se o SP trabalhar somente com o mecanismo de depuração personalizado, você pode implementar o SP como desejar dependendo das necessidades de seu mecanismo de depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)