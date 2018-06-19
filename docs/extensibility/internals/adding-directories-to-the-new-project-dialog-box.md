---
title: Adicionando pastas a caixa de diálogo Novo projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4ad992785fdf8ab5ffdd3faa7043e2a0ee5411b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128063"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Adicionando pastas a caixa de diálogo Novo projeto
Quando você criar novos tipos de projeto, você também pode registrar um novo diretório no **novo projeto** caixa de diálogo para exibi-los para uso como modelos. O exemplo de código a seguir explica como registrar um novo diretório, também conhecido como um nó. No exemplo, modelos expostos pelo VSPackage CLSID_Package são registrados. Como resultado, o lado esquerdo do **novo projeto** caixa de diálogo oferece o nó adicional, com um nome determinado pelo recurso Folder_Label_ResID. Esse recurso é carregado do DLL de satélite VSPackage.  
  
 O **pasta** valor representa um GUID de uma pasta sob a qual o nó de Folder_Label_ResID é exibido. No exemplo, o GUID que representa o **outros projetos** pasta o **tipos de projeto** painel do **novo projeto** caixa de diálogo. Se o **outros projetos** valor está ausente, o rótulo é posicionado no nível superior.  
  
 O valor de TemplatesDir Especifica o caminho completo do diretório que contém os modelos de projeto. Esses arquivos podem ser arquivos. vsz ou arquivos de modelo comum a ser clonado.  
  
 Se você especificar TemplatesLocalizedSubDir, ele deve ser a identificação de recurso de uma cadeia de caracteres que nomeia o subdiretório de TemplatesDir que contém modelos localizados. Porque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega o recurso de cadeia de caracteres de uma DLL satélite se você tiver um, cada DLL satélite pode conter um nome de subdiretório diferentes. O valor de SortPriority Especifica uma prioridade de classificação.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Registro de modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Adicionar itens para o adicionar novo Item caixas de diálogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Adicionar diretórios à caixa de diálogo Adicionar Novo Item](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)