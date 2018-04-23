---
title: Verificando subtipos de um projeto em tempo de execução | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8898da6850c01c1a248b57b0fbc5f46be2a8ff4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Verificando subtipos de um projeto em tempo de execução
Um VSPackage que depende de um subtipo de projeto personalizado deve incluir a lógica para procurar subtipo para que ele pode falhar, normalmente o subtipo não está presente. O procedimento a seguir mostra como verificar a presença de um subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar a presença de um subtipo de  
  
1.  Obter a hierarquia de projeto dos objetos de projeto e solução como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto adicionando o seguinte código ao seu VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Converter a hierarquia para o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obter a lista de GUIDs de tipo de projeto invocando o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Verifique a lista para o GUID do subtipo especificado.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Subtipos de projeto](../extensibility/internals/project-subtypes.md)   
 [Design de subtipos de projeto](../extensibility/internals/project-subtypes-design.md)   
 [Propriedades e métodos estendidos por subtipos do projeto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)