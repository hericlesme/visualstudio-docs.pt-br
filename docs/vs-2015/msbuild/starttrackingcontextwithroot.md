---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2c713b9f2b285bee56303b7d2142837d9afc62b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462087"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [StartTrackingContextWithRoot](https://docs.microsoft.com/visualstudio/msbuild/starttrackingcontextwithroot).  
  
  
Inicia um contexto de acompanhamento usando um arquivo de resposta especificando um marcador de raiz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 [in] `intermediateDirectory`  
 O diretório no qual deseja armazenar o log de acompanhamento.  
  
 [in] `taskName`  
 Identifica o contexto de acompanhamento. Esse nome é usado para criar o nome de arquivo de log.  
  
 [in] `rootMarkerResponseFile`  
 O nome do caminho de um arquivo de resposta que contém um marcador de raiz. O nome da raiz é usado para agrupar todos os acompanhamentos para um contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) com [SUCCEEDED] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits, se o contexto de acompanhamento foi criado.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## <a name="see-also"></a>Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)



