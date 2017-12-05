---
title: Gerenciando recursos de aplicativo (.NET) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b599a919911fcc5d2833cfe69b75f7b32cced858
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="managing-application-resources-net"></a>Gerenciando recursos de aplicativo (.NET)
Arquivos de recurso são arquivos que fazem parte de um aplicativo, mas não são compilados, por exemplo, arquivos de ícone ou arquivos de áudio. Como esses arquivos não fazem parte do processo de compilação, você pode alterá-los sem precisar recompilar os binários. Se estiver planejando localizar seu aplicativo, você deverá usar arquivos de recurso para todas as cadeias de caracteres e outros recursos que precisam ser alterados ao localizar o aplicativo.  
  
Para obter mais informações sobre recursos em aplicativos de área de trabalho do .NET, consulte [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index). Para obter mais informações sobre recursos em aplicativos de área de trabalho do C++, consulte [Working with Resource Files](/cpp/windows/working-with-resource-files) (Trabalhando com arquivos de recursos).  
  
Os aplicativos UWP usam um modelo de recurso diferente dos aplicativos da área de trabalho. Para obter informações sobre os recursos nos aplicativos do Windows 8.x, consulte [Definindo recursos de aplicativo (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx).  
  
## <a name="working-with-resources"></a>Trabalho com recursos  
Em um projeto de código gerenciado, abra a janela de propriedades do projeto. Você pode abrir a janela Propriedades das seguintes maneiras:

- clicando com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecionando **Propriedades**
- digitando **propriedades do projeto** na janela **Início Rápido**
- escolhendo **Alt + Enter** na janela **Gerenciador de Soluções**

Selecione a guia **Recursos**. Você poderá adicionar um arquivo .resx se o projeto ainda não contiver um, adicionar e excluir diferentes tipos de recursos e modificar os recursos existentes.  
  
Para saber como trabalhar com recursos em projetos C++, consulte [Como criar um recurso](/cpp/windows/how-to-create-a-resource).