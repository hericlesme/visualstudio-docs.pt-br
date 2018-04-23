---
title: Método GetAutoInsertExtensions | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67f6bfcb0ee38acf9abb604f28fa95eeaa605fde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="getautoinsertextensions-method"></a>Método GetAutoInsertExtensions
  Obtém informações sobre os aplicativos do Office que serão inseridos automaticamente durante a depuração.  
  
 Este método está reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*psaExtensionNames*|Os nomes de extensão dos aplicativos do Office.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor HRESULT que indica se o método foi concluída com êxito.  
  
## <a name="remarks"></a>Comentários  
 Cada aplicativo do Office a ser inserido é retornado como um nome de extensão de aplicativo do Office, que corresponde a um valor em HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. O host deve pesquisar esses valores no registro e, em seguida, inserir automaticamente as extensões.  
  
  