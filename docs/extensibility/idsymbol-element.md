---
title: Elemento IDSymbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71979bd4f859257555c9d72ac5521a5ae21b9ed4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
O `IDSymbol` elemento contém a ID do par GUID:ID que representa um menu, o grupo ou o comando. O GUID é proveniente do pai `GuidSymbol` elemento. O `IDSymbol` elemento tem um `name` atributo que forneça um nome amigável para a ID, que está contida no `value` atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Necessário. Nome do símbolo de ID.|  
|Valor |Necessário. Valor numérico da ID do símbolo ID.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contém o GUID do par GUID:ID que representa um menu, o grupo ou o comando. Agrupa elementos `IDSymbol`.|  
  
## <a name="remarks"></a>Comentários  
 Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter uma única `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles têm diferentes pais.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)