---
title: Elemento de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d36bcf22d012d4543267d1b57d41567baf3e85b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466281"
---
# <a name="symbols-element"></a>Elemento Symbols
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento Symbols](https://docs.microsoft.com/visualstudio/extensibility/symbols-element).  
  
Define os GUIDs e IDs que são usadas por outros elementos VSCT. Para código não gerenciado, essas informações geralmente vem dos arquivos de cabeçalho que são especificados por [elemento Extern](../extensibility/extern-element.md). O código gerenciado usa os elementos filho do elemento símbolos para definir essas informações.  
  
 Se você criar um arquivo. VSCT de um arquivo CTO já existente, os símbolos serão gerados como filhos do elemento de símbolos. Para obter mais informações, consulte [como: criar um. Arquivo VSCT de um existente. Arquivo CTO](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 O elemento de símbolos não deve ser confundido com o [definem o elemento](../extensibility/define-element.md), que define os pares nome-valor para uso pelo pré-processador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|Nenhum||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|GuidSymbol|Define um símbolo GUID. GuidSymbol possui dois atributos obrigatórios: nome e valor. O nome é o nome do símbolo e o valor é o valor do GUID como uma cadeia de caracteres.<br /><br /> Por exemplo:\<GuidSymbol nome = "guidVsPackage1Pkg" value = "{c5f54698-101a-4846-84d3-dc748f9cd848}" / >|  
|IDSymbol|Define um símbolo. IDSymbol possui dois atributos obrigatórios: nome e valor. O nome é o nome do símbolo e o valor é o valor do símbolo, como uma cadeia de caracteres.<br /><br /> Por exemplo:\<IDSymbol nome = "MyMenuGroup" value = "0x1020" / >|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|O elemento raiz do arquivo. VSCT.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

