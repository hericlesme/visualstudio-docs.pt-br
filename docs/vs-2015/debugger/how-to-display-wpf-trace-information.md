---
title: 'Como: exibir informações de rastreamento do WPF | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07cdebcc636f768c7caf2437af55f20283db7b6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466994"
---
# <a name="how-to-display-wpf-trace-information"></a>Como exibir informações de acompanhamento WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: exibir informações de rastreamento de WPF](https://docs.microsoft.com/visualstudio/debugger/how-to-display-wpf-trace-information).  
  
[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] pode receber informações de rastreamento de depuração de aplicativos do WPF e exibir essas informações na **saída** janela. Para exibir informações de rastreamento de depuração, rastreamento do WPF deve ser habilitado.  
  
 Você pode habilitar o rastreamento do WPF no arquivo App.config ou programaticamente usando a classe <xref:System.Diagnostics.PresentationTraceSources>. Uma maneira mais fácil para habilitar o rastreamento do WPF é usando o **opções** janela. O rastreamento do WPF para aplicativos Web não tem suporte.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar ou personalizar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** caixa de diálogo, na caixa à esquerda, abra o **depuração** nó.  
  
3.  Sob **Debugging**, clique em **janela de saída**.  
  
4.  Sob **configurações gerais de saída**, selecione **todas as saídas da depuração**.  
  
5.  Na caixa à direita, procure **configurações de rastreamento de WPF**.  
  
6.  Abra o **configurações de rastreamento de WPF** nó.  
  
7.  Sob **configurações de rastreamento do WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **associação de dados**).  
  
     Um controle de lista suspensa aparece na coluna configurações ao lado **associação de dados** ou qualquer categoria que você clicou.  
  
8.  Clique na lista suspensa e selecione o tipo de informações de rastreamento que você deseja ver: **todos os**, **crítico**, **erro**, **aviso**,  **Informações**, **Verbose**, ou **ActivityTracing**.  
  
     **Crítico** habilita o rastreamento de eventos críticos apenas.  
  
     **Erro** habilita o rastreamento de eventos críticos e de erro.  
  
     **Aviso** habilita o rastreamento de crítico, erro e eventos de aviso.  
  
     **Informações** habilita o rastreamento de eventos crítico, erro, aviso e informações.  
  
     **Verbose** habilita o rastreamento de eventos crítico, erro, aviso, informações e detalhado.  
  
     **ActivityTracing** habilita o rastreamento de eventos parar, iniciar, suspender, transferência e continuar.  
  
     Para obter mais informações sobre o significado desses níveis de informações de rastreamento, consulte <xref:System.Diagnostics.SourceLevels>.  
  
9. Clique em **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para desabilitar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** caixa de diálogo, na caixa à esquerda, abra o **depuração** nó.  
  
3.  Sob **Debugging**, clique em **janela de saída**.  
  
4.  Na caixa à direita, procure **configurações de rastreamento de WPF**.  
  
5.  Abra o **configurações de rastreamento de WPF** nó.  
  
6.  Sob **configurações de rastreamento do WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **associação de dados**).  
  
     Um controle de lista suspensa aparece na coluna configurações ao lado **associação de dados** ou qualquer categoria que você clicou.  
  
7.  Clique na lista suspensa e selecione **desativar**.  
  
8.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando WPF](../debugger/debugging-wpf.md)



