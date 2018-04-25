---
title: Como escapar caracteres especiais no MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e325ab2d5a5a54a9aaf8378753ccbe8f3a72a5a8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>Como escapar caracteres especiais no MSBuild
Determinados caracteres têm significado especial em arquivos de projeto do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. O ponto e vírgula (;) e o asterisco (*) são exemplos de caracteres. Para obter uma lista completa desses caracteres especiais, consulte [Caracteres especiais do MSBuild](../msbuild/msbuild-special-characters.md).  
  
 Para usar esses caracteres especiais como literais em um arquivo de projeto, eles devem ser especificados usando a sintaxe %*xx*, em que *xx* representa o valor hexadecimal ASCII do caractere.  
  
## <a name="msbuild-special-characters"></a>Caracteres especiais no MSBuild  
 Um exemplo de quando os caracteres especiais são usados é no atributo `Include` de listas de itens. Por exemplo, a lista de itens a seguir declara dois itens: `MyFile.cs` e `MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 Se você quiser declarar um item que contém um ponto e vírgula no nome, você deverá usar a sintaxe %*xx* para escapar o ponto e vírgula e evitar que o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] declare dois itens separados. Por exemplo, o item a seguir escapa o ponto e vírgula e declara um item denominado `MyFile.cs;MyClass.cs`.  
  
```xml  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>Para usar um caractere especial do MSBuild como um caractere literal  
  
-   Use a notação %*xx* no lugar do caractere especial, em que *xx* representa o valor hexadecimal do caractere ASCII. Por exemplo, para usar um asterisco (*) como um caractere literal, use o valor `%2A`.  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)   
 [MSBuild](../msbuild/msbuild.md) [Itens](../msbuild/msbuild-items.md)