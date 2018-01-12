---
title: "Caixa de diálogo de opções de teclado do Word do Microsoft Office, configurações de teclado do Microsoft Office, | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords: keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7fc2f6ea9f9f404efae6ca85c8e6a4b0f70be129
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Caixa de diálogo Teclado do Word do Microsoft Office, Configurações de Teclado do Microsoft Office, Opções
  O Microsoft Office Word e o Visual Studio ambos manipulam teclas de atalho. Comandos diferentes no Word e no Visual Studio pode representar a mesma combinação de teclas de atalho. Quando o Word é aberto em um projeto no nível do documento no Visual Studio, apenas um aplicativo em um momento recebe os comandos de teclas de atalho. Por padrão, o Visual Studio receberá todos os comandos de tecla de atalho, mas você pode fazer com que o Word recebê-las quando o documento tem foco selecionando **esquema de teclado dinâmico**.  
  
 Se você usar uma tecla de atalho que não está atribuída a um comando no aplicativo que está tratando as teclas de atalho no momento, a tecla de atalho é passada para o outro aplicativo.  
  
 A opção que você selecionar permanecerá em vigor para projetos do Word até você alterá-lo. A seleção não afeta seus projetos do Microsoft Office Excel; Você deve fazer qualquer alteração para o Excel usando as opções de teclado do Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Esquema de teclado do Visual Studio**  
 O Visual Studio recebe todos os comandos de tecla de atalho, mesmo se o documento do Word tem foco. Por exemplo, se você pressionar a tecla F5 enquanto o documento tem o foco, o Visual Studio inicia a depuração de sua solução.  
  
 **Esquema de teclado dinâmico**  
 O Visual Studio recebe comandos de tecla de atalho apenas quando ele tem o foco. Quando o documento do Word tem foco, o Word recebe todos os comandos de tecla de atalho. Por exemplo, se você pressionar a tecla F5 enquanto o documento do Word tem foco, o Word abrirá o **localizar e substituir** caixa de diálogo com o **ir para** guia selecionada. Se você pressionar F5, enquanto o Visual Studio tem foco, o Visual Studio inicia a depuração de sua solução.  
  
## <a name="see-also"></a>Consulte também  
 [Caixa de diálogo Teclado do Excel do Microsoft Office, Configurações de Teclado do Microsoft Office, Opções](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  