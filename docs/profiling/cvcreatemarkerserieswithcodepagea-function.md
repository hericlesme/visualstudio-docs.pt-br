---
title: "Função CvCreateMarkerSeriesWithCodePageA | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords: CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6e435e702b25bd3abaacd4a789d635901617a611
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>Função CvCreateMarkerSeriesWithCodePageA
Cria a série de marcador para determinado provedor e uma página de código especificada. Essa função pode ser usada para especificar a página de código explicitamente para o texto gravado por funções ANSI da API do marcador. Configurar a página de código pode ser útil caso o rastreamento seja capturado e então analisado em diferentes computadores com diferentes localidades/idiomas. Por padrão, a página de código retornada pela função GetACP() é usada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Objeto de provedor inicializado anteriormente por CvInitProvider. Não pode ser NULL.  
  
 `pSeriesName`  
 Nome da série de marcador. Não pode ser NULL, mas uma cadeia de caracteres vazia é permitida.  
  
 `nTextCodePage`  
 Página de código válida.  
  
 `ppMarkerSeries`  
 Endereço de uma variável de saída que armazenará o contexto de série de marcador. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK quando a série de marcador é criada com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)