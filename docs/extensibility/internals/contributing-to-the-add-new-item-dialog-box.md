---
title: Que contribuem para a caixa de diálogo Novo Item adicionar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 923d95256a3ab0e63bdcf35c7ae38d70a117fa02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Que contribuem para a adicionar a caixa de diálogo Novo Item
Um subtipo de projeto pode fornecer um novo diretório completo de itens para o **Adicionar Novo Item** caixa de diálogo Registrar **Adicionar Item** modelos sob o `Projects` subchave do registro.  
  
## <a name="registering-add-new-item-templates"></a>Registrando Adicionar Novo Item modelos  
 Esta seção está localizada em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** no registro. As entradas de registro abaixo supõem um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregados por um subtipo de projeto hipotético. As entradas para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto estão listados abaixo.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 O `AddItemTemplates\TemplateDirs` subchave contém entradas do registro com o caminho para o diretório onde itens disponibilizados no **Adicionar Novo Item** caixa de diálogo são colocados.  
  
 O ambiente carregará automaticamente todos os a `AddItemTemplates` dados sob o `Projects` subchave do registro. Isso pode incluir os dados para implementações de base do projeto, bem como os dados para tipos de subtipo de projeto específico. Cada subtipo de projeto é identificado por um tipo de projeto `GUID`. O subtipo de projeto pode especificar que uma alternativa conjunto de `Add Item` modelos devem ser usados para uma instância de projeto de uma determinada, dando suporte a `VSHPROPID_ AddItemTemplatesGuid` enumeração de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementação para retornar o GUID valor do subtipo do projeto. Se `VSHPROPID_AddItemTemplatesGuid` propriedade não for especificada, o projeto base GUID é usado.  
  
 Você pode filtrar itens o **Adicionar Novo Item** caixa de diálogo Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interface no objeto do agregador de subtipo de projeto. Por exemplo, um subtipo de projeto que implementa um projeto de banco de dados agregando um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projeto, pode filtrar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] itens específicos do **Adicionar Novo Item** caixa de diálogo com a implementação de filtragem e em Ativar, poderá adicionar itens específicos do projeto de banco de dados, dando suporte `VSHPROPID_ AddItemTemplatesGuid` em <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Para obter mais informações sobre filtragem e adição de itens para o **Adicionar Novo Item** caixa de diálogo, consulte [a adição de itens para as caixas de diálogo Adicionar Novo Item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs para objetos normalmente usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)