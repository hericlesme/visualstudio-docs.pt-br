---
title: Interface de assistente (IDTWizard) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba6952bce6d99149f2a8f18b7d2eac12cbd08761
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="wizard-interface-idtwizard"></a>Interface de assistente (IDTWizard)
O ambiente de desenvolvimento integrado (IDE) usa o <xref:EnvDTE.IDTWizard> interface para se comunicar com os assistentes. Assistentes devem implementar essa interface para ser instalada no IDE.  
  
 O <xref:EnvDTE.IDTWizard.Execute%2A> é o único método associado com o <xref:EnvDTE.IDTWizard> interface. Assistentes de implementam esse método e o IDE chama o método na interface. O exemplo a seguir mostra a assinatura do método.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 O mecanismo de início é semelhante para ambos os **novo projeto** e **Adicionar Novo Item**assistentes. Para começar, você deve chamar o <xref:EnvDTE.IDTWizard> interface definida em Dteinternal.h. A única diferença é o conjunto de contexto e os parâmetros personalizados que são passados para a interface quando a interface é chamada.  
  
 As informações a seguir descrevem o <xref:EnvDTE.IDTWizard> interface assistentes devem implementar para funcionar no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. O IDE chama o <xref:EnvDTE.IDTWizard.Execute%2A> método no assistente, passando o seguinte:  
  
-   O objeto DTE  
  
     O objeto DTE é a raiz do modelo de automação.  
  
-   O identificador para a caixa de diálogo janela conforme mostrado no segmento de código, `hwndOwner ([in] long)`.  
  
     O assistente usa esse `hwndOwner` como o pai para a caixa de diálogo do assistente.  
  
-   Parâmetros de contexto passado para a interface como variante de SAFEARRAY conforme mostrado no segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parâmetros de contexto contém uma matriz de valores que são específicos para o tipo de assistente que está sendo iniciado e o estado atual do projeto. O IDE passa parâmetros de contexto para o assistente. Para obter mais informações, consulte [parâmetros de contexto](../../extensibility/internals/context-parameters.md).  
  
-   Parâmetros personalizados passado para a interface como uma variante de SAFEARRAY conforme mostrado no segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parâmetros personalizados contêm uma matriz de parâmetros definidos pelo usuário. Um arquivo. vsz passa parâmetros personalizados para o IDE. Os valores são determinados pelo `Param=` instruções. Para obter mais informações, consulte [parâmetros personalizados](../../extensibility/internals/custom-parameters.md).  
  
-   São valores de retorno para a interface  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)