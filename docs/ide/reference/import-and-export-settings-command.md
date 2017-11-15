---
title: Comando Import and Export Settings | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61924f7d9430661114f1fecc36d585e2d223604b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="import-and-export-settings-command"></a>Comando Importar e Exportar Configurações
Importa, exporta ou redefine configurações [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Opções  
 /export:`filename`  
 Opcional. Exporta as configurações atuais para o arquivo especificado.  
  
 /import:`filename`  
 Opcional. Importa as configurações no arquivo especificado.  
  
 /reset  
 Opcional. Redefine as configurações atuais.  
  
## <a name="remarks"></a>Comentários  
 Executar esse comando sem nenhuma opção abre o assistente **Importar e Exportar Configurações**. Para obter mais informações, consulte [Como: Compartilhar configurações entre computadores ou versões de Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Exemplo  
 O comando a seguir exporta as configurações atuais para o arquivo `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)