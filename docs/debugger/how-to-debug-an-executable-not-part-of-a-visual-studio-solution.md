---
title: "Como: depurar um executável que não faz parte de uma solução do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: "23"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be07be0e1374360a96b6672b095dcc039c6bb4f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Como: depurar um executável que não faz parte de uma solução do Visual Studio
Às vezes, convém depurar um executável (arquivo .exe) que não é parte de um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Pode ser um executável criado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou um executável que você recebeu de outra pessoa.  
  
A resposta usual para esse problema é iniciar a parte externa executável do Visual Studio e anexá-la a ele usando o depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obter mais informações, consulte [anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
Anexar a um aplicativo requer algumas etapas manuais, por isso demora alguns segundos. Este pequeno atraso significa que a anexação não ajudará se você estiver tentando depurar um problema que ocorre durante a inicialização. Além disso, se você estiver depurando um programa que não aguarda a entrada do usuário, e fecha rapidamente, você poderá não ter tempo para anexar a ele. Se você tiver [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] instalado, você pode criar um projeto EXE para um programa.

> [!NOTE]
>  Nem todas as linguagens de programação oferecem suporte a projetos EXE.

Quando você estiver depurando um executável que não faz parte de sua solução do Visual Studio, os recursos de depuração disponíveis podem ser limitados, se você anexar um executável em execução ou adicionar o executável para um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução.

- Se você tiver o código-fonte, a melhor abordagem será importar o código-fonte para o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e criar uma compilação de depuração do executável no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Se você não tiver o código-fonte, e se o executável foi criado sem [informações de depuração](../debugger/how-to-set-debug-and-release-configurations.md) em um formato compatível, os recursos de depuração disponíveis são muito limitados. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Para criar um projeto EXE para um executável existente  
  
1.  Sobre o **arquivo** menu, clique em **abrir** e selecione **projeto**.  
  
2.  No **Abrir projeto** caixa de diálogo, clique na lista suspensa lista ao lado de **nome de arquivo** caixa e selecione **todos os arquivos de projeto**.  
  
3.  Localizar o executável e, em seguida, clique em **Okey**.  

    Isso cria uma solução temporária que contém o executável.

5.  Iniciar o executável, escolhendo um comando de execução, como **iniciar**, do **depurar** menu.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Para importar um executável em uma solução do Visual Studio  
  
1.  Sobre o **arquivo** , aponte para **Adicionar projeto**e, em seguida, clique em **projeto existente**.  
  
2.  No **Adicionar projeto existente** caixa de diálogo, clique na lista suspensa lista ao lado de **nome de arquivo** caixa e selecione **todos os arquivos de projeto**.  
  
3.  Localize e selecione o executável.  
  
4.  Clique em **OK**.  
  
5.  Iniciar o executável, escolhendo um comando de execução, como **iniciar**, do **depurar** menu.    
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Arquivos DBG](http://msdn.microsoft.com/en-us/91e449e9-8b65-4123-960f-2107cd1f1cfd)