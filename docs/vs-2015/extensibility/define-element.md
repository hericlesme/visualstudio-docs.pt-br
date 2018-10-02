---
title: Definir o elemento | Microsoft Docs
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
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76e44ccc221b0f11f30ed63de63f82634f726b79
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464739"
---
# <a name="define-element"></a>Elemento Define
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [definem o elemento](https://docs.microsoft.com/visualstudio/extensibility/define-element).  
  
Define um par de nome e o valor do símbolo. Este símbolo pode ser avaliado por atributos condicionais. Para obter mais informações, consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md). Consulte também o [símbolos elemento](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|Necessário. O nome do símbolo:<br /><br /> nome = "Modo"|  
|Valor |Necessário. O valor do símbolo:<br /><br /> valor = "Padrão"|  
|Condição|Opcional. Para obter mais informações, consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos os elementos que representam os comandos que fornece um VSPackage para o ambiente de desenvolvimento integrado (IDE). Por exemplo, itens de menu, menus, barras de ferramentas e caixas de combinação.|  
  
## <a name="example"></a>Exemplo  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

