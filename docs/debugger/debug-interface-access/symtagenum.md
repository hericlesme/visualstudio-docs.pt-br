---
title: SymTagEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36dc9b3d9fc15b06c92db27b38d94805c1ce8a25
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480856"
---
# <a name="symtagenum"></a>SymTagEnum
Especifica o tipo de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## <a name="elements"></a>Elementos  
 `SymTagNull`  
 Indica que o símbolo não tem um tipo.  
  
 `SymTagExe`  
 Indica que o símbolo é um arquivo de .exe. Há apenas um `SymTagExe` símbolo por armazenamento de símbolo. Ele serve como o escopo global e não tem um pai léxico.  
  
 `SymTagCompiland`  
 Indica o símbolo compiland para cada componente de compiland do repositório de símbolos. Para aplicativos nativos, `SymTagCompiland` símbolos corresponde aos arquivos de objeto vinculados na imagem. Para alguns tipos de imagens do Microsoft Intermediate Language (MSIL), há um compiland por classe.  
  
 `SymTagCompilandDetails`  
 Indica que o símbolo contém atributos estendidos do compiland. Recuperar essas propriedades pode exigir carregar símbolos compiland.  
  
 `SymTagCompilandEnv`  
 Indica que o símbolo é uma cadeia de caracteres de ambiente definida para o compiland.  
  
 `SymTagFunction`  
 Indica que o símbolo é uma função.  
  
 `SymTagBlock`  
 Indica que o símbolo é um bloco aninhado.  
  
 `SymTagData`  
 Indica que o símbolo de dados.  
  
 `SymTagAnnotation`  
 Indica que o símbolo de uma anotação de código. Os filhos desse símbolo são cadeias de caracteres de constante de dados (`SymTagData`, `LocIsConstant`, `DataIsConstant`). A maioria dos clientes ignorar este símbolo.  
  
 `SymTagLabel`  
 Indica que o símbolo é um rótulo.  
  
 `SymTagPublicSymbol`  
 Indica que o símbolo é um símbolo público. Para aplicativos nativos, este símbolo é o símbolo externo COFF ao vincular a imagem.  
  
 `SymTagUDT`  
 Indica que o símbolo for um tipo definido pelo usuário (estrutura, classe ou união).  
  
 `SymTagEnum`  
 Indica que o símbolo é uma enumeração.  
  
 `SymTagFunctionType`  
 Indica que o símbolo é um tipo de assinatura de função.  
  
 `SymTagPointerType`  
 Indica que o símbolo é um tipo de ponteiro.  
  
 `SymTagArrayType`  
 Indica que o símbolo é um tipo de matriz.  
  
 `SymTagBaseType`  
 Indica que o símbolo é um tipo base.  
  
 `SymTagTypedef`  
 Indica que o símbolo é um `typedef`, ou seja, um alias de outro tipo.  
  
 `SymTagBaseClass`  
 Indica que o símbolo é uma classe base de um tipo definido pelo usuário.  
  
 `SymTagFriend`  
 Indica que o símbolo é um amigo de um tipo definido pelo usuário.  
  
 `SymTagFunctionArgType`  
 Indica que o símbolo é um argumento de função.  
  
 `SymTagFuncDebugStart`  
 Indica que o símbolo é o local final do código de prólogo da função.  
  
 `SymTagFuncDebugEnd`  
 Indica que o símbolo é o local de início do código de epílogo da função.  
  
 `SymTagUsingNamespace`  
 Indica se o símbolo é um nome de namespace, ativo no escopo atual.  
  
 `SymTagVTableShape`  
 Indica que o símbolo é uma descrição da tabela virtual.  
  
 `SymTagVTable`  
 Indica que o símbolo é um ponteiro de tabela virtual.  
  
 `SymTagCustom`  
 Indica que o símbolo é um símbolo personalizado e não é interpretado por DIA.  
  
 `SymTagThunk`  
 Indica que o símbolo é uma conversão usada para compartilhar dados entre 16 e 32 bits.  
  
 `SymTagCustomType`  
 Indica que o símbolo é um símbolo de compilador personalizado.  
  
 `SymTagManagedType`  
 Indica que o símbolo está nos metadados.  
  
 `SymTagDimension`  
 Indica que o símbolo é uma matriz multidimensional FORTRAN.  
  
 `SymTagCallSite`  
 Indica que o símbolo representa o site de chamada.  
  
 `SymTagInlineSite`  
 Indica que o símbolo representa o site embutido.  
  
 `SymTagBaseInterface`  
 Indica que o símbolo é uma interface base.  
  
 `SymTagVectorType`  
 Indica que o símbolo é um tipo de vetor.  
  
 `SymTagMatrixType`  
 Indica que o símbolo é um tipo de matriz.  
  
 `SymTagHLSLType`  
 Indica que o símbolo é um tipo de linguagem de sombreador de nível alto.  
  
## <a name="remarks"></a>Comentários  
 Todos os símbolos em um arquivo de depuração tem uma marca de identifica que especifica o tipo do símbolo.  
  
 Os valores nesta enumeração são retornados por uma chamada para o [: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) método.  
  
 Os valores nesta enumeração são passados para os seguintes métodos para limitar o escopo da pesquisa como um tipo de símbolo específico:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: cvconst.h  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [: Findsymbolbyaddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [: Findsymbolbyrva](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [: Findsymbolbyrvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [: Findsymbolbytoken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [: Findsymbolbyva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [: Findsymbolbyvaex](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [: Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)