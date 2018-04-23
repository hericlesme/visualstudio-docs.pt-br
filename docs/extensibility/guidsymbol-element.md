---
title: Elemento GuidSymbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d5e3a3f4d33e166d344669dbeb4bc1a877335f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
O `GuidSymbol` elemento contém o GUID do par GUID:ID que representa um menu, o grupo ou o comando. A ID vêm de um `IDSymbol` elemento o `GuidSymbol` elemento. O `GuidSymbol` elemento tem um `name` atributo que forneça um nome amigável para o GUID, que está contido no `value` atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Necessário. Nome do símbolo GUID.|  
|Valor |Necessário. GUID do símbolo GUID.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contém a ID do par GUID:ID que representa um menu, o grupo ou o comando.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Symbols](../extensibility/symbols-element.md)|Grupos de `GuidSymbol` elementos em um arquivo. VSCT.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, um arquivo. VSCT contém três `GuidSymbol` elementos no seu `Symbols` seção, para o pacote propriamente dito, um para o conjunto de comandos (a coleção de comandos que disponibiliza o pacote de menus e grupos) e para os bitmaps que fornecem ícones de botões e outros componentes visuais. Cada `IDSymbol` elemento em um determinado `GuidSymbol` elemento deve ter uma única `value`. No entanto, `IDSymbol` elementos que têm valores idênticos podem existir em um pacote, desde que eles têm diferentes pais.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)