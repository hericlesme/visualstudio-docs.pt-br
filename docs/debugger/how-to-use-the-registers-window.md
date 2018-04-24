---
title: Exibir os valores do registro no depurador do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7630ab56ef738febcf80058916272958e267a386
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Exibir valores de registrar e usar a janela registra no depurador do Visual Studio
A janela de registradores só estará disponível se a depuração de nível de endereço está habilitada no **opções** caixa de diálogo, **depuração** nó **geral** categoria.  
  
 O **registra** janela exibe conteúdo do registro. Se você mantiver o **registra** janela aberta percorrer seu programa, você pode ver registrar valores alterados durante a execução do seu código. Os valores que foram alterados recentemente são exibidos em vermelho. Você pode editar valores do registro. Para obter mais informações, consulte [como: editar um valor de registro](../debugger/how-to-edit-a-register-value.md).  
  
 Para reduzir a desordem, o **registra** janela organiza registros em grupos, que variam de acordo com a plataforma e o processador de tipo. Você pode exibir ou ocultar grupos como desejar. Para obter mais informações, consulte [como: exibir e ocultar grupos registrar](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Para obter uma introdução de alto nível para conceitos por trás de registros e a janela de registros, consulte [Noções básicas de depuração: janela registra](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Para exibir a janela Registros  
  
-   Sobre o **depurar** menu, escolha **Windows**e, em seguida, escolha **registra**.  
  
     O depurador deve estar em execução ou no modo de interrupção.  
  
    > [!NOTE]
    >  As informações de registro não estão disponíveis para scripts ou aplicativos SQL.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas sobre depuração: janela Registros](../debugger/debugging-basics-registers-window.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Noções básicas sobre depuração: janela Registros](../debugger/debugging-basics-registers-window.md)