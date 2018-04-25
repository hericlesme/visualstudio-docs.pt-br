---
title: Caracteres especiais do MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5c1a2f67204fd6df7c8eb12ce5f13e8d1f4ec29d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="msbuild-special-characters"></a>Caracteres especiais no MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] reserva alguns caracteres para uso especial em contextos específicos. Você precisa apenas tais caracteres de escape se desejar usá-los literalmente no contexto no qual eles estão reservados. Por exemplo, um asterisco tem um significado especial somente nos atributos `Include` e `Exclude` de uma definição de item e, em chamadas para `CreateItem`. Se você quiser que um asterisco seja exibido como um asterisco em um desses contextos, você deve usar um caractere de escape. Nos outros contextos, basta digitar o asterisco onde você deseja que ele apareça.  
  
 Para escapar um caractere especial, use a sintaxe %*xx*, onde *xx* representa o valor hexadecimal de ASCII do caractere. Para obter mais informações, confira [Como: usar caracteres especiais no MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md).  
  
## <a name="special-characters"></a>Caracteres especiais  
 A tabela a seguir lista os caracteres especiais do [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]:  
  
|**Caractere**|**ASCII**|**Uso reservado**|  
|-------------------|---------------|------------------------|  
|%|%25|Metadados de referência|  
|$|%24|Propriedades de referência|  
|@|%40|Listas de Itens de Referência|  
|'|%27|Condições e outras expressões|  
|;|%3B|Separador de lista|  
|?|%3F|Caractere curinga para nomes de arquivos em atributos `Include` e `Exclude`|  
|*|%2A|Caractere curinga para uso em nomes de arquivos em atributos `Include` e `Exclude`|  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)   
 [Itens](../msbuild/msbuild-items.md)