---
title: Caixa de diálogo de opções de teclado do Word do Microsoft Office, configurações de teclado do Microsoft Office, | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572105"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Caixa de diálogo de opções de teclado do Word do Microsoft Office, configurações de teclado do Microsoft Office
  O Microsoft Office Word e o Visual Studio ambos manipulam teclas de atalho. Comandos diferentes no Word e no Visual Studio pode representar a mesma combinação de teclas de atalho. Quando o Word é aberto em um projeto no nível do documento no Visual Studio, apenas um aplicativo em um momento recebe os comandos de teclas de atalho. Por padrão, o Visual Studio receberá todos os comandos de tecla de atalho, mas você pode fazer com que o Word recebê-las quando o documento tem foco selecionando **esquema de teclado dinâmico**.  
  
 Se você usar uma tecla de atalho que não está atribuída a um comando no aplicativo que está tratando as teclas de atalho no momento, a tecla de atalho é passada para o outro aplicativo.  
  
 A opção que você selecionar permanecerá em vigor para projetos do Word até você alterá-lo. A seleção não afeta seus projetos do Microsoft Office Excel; Você deve fazer qualquer alteração para o Excel usando as opções de teclado do Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Esquema de teclado do Visual Studio**  
 O Visual Studio recebe todos os comandos de tecla de atalho, mesmo se o documento do Word tem foco. Por exemplo, se você pressionar a tecla de função **F5** enquanto o documento tem o foco, o Visual Studio inicia a depuração de sua solução.  
  
 **Esquema de teclado dinâmico**  
 O Visual Studio recebe comandos de tecla de atalho apenas quando ele tem o foco. Quando o documento do Word tem foco, o Word recebe todos os comandos de tecla de atalho. Por exemplo, se você pressionar a tecla de função **F5** enquanto o documento do Word tem foco, o Word abrirá o **localizar e substituir** caixa de diálogo com o **ir para** guia selecionada. Se você pressionar **F5** enquanto o Visual Studio tem foco, o Visual Studio inicia a depuração de sua solução.  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo de opções de teclado do Microsoft Office Excel, configurações de teclado do Microsoft Office](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  