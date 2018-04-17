---
title: Método SetWefProcessId | Microsoft Docs
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
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  