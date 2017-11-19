---
title: Elemento IDSymbol | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 734d05dd013be9a3d6c4a173a5c7abc7a01ef2d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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