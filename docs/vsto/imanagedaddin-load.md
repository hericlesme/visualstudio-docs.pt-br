---
title: IManagedAddin::Load | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 545560c5f02437925c2f93e9c6dc3113e1cddd0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  