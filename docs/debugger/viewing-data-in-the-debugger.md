---
title: Criar exibições personalizadas de dados no depurador | Microsoft Docs
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ccf8b24618aeb2cb4b8774786bf96b2184f5da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31482172"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Criar exibições personalizadas de dados no depurador do Visual Studio
O depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece diversas ferramentas para inspecionar e alterar o estado do seu programa. A maioria dessas ferramentas funciona somente no modo de interrupção.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Criar exibições personalizadas de dados em variáveis e DataTips
 Muitas do [janelas do depurador](../debugger/debugger-windows.md), como o **Autos** e **inspecionar** windows, permitem que você inspecione variáveis enquanto está depurando. Você pode personalizar a exibição de tipos nativos e objetos gerenciados em janelas de variáveis do depurador e em [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Isso pode ser útil para exibir os tipos que você criar em seus próprios aplicativos. Para obter mais informações, consulte [criar exibições personalizadas de objetos nativos](../debugger/create-custom-views-of-native-objects.md) e [criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Criar visualizadores personalizados  
 Visualizadores permitem exibir o conteúdo de um objeto ou variável de forma significativa. O depurador do Visual Studio, um visualizador refere-se do Windows diferente que pode ser aberto usando o ícone de lupa ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ícone visualizador"). Por exemplo, você pode usar o visualizador HTML para exibir uma cadeia de caracteres HTML da maneira que ela seria interpretada e exibida em um navegador. Você pode acessar visualizadores de DataTips, a **inspecionar** janela, o **Autos** janela, o **locais** janela, ou o **QuickWatch** caixa de diálogo caixa. Para obter mais informações, consulte [criar visualizadores personalizados](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Janela Comando](../ide/reference/command-window.md)   
 [Segurança do depurador](../debugger/debugger-security.md)