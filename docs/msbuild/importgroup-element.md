---
title: Elemento ImportGroup | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df9aebf8e604ad16b99ac458bdd9d143bd461ff7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="importgroup-element"></a>Elemento ImportGroup
Contém uma coleção de elementos `Import` que são agrupados em uma condição opcional. Para obter mais informações, consulte [Importar Elemento (MSBuild)](../msbuild/import-element-msbuild.md).  

 \<Project>  
 \<ImportGroup>  

## <a name="syntax"></a>Sintaxe  

```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> A condição a ser avaliada. Para obter mais informações, consulte [Condições](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|Importa o conteúdo de um arquivo de projeto para outro arquivo de projeto.|  

### <a name="parent-elements"></a>Elementos pai  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Comentários  

## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra o elemento `ImportGroup`.  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  

## <a name="see-also"></a>Consulte também  
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Itens](../msbuild/msbuild-items.md)
