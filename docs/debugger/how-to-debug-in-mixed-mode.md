---
title: 'Como: depurar no modo misto | Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 834288c063a4bc0d830f121dcb8589b509c61bcf
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256156"
---
# <a name="how-to-debug-in-mixed-mode"></a>Como depurar no modo misto
Os procedimentos a seguir descrevem como depurar código gerenciado e código nativo, também conhecido depuração de modo misto. Há dois cenários para fazer isso, dependendo de a DLL ou o aplicativo serem escritos em código nativo:  
  
-   O aplicativo de chamada que chama a DLL é escrito em código nativo. Nesse caso, a DLL é gerenciada e os depuradores gerenciados e nativos devem estar habilitados para depurar ambos. Você pode verificar isso na  **\<projeto > páginas de propriedade** caixa de diálogo. Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada.  
  
-   O aplicativo de chamada que chama a DLL é escrito em código gerenciado e sua DLL é escrita em código nativo. Para obter um tutorial que orienta você através dessas etapas, consulte [depurar código gerenciado e nativo](../debugger/how-to-debug-managed-and-native-code.md).
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Se você não tiver acesso ao projeto para o aplicativo de chamada, você pode depurar uma DLL do projeto de DLL. Para obter mais informações, consulte [como: depurar de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md). Você não precisa usar misto para depurar apenas o projeto DLL.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>Para habilitar a depuração de modo misto (aplicativo de chamada do C++)  
  
1.  Na **Gerenciador de soluções**, selecione o projeto nativo.
  
2.  Sobre o **modo de exibição** menu, clique em **páginas de propriedade**.
  
3.  No  **\<projeto > páginas de propriedades** caixa de diálogo caixa, expanda o **as propriedades de configuração** nó e, em seguida, selecione **depuração**.  
  
4.  Definir **tipo de depurador** à **misto** ou **automática**.

    ![Habilitar a depuração de modo misto](../debugger/media/dbg-mixed-mode-from-native.png "habilitar a depuração de modo misto")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>Para habilitar a depuração de modo misto (c# ou VB aplicativo de chamada)  
  
1.  Na **Gerenciador de soluções**, selecione o projeto gerenciado.  
  
2.  Sobre o **modo de exibição** menu, clique em **páginas de propriedade**.  
  
3.  No  **\<projeto > páginas de propriedades** caixa de diálogo, selecione o **depurar** guia e, em seguida, selecione **habilitar a depuração de código nativo**

    ![Habilitar a depuração de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "habilitar a depuração de código nativo")
  
## <a name="see-also"></a>Consulte também  
 [Como depurar de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md)