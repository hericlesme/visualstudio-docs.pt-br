---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d55fb2d816931a74827d318e13860b3f97f0fd23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
Obtém a propriedade que é especificada pelo parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwProperty`  
 O valor da propriedade para obter.  
  
 `pvarIndex`  
 Não usado.  
  
 `pvarValue`  
 O valor da propriedade.  
  
 Os valores permitidos para `dwProperty` são descritos na tabela a seguir.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Força o mecanismo de script a divisão em modo de inteiro em vez do modo de ponto flutuante.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|Permite que a função de comparação de cadeia de caracteres do mecanismo de script a ser substituído.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|Informa ao mecanismo de script que outros mecanismos de script não existem para contribuir para o objeto global.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|Força o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script para selecionar um conjunto de recursos de idioma com suporte. O conjunto padrão de recursos de idioma com suporte a [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script é equivalente ao conjunto de recursos de idioma que apareceu na versão 5.7 do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento não é válido.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 O host pode usar a propriedade SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION para informar um mecanismo de script que outros mecanismos de script não existem para contribuir para o objeto global. Por exemplo, o Internet Explorer pode informar o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo que a página está sendo processada contém apenas [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripts. Assim, somente o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo pode adicionar novas propriedades para a janela do objeto global, e não há nenhum mecanismo de Visual Basic Scripting Edition (VBScript) para fazer o mesmo. O mecanismo pode ignorar esse sinalizador ou pode ser usado para otimizar o gerenciamento de novos membros que são adicionadas ao objeto global.  
  
 O host pode usar a propriedade SCRIPTPROP_INVOKEVERSIONING para selecionar o conjunto de recursos de idioma a ser suportado quando o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script é iniciado. Se essa propriedade for definida como 1 (SCRIPTLANGUAGEVERSION_5_7), os recursos de idioma disponíveis são as mesmas que eram exibidos na versão 5.7 do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script. Se ele for definido como 2 (SCRIPTLANGUAGEVERSION_5_8), os recursos de idioma disponíveis são aquelas que apareceu na versão 5.7, além de recursos que foram adicionados na versão 5.8. Por padrão, essa propriedade é definida como 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que é equivalente ao conjunto de recursos de idioma que apareceu na versão 5.7, a menos que o host oferece suporte a um comportamento diferente do padrão. Por exemplo, o Internet Explorer 8 aceita para o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] recursos de idioma com suporte pela versão 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script por padrão quando o modo de documento do Internet Explorer 8 está no modo "Padrões do Internet Explorer 8".  
  
## <a name="see-also"></a>Consulte também  
 [Definindo a compatibilidade do documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informações de versão](../../javascript/reference/javascript-version-information.md)