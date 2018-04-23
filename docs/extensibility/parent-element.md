---
title: Pai do elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 795654925a92f3e9ac0718e070e85c0f4f7f21c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="parent-element"></a>Elementos pai
O pai de um botão ou caixa de combinação só pode ser um grupo. O pai de um menu ou grupo pode ser qualquer outro menu ou grupo. Em um [CommandPlacement elemento](../extensibility/commandplacement-element.md), esse elemento é necessário; em todas as outras instâncias é opcional. Se esse elemento for omitido, o pai do `Group_Undefined:0` será implícita.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. Identificador de comando GUID do GUID/ID.|  
|id|Necessário. Identificador de comando de ID de GUID/ID.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage para o ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Grupos de [elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando de um VSPackage.|  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)