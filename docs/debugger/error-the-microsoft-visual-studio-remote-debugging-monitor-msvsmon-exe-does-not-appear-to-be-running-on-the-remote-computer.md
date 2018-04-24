---
title: 'Erro: o Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto. | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 683af8cf0c75068a58b5e8cf4732cdf69c586d4f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio (MSVSMON.EXE) parece não estar sendo executado no computador remoto.
Essa mensagem de erro significa que o Visual Studio não pôde localizar a instância correta do Visual Studio Remote Debugging Monitor no computador remoto. O Visual Studio Remote Debugging Monitor deve ser instalado para a depuração remota de trabalho. Para obter informações sobre como baixar e configurar o depurador remoto, consulte [depuração remota](../debugger/remote-debugging.md).  
  
> [!IMPORTANT]
>  Se você acredita ter recebido esta mensagem devido a um bug no produto, [relatar o problema para o Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Se você precisar de mais ajuda, consulte [Fale conosco](../ide/talk-to-us.md) para formas de contatar a Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Recebi a seguinte mensagem enquanto eu estava depurando no Visual Studio 2010 ou anterior  
 Se a versão do Visual Studio que você estiver usando o Visual Studio 2010 ou anterior, você também poderá receber esse erro se o compartilhamento de arquivos e impressora não está habilitado. Para obter mais informações sobre esse problema, consulte a versão do Visual Studio 2010 desta documentação: [erro: O Microsoft Visual Studio Monitor de depuração remota (MSVSMON. EXE) parece não estar em execução no computador remoto. -O visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Recebi a seguinte mensagem enquanto eu estava depurando localmente  
 Se você estiver recebendo essa mensagem enquanto você estiver depurando localmente, o software antivírus ou um firewall de terceiros pode ser de culpado. Visual Studio é um aplicativo de 32 bits, portanto, ele usa a versão de 64 bits do depurador remoto para depurar aplicativos de 64 bits. Os dois processos se comunicam usando a rede local no computador local. Nenhum tráfego deixa o computador, mas é possível que o software de segurança de terceiros pode bloquear a comunicação.  
  
 As seções a seguir listam algumas outras razões por que você pode ter chegado essa mensagem e que você pode fazer para corrigir o problema.  
  
## <a name="the-remote-machine-is-not-reachable"></a>O computador remoto não está acessível  
 Tente [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) o computador remoto. Se ele não responder ao ping, as ferramentas remotas não será capazes de se conectar a um. Tente reiniciar o computador remoto e caso contrário, certificando-se de que ele está configurado corretamente na rede.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>A versão do depurador remoto não corresponde à versão do Visual Studio  
 A versão do Visual Studio que estão sendo executados localmente precisa corresponder à versão do monitor de depuração remota em execução no computador remoto. Para corrigir isso, baixe e instale a versão correspondente do monitor de depuração remota. Vá para o [Centro de Download](http://www.microsoft.com/en-us/download) para localizar a versão correta do depurador remoto.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>As máquinas locais e remotas têm diferentes modos de autenticação  
 As máquinas locais e remotas precisam usar o mesmo modo de autenticação. Para corrigir isso, certifique-se de que ambos os computadores estão usando o mesmo modo de autenticação. Para obter mais informações sobre modos de autenticação, consulte [visão geral de autenticação do Windows](https://technet.microsoft.com/en-us/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>O depurador remoto é executado sob uma conta de usuário diferente  
 Você pode resolver isso em uma das seguintes maneiras:  
  
-   Você pode parar o depurador remoto e reiniciá-lo com a conta que você está usando no computador local.  
  
-   Você pode iniciar o depurador remoto na linha de comando com o **/ permitir \<nome de usuário >** parâmetro: `msvsmon /allow <username@computer>`  
  
-   Você pode adicionar o usuário para permissões do depurador remoto (na janela de depurador remoto, **Ferramentas > permissões**).  
  
-   Se você não pode usar os métodos nas etapas anteriores, você pode permitir que qualquer usuário pode fazer a depuração remota. Na janela de depurador remoto, vá para o **Ferramentas > Opções** caixa de diálogo. Quando você seleciona **sem autenticação**, em seguida, você pode verificar **permitir que qualquer usuário depure**. No entanto, você deve usar essa opção somente se você não tem escolha, ou se você estiver usando uma rede privada.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>O firewall no computador remoto não permite conexões de entrada para o depurador remoto  
 O firewall no computador do Visual Studio e o firewall no computador remoto devem ser configurados para permitir a comunicação entre o Visual Studio e o depurador remoto. Para obter informações sobre as portas que o depurador remoto está usando, consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Para obter informações sobre como configurar o firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>O software antivírus está bloqueando as conexões  
 Software antivírus do Windows permite conexões do depurador remoto, mas alguns software de antivírus de terceiros pode bloqueá-los. Verifique a documentação do seu software antivírus saber como permitir que essas conexões.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Política de segurança de rede está bloqueando a comunicação entre o computador remoto e o Visual Studio  
 Revise a segurança da rede para certificar-se de que ele não está bloqueando a comunicação. Para obter mais informações sobre a política de segurança de rede do Windows, consulte [configurações de política de segurança](/windows/device-security/security-policy-settings/security-policy-settings).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>A rede está muito ocupada para dar suporte a depuração remota  
 Talvez seja necessário fazer a depuração remota em um momento diferente ou reagendar o trabalho na rede para um horário diferente.  
  
## <a name="more-help"></a>Mais ajuda  
 Para obter ajuda do depurador remota mais, incluindo opções de linha de comando, clique em **Ajuda > uso** na janela de depurador remoto. Se você não estiver com ele aberto você pode ver a página da web, copie a seguinte linha a uma **Explorador de arquivos** janela. (Você precisa substituir \<diretório de instalação do Visual Studio > com o local de instalação do Visual Studio.)  
  
 res: / /*\<diretório de instalação do Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Consulte também  
 [Erros e solução de problemas de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)