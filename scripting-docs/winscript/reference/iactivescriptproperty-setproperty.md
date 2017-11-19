---
title: IActiveScriptProperty::SetProperty | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc9b5f4c0d02789988bb41f46417651414beed7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
Define a propriedade que é especificada pelo parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetProperty(  
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
 O valor da propriedade a ser definido.  
  
 `pvarIndex`  
 Não usado.  
  
 `pvarValue`  
 O valor da propriedade.  
  
 Os valores permitidos para `dwProperty` são descritos na tabela a seguir.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|Força o mecanismo de script a divisão em modo de inteiro em vez do modo de ponto flutuante. O valor padrão é `False`.|  
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
 Para habilitar ou desabilitar a divisão de inteiro, invocar `SetProperty` e converter um `Boolean` para um `Object`. Por padrão, o valor da propriedade é `False`. Se você defini-lo `True`, operações de divisão retornará apenas números inteiros.  
  
 Para habilitar ou desabilitar a comparação de cadeia de caracteres personalizada, invocar `SetProperty` e passar uma `Object` valor. O objeto que você transmitir deve implementar a interface [IActiveScriptStringCompare Interface](../../winscript/reference/iactivescriptstringcompare-interface.md). O [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) método o [IActiveScriptStringCompare Interface](../../winscript/reference/iactivescriptstringcompare-interface.md) interface é chamada sempre que uma função de comparação de cadeia de caracteres é executada.  
  
 Para selecionar o conjunto de recursos de idioma com suporte quando o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script é inicializado, invoque `SetProperty` e passar um valor que corresponde ao recurso de idioma definido para ser habilitado para SCRIPTPROP_INVOKEVERSIONING. Se essa propriedade for definida como 1 (SCRIPTLANGUAGEVERSION_5_7), os recursos de idioma disponíveis são as mesmas que eram exibidos na versão 5.7 do [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script. Se ele for definido como 2 (SCRIPTLANGUAGEVERSION_5_8), os recursos de idioma disponíveis são aquelas que apareceu na versão 5.7, além de novos recursos que foram adicionados na versão 5.8. Por padrão, essa propriedade é definida como 0 (SCRIPTLANGUAGEVERSION_DEFAULT), que é equivalente ao conjunto de recursos de idioma que apareceu na versão 5.7, a menos que o host oferece suporte a um comportamento diferente do padrão. Por exemplo, o Internet Explorer 8 aceita para o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] recursos de linguagem que são suportados pela versão 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script por padrão quando o modo de documento padrão do Internet Explorer 8 está no modo "Padrões do Internet Explorer 8". Alternar o modo de documento do Internet Explorer 8 para os padrões do Internet Explorer 7 ou o modo Quirks redefine o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script para dar suporte a apenas o conjunto de recursos de idioma que existiam na versão 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script.  
  
> [!NOTE]
>  SCRIPTPROP_INVOKEVERSIONING deve ser definido somente quando o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo de script está sendo inicializado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como forçar o mecanismo de script para usar a divisão de inteiro e permitir a sobrecarga da função de comparação.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>Consulte também  
 [Definindo a compatibilidade do documento](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [Informações de versão](../../javascript/reference/javascript-version-information.md)