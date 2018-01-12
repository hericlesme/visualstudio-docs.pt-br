---
title: Interface IWefDebuggingSupport | Microsoft Docs
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
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="iwefdebuggingsupport-interface"></a>Interface IWefDebuggingSupport
  Implementado por um ambiente de depuração, como o Visual Studio, para facilitar a depuração de aplicativos do Office. O aplicativo do Office, como o Word ou Excel, obtém essa interface do Visual Studio e, em seguida, chama métodos na interface em determinados pontos durante a sessão de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos que define a interface IWefDebuggingSupport.  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Obtém informações sobre os aplicativos do Office que serão inseridos automaticamente durante a depuração.|  
|[Método SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornece o identificador do processo que executará o conteúdo da estrutura de extensões da Web (WEF).|  
  
  