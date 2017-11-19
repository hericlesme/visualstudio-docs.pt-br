---
title: Estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e231484b48bf2741281644c746b448fd6f657b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>Estrutura PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Representa informações opcionais sobre objetos do heap.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Tipo|Descrição|  
|------------|----------|-----------------|  
|Tipo de informação|[Enumeração PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|O tipo das informações opcionais.|  
|protótipo|[Tipo PROFILER_HEAP_OBJECT_ID](../../winscript/reference/profiler-heap-object-id-type.md)|A ID do objeto de protótipo do objeto heap.|  
|nomedafunção|LPCWSTR|Nome da função do objeto heap.|  
|elementAttributesSize|UINT|O tamanho do heap do elemento de atributos de objeto.|  
|elementTextChildrenSize|UINT|O tamanho do heap do texto de filhos do objeto.|  
|Lista_de_escopo|[Estrutura PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Lista de escopo do objeto heap.|  
|internalProperty|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|A pilha propriedade do objeto interno.|  
|namePropertyList|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Uma lista de propriedades de nome do objeto do heap.|  
|indexPropertyList|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Uma lista de propriedades do índice do objeto heap.|  
|relationshipList|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Uma lista de relações do objeto heap.|  
|lista de eventos|[Estrutura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Uma lista de eventos do objeto do heap.|