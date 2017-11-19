---
title: IManagedAddin::Load | Microsoft Docs
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
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62c1af72158c0b416942e9124003dbeb06b584ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Chamado quando um gerenciado VSTO suplemento é carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*bstrManifestURL*|O caminho completo do manifesto para o suplemento do VSTO.|  
|*pdispApplication*|Um ponteiro para um IDispatch que representa o aplicativo de host que está carregando o suplemento do VSTO.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor HRESULT que indica se o método foi concluída com êxito.  
  
## <a name="remarks"></a>Comentários  
 Um manifesto é um arquivo (normalmente, um arquivo XML) que fornece informações que são usadas para ajudar a carregar o suplemento do VSTO. Por exemplo, um manifesto pode especificar o local do assembly do suplemento do VSTO e a classe de ponto de entrada para criar uma instância quando o suplemento do VSTO é carregado.  
  
 O *bstrManifestURL* parâmetro contém o valor da `Manifest` entrada sob o HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome do aplicativo >*\Addins\\*\<na ID de->* chave do registro para o suplemento do VSTO. Para obter mais informações, consulte [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Implementar o [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) método para executar tarefas como configurar a política de segurança e de domínio de aplicativo para o Add-in do VSTO que está sendo carregado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  