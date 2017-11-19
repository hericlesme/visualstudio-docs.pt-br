---
title: "Como: exibir informações de rastreamento do WPF | Microsoft Docs"
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
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe00aff9834d612702c61f06a1d0c924852c9462
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-display-wpf-trace-information"></a>Como exibir informações de acompanhamento WPF
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]pode receber informações de rastreamento de depuração de aplicativos do WPF e exibir essas informações no **saída** janela. Para exibir informações de rastreamento de depuração, o rastreamento do WPF deve ser habilitado.  
  
 Você pode habilitar o rastreamento do WPF no arquivo App.config ou programaticamente usando a classe <xref:System.Diagnostics.PresentationTraceSources>. É uma maneira mais fácil para habilitar o rastreamento de WPF usando o **opções** janela. O rastreamento do WPF para aplicativos Web não tem suporte.  
  
### <a name="to-enable-or-customize-wpf-trace-information"></a>Para habilitar ou personalizar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** abrir caixa de diálogo, na caixa à esquerda, o **depuração** nó.  
  
3.  Em **depuração**, clique em **a janela de saída**.  
  
4.  Em **configurações gerais de saída**, selecione **todos saída de depuração**.  
  
5.  Na caixa à direita, procure **as configurações de rastreamento do WPF**.  
  
6.  Abra o **as configurações de rastreamento do WPF** nó.  
  
7.  Em **as configurações de rastreamento do WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **Data Binding**).  
  
     Um controle de lista suspensa aparece na coluna configurações lado **associação de dados** ou qualquer categoria que você clicou.  
  
8.  Clique na lista suspensa e selecione o tipo de informações de rastreamento que você deseja ver: **todos os**, **crítico**, **erro**, **aviso**,  **Informações**, **detalhado**, ou **ActivityTracing**.  
  
     **Crítico** habilita o rastreamento de eventos críticos somente.  
  
     **Erro** habilita o rastreamento de eventos críticos e de erro.  
  
     **Aviso** habilita o rastreamento de erro, crítico e eventos de aviso.  
  
     **Informações** habilita o rastreamento de eventos de erro, crítico, aviso e informações.  
  
     **Verbose** habilita o rastreamento de eventos de erro, crítico, aviso, informações e detalhado.  
  
     **ActivityTracing** habilita o rastreamento de eventos de parar, iniciar, suspender, transferência e continuar.  
  
     Para obter mais informações sobre o significado desses níveis de informações de rastreamento, consulte <xref:System.Diagnostics.SourceLevels>.  
  
9. Clique em **OK**.  
  
### <a name="to-disable-wpf-trace-information"></a>Para desabilitar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  No **opções** abrir caixa de diálogo, na caixa à esquerda, o **depuração** nó.  
  
3.  Em **depuração**, clique em **a janela de saída**.  
  
4.  Na caixa à direita, procure **as configurações de rastreamento do WPF**.  
  
5.  Abra o **as configurações de rastreamento do WPF** nó.  
  
6.  Em **as configurações de rastreamento do WPF**, clique na categoria de configurações que você deseja habilitar (por exemplo, **Data Binding**).  
  
     Um controle de lista suspensa aparece na coluna configurações lado **associação de dados** ou qualquer categoria que você clicou.  
  
7.  Clique na lista suspensa e selecione **Off**.  
  
8.  Clique em **OK**.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando WPF](../debugger/debugging-wpf.md)