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
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c865fd1d01f7bf0137c68010bcb850a7a8450680
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="managing-application-resources-net"></a>Gerenciando recursos de aplicativo (.NET)

Arquivos de recurso são arquivos que fazem parte de um aplicativo, mas não são compilados, por exemplo, arquivos de ícone ou arquivos de áudio. Como esses arquivos não fazem parte do processo de compilação, você pode alterá-los sem precisar recompilar os binários. Se estiver planejando localizar seu aplicativo, você deverá usar arquivos de recurso para todas as cadeias de caracteres e outros recursos que precisam ser alterados ao localizar o aplicativo.

Para obter mais informações sobre recursos em aplicativos de área de trabalho do .NET, consulte [Recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Trabalhando com recursos

Em um projeto de código gerenciado, abra a janela de propriedades do projeto. Você pode abrir a janela Propriedades das seguintes maneiras:

- clicando com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecionando **Propriedades**
- digitando “propriedades do projeto” na janela **Início Rápido**
- escolhendo **Alt**+**Enter** na janela **Gerenciador de Soluções**

Selecione a guia **Recursos**. Você poderá adicionar um arquivo .resx se o projeto ainda não contiver um, adicionar e excluir diferentes tipos de recursos e modificar os recursos existentes.

## <a name="resources-in-other-project-types"></a>Recursos em outros tipos de projeto

Recursos são gerenciados de forma diferente em projetos do .NET que em outros tipos de projeto. Para obter mais informações sobre os recursos em:

- Aplicativos UWP (Plataforma Universal do Windows), consulte [Recursos do aplicativo e o Sistema de Gerenciamento de Recursos](/windows/uwp/app-resources/)
- Aplicativos do Windows 8.x, consulte [Definindo recursos de aplicativo (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx)
- Para projetos C++, consulte [Trabalhando com arquivos de recurso](/cpp/windows/working-with-resource-files) e [Como criar um recurso](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Consulte também

[Recursos em aplicativos da área de trabalho (.NET Framework)](/dotnet/framework/resources/index)