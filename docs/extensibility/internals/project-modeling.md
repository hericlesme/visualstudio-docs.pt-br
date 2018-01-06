---
title: Projeto de modelagem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c3d87a44838ead7663ff4c156985ab1b8e98eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="project-modeling"></a>Projeto de modelagem
A próxima etapa no fornecimento de automação para seu projeto é implementar os objetos do projeto padrão: o <xref:EnvDTE.Projects> e `ProjectItems` coleções; o `Project` e <xref:EnvDTE.ProjectItem> objetos; e os objetos restantes exclusivos para sua implementação. Esses objetos padrão são definidos no arquivo Dteinternal.h. Uma implementação dos objetos padrão é fornecida no exemplo BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que suporte lado a lado com objetos de outros tipos de projeto do projeto.  
  
 Presume que um consumidor de automação para poder chamar <xref:EnvDTE.Solution>("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`) em que n é um número de índice para a obtenção de um projeto específico na solução. Fazer essa chamada de automação faz com que o ambiente chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na hierarquia de projeto apropriado, passando VSITEMID_ROOT como o parâmetro ItemID e VSHPROPID_ExtObject como parâmetro VSHPROPID. `IVsHierarchy::GetProperty`Retorna um `IDispatch` ponteiro para o objeto de automação, fornecendo o núcleo `Project` interface, que você implementou.  
  
 A seguir está a sintaxe de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projetos acomodar aninhamento e usam coleções para criar grupos de itens de projeto. A hierarquia tem esta aparência.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Aninhar significa que um <xref:EnvDTE.ProjectItem> objeto pode ser <xref:EnvDTE.ProjectItems> coleção ao mesmo tempo porque um `ProjectItems` coleção pode conter os objetos aninhados. O exemplo de projeto básico não demonstram esse aninhamento. Implementando o `Project` objeto participar na estrutura de árvore que caracteriza o design do modelo geral de automação.  
  
 A automação de projeto segue o caminho no diagrama a seguir.  
  
 ![Objetos de projeto do Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automação de projeto  
  
 Se você não implemente um `Project` do objeto, o ambiente ainda retornará um genérico `Project` objeto que contém apenas o nome do projeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>