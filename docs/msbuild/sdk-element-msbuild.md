---
title: Elemento Sdk (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 15084b21c80967a5ebd170e175adf09d9623be5b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154087"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)
Faz referência a um SDK do projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Sintaxe  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Atributo obrigatório.<br /><br /> O nome do SDK do projeto.|  
|`Version`|Atributo opcional.<br /><br /> A versão do SDK do projeto|  

### <a name="child-elements"></a>Elementos filho  
 nenhuma.

### <a name="parent-elements"></a>Elementos pai  
 |Elemento|Descrição|  
|-------------|-----------------|  
|[Projeto](../msbuild/project-element-msbuild.md)|Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="see-also"></a>Consulte também  
 [Como fazer referência a um SDK de projeto do MSBuild](../msbuild/how-to-use-project-sdk.md)   
 [Referência de esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
