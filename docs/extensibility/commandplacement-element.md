---
title: Elemento CommandPlacement | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6a5c8d9220b0cd2c0dddfee283d222f4efb9ab8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="commandplacement-element"></a>Elemento CommandPlacement
Permite que o elemento CommandPlacement botões, grupos e menus devem ser incluídos em mais de um grupo ou menu. Usando o elemento CommandPlacement, você não precisa redefinir completamente esses itens para modificar a aparência de uma interface de usuário.  
  
 Para obter mais informações, consulte [criando grupos reutilizável de botões](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|GUID|Necessário. O guid do conjunto de comando, conforme definido no [símbolos elemento](../extensibility/symbols-element.md).|  
|id|Necessário. A id do menu, o grupo ou o comando será colocado, conforme definido no `Symbols Element`.|  
|priority|Necessário. Determina a posição visual do item em seu elemento pai.|  
|Condição|Opcional. Consulte [atributos condicionais](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Pai|Necessário. O menu ou grupo que hospeda o item será colocado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Especifica os grupos de elementos CommandPlacements e CommandPlacement.|  
  
## <a name="example"></a>Exemplo  
  
```  
<CommandPlacements>  
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"  
    priority="0x0300">  
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>  
  </CommandPlacement>  
</CommandPlacements>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)   
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)