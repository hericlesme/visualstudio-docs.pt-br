---
title: 'Erro: o processo de trabalho do site da Web foi encerrado pelo IIS | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fb7a0220cf6650aeeb12ec6549d112a39918de3f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Erro: o processo de trabalho do site foi encerrado pelo IIS
O depurador interrompeu a execução de código no site. Isso fez o IIS (Serviços de Informações da Internet) supor que o processo de trabalho parou de responder. Consequentemente, o IIS terminou o processo de trabalho.  
  
 Para retomar a depuração, será necessário configurar o IIS para permitir que o processo de trabalho continue. Essa mensagem de erro não aparece em versões do IIS que são anteriores ao IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Para configurar o IIS 7 para permitir que o processo de trabalho continue  
  
1.  Abra o **ferramentas administrativas** janela.  
  
    1.  Clique em **iniciar**e, em seguida, escolha **painel de controle**.  
  
    2.  Em **painel de controle**, escolha **alternar para modo de exibição clássico**, se necessário e, em seguida, clique duas vezes em **ferramentas administrativas**.  
  
2.  No **ferramentas administrativas** janela, clique duas vezes em **serviços de informações da Internet (IIS) Manager**.  
  
     O Gerenciador do IIS é aberto.  
  
3.  No **conexões** painel, expanda o \<nome do computador > nó se necessário.  
  
4.  Sob o \<nome do computador > nó, clique em **Pools de aplicativos**.  
  
5.  No **Pools de aplicativos** lista, clique no nome do seu aplicativo é executado no pool e, em seguida, clique em **configurações avançadas**.  
  
6.  No **configurações avançadas** caixa de diálogo caixa, localize o **modelo de processo** seção e execute uma das seguintes ações:  
  
    -   Definir **Ping habilitado** para **False**.  
  
    -   Definir **tempo máximo de resposta de Ping** para um valor maior que 90 segundos.  
  
     Configuração **Ping habilitado** para **False** impede que o IIS verificando se o processo de trabalho ainda está em execução e mantém o processo de trabalho ativo até que você interrompa o processo depurado. Configuração **tempo máximo de resposta de Ping** com um valor grande permite que o IIS continuar a monitorar o processo de trabalho.  
  
7.  Clique em **Okey** para fechar o **configurações avançadas** caixa de diálogo.  
  
8.  Feche o Gerenciador do IIS e o **ferramentas administrativas** janela.  
  
## <a name="see-also"></a>Consulte também  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)