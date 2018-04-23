---
title: Elemento ButtonText | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2fca0fbb22bf51353eeaa64f519face53bfb23c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo permite que você especifique o texto que aparece em vários menus. Por padrão, o `ButtonText` elemento aparece em controladores de menu. O `ButtonText` elemento também se tornará o padrão se campos de texto estão em branco. O `ButtonText` elemento não pode ficar em branco, mesmo se os outros campos de texto forem especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<ButtonText>My Command</ButtonText>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento Strings](../extensibility/strings-element.md)|Agrupa elementos de texto, como `ButtonText` e `CommandName`.|  
  
## <a name="text-value"></a>Valor de texto  
 O valor de texto de `ButtonText` elemento fornece o texto que é exibido para os itens de menu, combinações e outros elementos de interface de usuário com texto visível.  
  
## <a name="see-also"></a>Consulte também  
 [Arquivos da tabela de comandos do Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)