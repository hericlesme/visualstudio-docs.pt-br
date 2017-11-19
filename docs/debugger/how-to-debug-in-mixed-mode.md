---
title: 'Como: depurar no modo misto | Microsoft Docs'
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e319f0e6c9ca6197930858407a2177e9fe246907
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-in-mixed-mode"></a>Como depurar no modo misto
Os procedimentos a seguir descrevem como depurar código gerenciado e código nativo, também conhecido depuração de modo misto. Há dois cenários para fazer isso, dependendo de a DLL ou o aplicativo serem escritos em código nativo:  
  
-   O aplicativo de chamada que chama a DLL é escrito em código nativo. Nesse caso, a DLL é gerenciada e os depuradores gerenciados e nativos devem estar habilitados para depurar ambos. Você pode verificar isso no  **\<projeto > páginas de propriedade** caixa de diálogo. Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada.  
  
-   O aplicativo de chamada que chama a DLL é escrito em código gerenciado e sua DLL é escrita em código nativo.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Se você não tiver acesso ao projeto para o aplicativo de chamada, você pode depurar uma DLL do projeto de DLL. Para obter mais informações, consulte [como: depuração de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md). Você não precisa usar misto para depurar o projeto de DLL.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>Para habilitar a depuração de modo misto (aplicativo de chamada de C++)  
  
1.  Em **Solution Explorer**, selecione o projeto nativo.
  
2.  Sobre o **exibição** menu, clique em **páginas de propriedade**.
  
3.  No  **\<projeto > páginas de propriedade** caixa de diálogo caixa, expanda o **propriedades de configuração** nó e selecione **depuração**.  
  
4.  Definir **tipo de depurador** para **misto** ou **automática**.

    ![Habilitar a depuração de modo misto](../debugger/media/dbg-mixed-mode-from-native.png "habilitar a depuração de modo misto")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>Para habilitar a depuração de modo misto (c# ou VB chamada app)  
  
1.  Em **Solution Explorer**, selecione o projeto gerenciado.  
  
2.  Sobre o **exibição** menu, clique em **páginas de propriedade**.  
  
3.  No  **\<projeto > páginas de propriedade** caixa de diálogo, selecione o **depurar** guia e, em seguida, selecione **habilitar a depuração de código nativo**

    ![Habilitar a depuração de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "habilitar a depuração de código nativo")
  
## <a name="see-also"></a>Consulte também  
 [Como depurar de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md)