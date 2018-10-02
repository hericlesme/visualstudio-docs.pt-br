---
title: Função SccGetVersion | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2b5c5e5e6035d6ce0b81ba747efa3cea65ab2f97
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474315"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [função SccGetVersion](https://docs.microsoft.com/visualstudio/extensibility/sccgetversion-function).  
  
Essa função obtém o número de versão de API de plug-in de controle de origem compatível com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `LONG` tipo de dados que contém o número de versão de API de plug-in de controle de origem com suporte:  
  
|WORD|Descrição|  
|----------|-----------------|  
|HIWORD|Versão principal|  
|LOWORD|Versão secundária|  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, se um plug-in de controle de origem dá suporte à versão 1.3 da API de plug-in de controle de origem, essa função retornará 0x0103.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)

