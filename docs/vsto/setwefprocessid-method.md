---
title: "Método SetWefProcessId | Microsoft Docs"
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
ms.openlocfilehash: 5c27588eb6d09c0565b4b4d8faec52239ef792f7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="setwefprocessid-method"></a>Método SetWefProcessId
  Fornece o identificador do processo que executará o conteúdo da estrutura de extensões da Web (WEF).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|*dwProcessId*|O identificador do processo que será usado para executar o WEF conteúdo.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor HRESULT que indica se o método foi concluída com êxito.  
  
## <a name="remarks"></a>Comentários  
 Esse método deve ser chamado depois que o processo de conteúdo WEF é criado, mas antes de qualquer conteúdo WEF é executado.  
  
 Se você quiser que o ambiente de desenvolvimento para anexar um depurador ao processo WEF conteúdo, o ambiente deve executar esta operação em sua implementação deste método.  
  
  