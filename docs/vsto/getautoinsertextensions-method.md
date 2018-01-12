---
title: "Método GetAutoInsertExtensions | Microsoft Docs"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a53148b0130dd05f3ffc3360a518f9b2b66002e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
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
  
  