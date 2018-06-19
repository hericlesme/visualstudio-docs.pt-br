---
title: Depurando aplicativos de modo misto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0564a1e4a03d0b2d72298f0467e6cd1a91cdab9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480313"
---
# <a name="debugging-mixed-mode-applications"></a>Depurando aplicativos de modo misto
Um aplicativo no modo misto é qualquer aplicativo que combine código nativo (C++) com código gerenciado (como o Visual Basic, Visual C# ou C++ que é executado no Common Language Runtime). A depuração de aplicativos no modo misto é totalmente transparente no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; não é muito diferente da depuração de um aplicativo no modo único. No entanto, há algumas considerações especiais a serem feitas.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>Habilitar o recurso Editar e Continuar do C++ na depuração em modo misto  

Para habilitar editar e continuar para C++, consulte [como habilitar e desabilitar editar e continuar](../debugger/how-to-enable-and-disable-edit-and-continue.md).

> [!NOTE]
> Para usar o recurso Editar e Continuar do C++ no Visual Studio 2013, você precisa reverter para o mecanismo de depuração herdado. Consulte [alternar para modo de compatibilidade gerenciado no Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) no blog Microsoft Application Lifecycle Management.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>Avaliação da propriedade em aplicativos no modo misto  
 Em um aplicativo no modo misto, a avaliação das propriedades pelo depurador é uma operação cara. Consequentemente, as operações de depuração em etapas pode parecer lenta. Para obter mais informações, consulte [revisão](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9). Se o desempenho for baixo na depuração em modo misto, você poderá desativar a avaliação da propriedade nas janelas do depurador.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
#### <a name="to-turn-off-property-evaluation"></a>Para desativar a avaliação da propriedade  
  
1.  No menu **Ferramentas**, escolha **Opções**.  
  
2.  No **opções** caixa de diálogo, abra o **depuração** pasta e selecione o **geral** categoria.  
  
3.  Limpar o **habilitar avaliação de propriedades e outras chamadas de função implícitas** caixa de seleção.  
  
 Como as pilhas de chamadas nativas e as pilhas de chamadas gerenciadas são diferentes, o depurador nem sempre pode fornecer a pilha de chamadas completa para código combinado. Quando o código nativo chamar o código gerenciado, você poderá observar algumas discrepâncias. Para obter mais informações, consulte [código misto e informações ausentes na janela de pilha de chamada](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## <a name="see-also"></a>Consulte também  
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)