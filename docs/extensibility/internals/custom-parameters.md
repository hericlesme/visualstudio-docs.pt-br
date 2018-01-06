---
title: "Parâmetros personalizados | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 17a629c2d93bb5e91fb301d4da9dca825e5b8917
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-parameters"></a>Parâmetros personalizados
Parâmetros personalizados controlam a operação de um assistente depois que tiver iniciado um assistente. Um arquivo. vsz relacionados fornece uma matriz de parâmetros definidos pelo usuário que são empacotados pelo ambiente de desenvolvimento integrado (IDE) e passados para o assistente como uma matriz de cadeias de caracteres quando o assistente for iniciado. Em seguida, o assistente analisa a matriz de cadeias de caracteres e usa as informações para controlar a operação real do assistente. Dessa maneira, um assistente pode personalizar a funcionalidade de acordo com o conteúdo do arquivo. vsz.  
  
 Parâmetros de contexto, por outro lado, definem o estado do projeto quando o assistente for iniciado. Para obter mais informações, consulte [parâmetros de contexto](../../extensibility/internals/context-parameters.md).  
  
 A seguir está um exemplo de um arquivo. vsz com parâmetros personalizados:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 O autor do arquivo. vsz adiciona os valores dos parâmetros. Quando um usuário seleciona **novo projeto** ou **Adicionar Novo Item** no menu arquivo ou clicando em um projeto no **Solution Explorer**, o IDE coleta esses valores em uma matriz de cadeias de caracteres. O IDE, em seguida, chama o projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método com o <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> sinalizador conjunto e as chamadas de projeto de <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> método que é responsável por executar o assistente e retornar o resultado.  
  
 O assistente é responsável pela análise a matriz de cadeias de caracteres e atuando em cadeias de caracteres adequadamente. Dessa forma, com a implementação de parâmetros personalizados, você pode criar um assistente que executa uma variedade de funções. Em outras palavras, um assistente pode ter três arquivos. vsz diferentes. Cada arquivo passa diferentes conjuntos de parâmetros personalizados para controlar o comportamento do assistente em várias situações.  
  
 Para obter mais informações, consulte [Assistente (. Arquivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)