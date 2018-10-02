---
title: Elemento pai | Microsoft Docs
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
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b16aa3e3d6542130b449196de92e795e464ab0e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466127"
---
# <a name="parent-element"></a>Elementos pai
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [elemento pai](https://docs.microsoft.com/visualstudio/extensibility/parent-element).  
  
O pai de um botão ou caixa de combinação só pode ser um grupo. O pai de um menu ou grupo pode ser qualquer menu ou grupo. Em um [elemento CommandPlacement](../extensibility/commandplacement-element.md), esse elemento é necessário; em todas as outras instâncias é opcional. Se esse elemento for omitido, o pai do `Group_Undefined:0` será assumida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. Identificador de comando do GUID/ID de GUID.|  
|id|Necessário. Identificador de comando de ID de/ID de GUID.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage para o ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Grupos [elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento Menus](../extensibility/menus-element.md)|Define todos os menus que implementa um VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contém entradas que definem os grupos de comando de um VSPackage.|  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

