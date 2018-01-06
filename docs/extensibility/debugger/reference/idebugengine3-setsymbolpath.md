---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetSymbolPath
helpviewer_keywords: IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8cc60a266a238ee8d3635637b907ce88933b29a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Define o caminho ou caminhos que são pesquisados para símbolos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Cadeia de caracteres que contém o caminho de pesquisa de símbolo ou caminhos. Consulte "Comentários" para obter detalhes. Não pode ser nulo.|  
|`szSymbolCachePath`|[in] Cadeia de caracteres que contém o caminho local onde símbolos podem ser armazenados em cache. Não pode ser nulo.|  
|`Flags`|[in] Não utilizado; sempre definido como 0.|  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres `szSymbolSearchPath` é uma lista de um ou mais caminhos, separados por ponto e vírgula, para procurar símbolos. Esses caminhos podem ser um caminho local, um caminho UNC estilo ou uma URL. Esses caminhos também podem ser uma mistura de tipos diferentes. Se o caminho UNC (por exemplo, \\\Symserver\Symbols), em seguida, o mecanismo de depuração deve determinar se o caminho é um servidor de símbolos e deve ser capaz de carregar os símbolos do servidor, armazenamento em cache no caminho especificado por `szSymbolCachePath`.  
  
 O caminho do símbolo também pode conter um ou mais locais de cache. Os caches são listados em ordem de prioridade, com o cache de prioridade mais alto primeiro e separados por * símbolos. Por exemplo:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 O [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) método executa a carga real dos símbolos.  
  
## <a name="see-also"></a>Consulte também  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)