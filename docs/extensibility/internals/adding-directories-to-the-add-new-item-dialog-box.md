---
title: Adicionando pastas para a caixa de diálogo Novo Item adicionar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127742"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Adicionando pastas para a adicionar a caixa de diálogo Novo Item
O exemplo de código a seguir demonstra como registrar um novo conjunto de diretórios para o **Adicionar Novo Item** caixa de diálogo. Diretórios para o **Adicionar Novo Item** caixa de diálogo são diferentes para cada projeto. Portanto, os diretórios são registrados na subchave projetos, encontrada no \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>O Script de registro  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 O valor de Template_Path Especifica o caminho completo do diretório que contém os modelos de projeto. Esses modelos podem ser arquivos. vsz ou arquivos de modelo de um modelo a ser clonado.  
  
 O valor de SortPriority Especifica uma prioridade de classificação.  
  
## <a name="adding-items-to-an-existing-project"></a>Adicionando itens a um projeto existente  
 Você também pode adicionar itens a um projeto existente. Por exemplo, para um [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projeto, você pode adicionar itens para o \<raiz > pasta \Program Files\Microsoft de \VC#\CSharpProjectItems\LocalProjectItems do Visual Studio. Nesse caso o `%GUID_Project%` é o GUID de um projeto c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Você também pode estender um projeto existente, um subtipo de projeto de programação. Com um subtipo de projeto, você pode estender um projeto sem gravar um novo tipo de projeto. Para obter mais informações sobre os subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionar itens para o adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionar diretórios à caixa de diálogo Novo Projeto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)