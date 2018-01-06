---
title: "Não é possível anexar ao processo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.unable2attach
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0468de6c-3ff1-4979-a8c6-8afb53f37547
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 691d0352b327dd2665b3a6daf22b3542929d3ca3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="unable-to-attach-to-the-process"></a>Não é possível anexar ao processo
Não é possível anexar ao processo. O componente do depurador no servidor recebeu acesso negado ao se conectar a esse computador.  
  
 Há dois cenários comuns que causam esse erro:  
  
 **Cenário 1:** um computador executando o Windows XP. O computador B executa o Windows Server 2003. O registro no computador B contém o seguinte valor DWORD:  
  
 `HKLM\Software\Microsoft\MachineDebugManager\AllowLaunchAsOtherUser=1`  
  
 O usuário 1 inicia uma sessão do Terminal Server (sessão 1) no computador B e inicia um aplicativo gerenciado a partir dessa sessão.  
  
 O usuário 2, que é o administrador em ambos os computadores, é registrado para a máquina. A partir daí, ele tenta anexar a um aplicativo em execução na sessão 1 na máquina b  
  
 **Cenário 2:** um usuário estiver conectado em dois computadores, A e B, no mesmo grupo de trabalho, usando a mesma senha nos dois computadores. O depurador está em execução no computador A e tentar se conectar a um aplicativo gerenciado em execução em uma máquina b tem **acesso à rede: modelo de compartilhamento e segurança para contas locais** definida como **convidado**.  
  
### <a name="to-solve-scenario-1"></a>Para solucionar o cenário 1  
  
-   Execute o depurador e o aplicativo gerenciado no mesmo nome e senha da conta do usuário.  
  
### <a name="to-solve-scenario-2"></a>Para resolver o cenário 2  
  
1.  Do **iniciar** menu, escolha **painel de controle**.  
  
2.  No painel de controle, clique duas vezes em **ferramentas administrativas**.  
  
3.  Na janela de ferramentas administrativas, clique duas vezes em **política de segurança Local**.  
  
4.  Na janela de política de segurança Local, selecione **políticas locais**.  
  
5.  No **políticas** coluna, clique duas vezes em **acesso à rede: modelo de compartilhamento e segurança para contas locais**.  
  
6.  No **acesso à rede: modelo de compartilhamento e segurança para contas locais** caixa de diálogo, altere a configuração de segurança local para **clássico**e clique em **Okey**.  
  
    > [!CAUTION]
    >  A alteração do modelo de segurança para Clássico pode resultar em acesso inesperado a arquivos e componentes DCOM compartilhados. Se você fizer essa alteração, um usuário remoto poderá ser autenticado com sua conta de usuário local em vez como Convidado. Se um usuário remoto corresponder ao seu nome de usuário e sua senha, esse usuário terá acesso a qualquer pasta ou objeto DCOM você compartilhar. Se você usar esse modelo de segurança, verifique se todas as contas de usuário no computador têm senhas fortes ou configure uma ilha isolada de rede para os computadores de depuração e depurados para impedir o acesso não autorizado.  
  
7.  Feche todas as janelas.  
  
## <a name="see-also"></a>Consulte também  
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)