---
title: Elemento ButtonText | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b17492b0cc8531ac892bf8ead1c309f403d1da48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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