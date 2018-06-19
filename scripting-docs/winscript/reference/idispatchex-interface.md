---
title: Interface IDispatchEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a100a193f5e3abcb076fb8aaf3d64a0d0c38833
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24730296"
---
# <a name="idispatchex-interface"></a>Interface IDispatchEx
`IDispatchEx`, uma extensão de `IDispatch` dá suporte a recursos de interface, apropriado para linguagens dinâmicas, como as linguagens de script. Esta seção descreve o `IDispatchEx` interface, as diferenças entre `IDispatch` e `IDispatchEx`e a lógica para as extensões. Espera-se que os leitores esteja familiarizados com `IDispatch` e acessem o `IDispatch` documentação.  
  
## <a name="remarks"></a>Comentários  
 `IDispatch`foi desenvolvido essencialmente para Microsoft Visual Basic. A principal limitação de `IDispatch` é que ele supõe que os objetos são estáticos. Em outras palavras, desde que os objetos não serão alterados durante o tempo de execução, informações de tipo podem totalmente descrevê-los em tempo de compilação. Modelos de tempo de execução dinâmicos que se encontram em linguagens de script, como Visual Basic Scripting Edition (VBScript) e [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e modelos de objeto, como HTML dinâmico requer uma interface mais flexível.  
  
 `IDispatchEx`foi desenvolvido para fornecer todos os serviços de `IDispatch` , bem como algumas extensões que são apropriados para idiomas de associação tardia mais dinâmicos, como as linguagens de script. Os recursos adicionais de `IDispatchEx` além daquelas fornecidas pelo `IDispatch` são:  
  
-   Adicionar novos membros a um objeto ("expando") — use `GetDispID` com o `fdexNameEnsure` sinalizador.  
  
-   Excluir membros de um objeto — use `DeleteMemberByName` ou `DeleteMemberByDispID`.  
  
-   As operações de distribuição de maiusculas e minúsculas — use `fdexNameCaseSensitive` ou `fdexNameCaseInsensitive`.  
  
-   Pesquisa de membro com nome implícita — use `fdexNameImplicit`.  
  
-   Enumerar DISPIDs de um objeto — use `GetNextDispID`.  
  
-   Mapa de DISPID ao nome do elemento — use `GetMemberName`.  
  
-   Obter propriedades de membros de objeto — use `GetMemberProperties`.  
  
-   Invocação de método com `this` ponteiro — use `InvokeEx` com DISPATCH_METHOD.  
  
-   Permitir que os navegadores que suportam o conceito de espaços de nome para obter o pai do espaço de nome de um objeto — use `GetNameSpaceParent`.  
  
 Objetos que dão suporte a `IDispatchEx` também podem oferecer suporte `IDispatch` para compatibilidade com versões anteriores. Natureza dinâmica dos objetos que dão suporte `IDispatchEx` tem algumas implicações para o `IDispatch` interface desses objetos. Por exemplo, `IDispatch` faz com que a suposição a seguir:  
  
-   O membro e o parâmetro DISPIDs devem permanecer constantes para o tempo de vida do objeto. Isso permite que um cliente obter DISPIDs uma vez e armazenam em cache para uso posterior.  
  
 Como `IDispatchEx` permite a adição e exclusão de membros, o conjunto de DISPIDs válidos não permanecer constante. No entanto, `IDispatchEx` requer que o mapeamento entre o nome do membro e DISPID permaneça constante. Isso significa que, se um membro é excluído:  
  
-   O DISPID não pode ser reutilizado até que um membro com o mesmo nome é criado.  
  
-   O DISPID deve permanecer válido por `GetNextDispID`.  
  
-   O DISPID deve ser aceito normalmente por qualquer uma da `IDispatch` ou `IDispatchEx` métodos – eles devem reconhecer o membro como excluído e retornar um código de erro apropriado (geralmente DISP_E_MEMBERNOTFOUND ou S_FALSE).  
  
## <a name="examples"></a>Exemplos  
 Isso [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código o Test () de função faz o seguinte:  
  
-   Cria um novo objeto chamando o `Object` construtor e atribui um ponteiro para o novo objeto para o objeto de variável  
  
-   Cria um novo elemento chamado Elem no objeto e atribui a esse elemento um ponteiro para o atendimento ao cliente de função.  
  
-   Chama essa função. Desde que ele está sendo chamado como um método, o `this` ponteiro refere-se ao objeto obj. A função adiciona um novo elemento, barra, para o objeto.  
  
 O código HTML completo é:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 Um controle colocado nessa mesma página da Web foi possível obter um ponteiro de expedição para mecanismos de script do navegador. O controle, em seguida, pode implementar o Test (função):  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 Código do controle, testar, faz a mesma coisa que o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] função `test()`. Observe que essas chamadas de expedição são feitas para a execução [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] engine e alterar o estado do mecanismo de:  
  
-   Obtém o ponteiro de expedição para a função cat usando `GetDispID()`.  
  
-   Obtém o ponteiro de expedição para o objeto função usando `GetDispID()`.  
  
-   Constrói um objeto, chamando a função do objeto com `InvokeEx()` e obtém um ponteiro de expedição para o objeto recém construído.  
  
-   Cria um novo elemento, Elem, usando o objeto `GetDispID()` com o `fdexNameEnsure` sinalizador.  
  
-   Coloca o ponteiro de expedição cat usando o elemento `InvokeEx()`.  
  
-   Chama o ponteiro de expedição de atendimento ao cliente como um método chamando `InvokeEx()` e passar o ponteiro de expedição para o objeto construído como o `this` ponteiro.  
  
-   O método cat cria um novo elemento, barra, atual `this` objeto.  
  
-   Verifica se o novo elemento, barras, foi criado no objeto construído Enumerando os elementos usando `GetNextDispID()`.  
  
 O código para o controle de teste:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>Métodos  
 [Métodos IDispatchEx](../../winscript/reference/idispatchex-methods.md)