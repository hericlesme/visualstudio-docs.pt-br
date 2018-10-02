---
title: 'Como: depurar DLLs nativas | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 467b87c1a0e72c5523523aae015f03b54273907c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47587867"
---
# <a name="how-to-debug-native-dlls"></a>Como depurar DLLs nativas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: depurar DLLs nativas](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-native-dlls).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Quando você depura uma DLL, pode iniciar a depuração de:  
  
-   O projeto usado para criar o executável que chama a DLL.  
  
 \- ou -  
  
-   O projeto usado para criar a própria DLL.  
  
 Se você tiver o projeto usado para criar o executável, inicie a depuração do início desse projeto. Você pode abrir um arquivo de origem para a DLL e definir os pontos de interrupção nesse arquivo, mesmo que não seja uma parte do projeto usado para criar o executável. Para obter mais informações, consulte [pontos de interrupção](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
 Se você iniciar a depuração do projeto que cria a DLL, deverá especificar o executável que deseja usar ao depurar a DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Para especificar um executável para a sessão de depuração  
  
1.  Na **Gerenciador de soluções**, selecione o projeto que cria a DLL.  
  
2.  Dos **modo de exibição** menu, escolha**páginas de propriedade**.  
  
3.  No **páginas de propriedades** caixa de diálogo, abra o **propriedades de configuração** pasta e selecione o **depuração** categoria.  
  
4.  No **comando** , especifique o nome do caminho para o contêiner. Por exemplo, C:\Arquivos de Programas\MyApplication\MYAPP.EXE.  
  
5.  No **argumentos de comando** , especifique todos os argumentos necessários para o executável.  
  
 Se você não especificar o executável na _Project_**páginas de propriedades** caixa de diálogo, o [executável para a caixa de diálogo de sessão de depuração](../debugger/executable-for-debugging-session-dialog-box.md) aparece quando você iniciar a depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)



