---
title: "Criando uma extensão com uma janela de ferramentas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e4e01959df5da96018aa8f1d06fce1076e732096
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-a-tool-window"></a>Criando uma extensão com uma janela de ferramenta
Neste procedimento, você aprenderá a usar o modelo de projeto do VSIX e **janela da ferramenta personalizada** modelo de item para criar uma extensão com uma janela de ferramenta.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Criar uma janela de ferramenta  
  
1.  Crie um projeto do VSIX denominado **FirstWindow**. Você pode encontrar o modelo de projeto do VSIX no **novo projeto** caixa de diálogo em **Visual C# / extensibilidade**.  
  
2.  Quando o projeto for aberto, adicionar um modelo de item da janela de ferramenta chamado **MyWindow**. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **Adicionar / Novo Item**. No **Adicionar Novo Item** caixa de diálogo, vá para **Visual C# / extensibilidade** e selecione **janela da ferramenta personalizada**. No **nome** campo na parte inferior da janela, altere o nome de arquivo da janela de ferramenta **MyWindow.cs**.  
  
3.  Compile o projeto e comece a depuração.  
  
     É exibida a instância experimental do Visual Studio. Para obter mais informações sobre a instância experimental, consulte [a instância Experimental](../extensibility/the-experimental-instance.md).  
  
4.  Na instância experimental, vá para **exibição / outras janelas**.  
  
     Você deve ver um item de menu para **MyWindow**. Clique nele.  
  
     Você verá uma janela de ferramenta com o título **MyWindow** e dizer um botão **clique Me!.**