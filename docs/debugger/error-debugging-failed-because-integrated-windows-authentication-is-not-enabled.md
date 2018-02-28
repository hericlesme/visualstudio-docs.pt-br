---
title: "Erro: Falha na depuração porque a autenticação integrada do Windows não está habilitada | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d3d66a2892378f04061907e383965c6c02096bf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Erro: falha na depuração porque a autenticação integrada do Windows não está habilitada
A autenticação do usuário que solicitou a depuração foi impedida por um erro de autenticação. Isso pode ocorrer ao tentar entrar em um aplicativo Web ou serviço Web XML. Uma causa desse erro é que a autenticação integrada do Windows não está habilitada. Para habilitá-la, siga as etapas em “Para habilitar a autenticação integrada do Windows”.  
  
 Se você habilitou a autenticação integrada do Windows e esse erro persistir, é possível que esse erro é causado porque **Digest autenticação para servidores de domínio Windows** está habilitado. Nessa situação, você deverá entrar em contato com o administrador da rede.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Para habilitar a autenticação integrada do Windows  
  
1.  Faça logon no servidor Web com uma conta de administrador.  
  
2.  Clique em **iniciar** e, em seguida, clique em **painel de controle**.  
  
3.  Em **painel de controle**, clique duas vezes em **ferramentas administrativas**.  
  
4.  Clique duas vezes em **serviços de informações da Internet**.  
  
5.  Clique no nó do servidor Web.  
  
     Um **Sites da Web** abre pasta sob o nome do servidor.  
  
6.  Você pode configurar a autenticação para todos os sites ou para sites individuais. Para configurar a autenticação para todos os sites da Web, clique com botão direito do **Sites da Web** pasta e depois clique em **propriedades**. Para configurar a autenticação para um site individual, abra o **Sites da Web** pasta, clique no site individual e, em seguida, clique em **propriedades**.  
  
     O **propriedades** caixa de diálogo é exibida.  
  
7.  Clique o **segurança de diretório** guia.  
  
8.  No **controle de acesso e autenticação anônima** seção, clique em **editar**.  
  
     O **métodos de autenticação** caixa de diálogo é exibida.  
  
9. Em **acesso autenticado**, selecione **autenticação integrada do Windows**.  
  
10. Clique em **Okey** para fechar o **métodos de autenticação** caixa de diálogo.  
  
11. Clique em **Okey** para fechar o **propriedades** caixa de diálogo.  
  
12. Fechar o **Internet Information Services** janela.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Para habilitar a autenticação integrada do Windows no Windows Vista/IIS 7  
  
1.  Faça logon no servidor Web com uma conta de administrador.  
  
2.  Ative a Autenticação do Windows e a Compatibilidade de Gerenciamento do II6, se você ainda não tiver feito isso anteriormente, seguindo estas etapas:  
  
    1.  Clique em **iniciar**, clique em **painel de controle** e, em seguida, clique em **programas**.  
  
    2.  Em **programas e recursos**, clique em **ou desativar recursos do Windows ativar**.  
  
         A caixa de diálogo Controle de Acesso do Usuário aparecerá e solicitará para que a permissão continue.  
  
    3.  Clique em **Continue**.  
  
         A caixa de diálogo Recursos do Windows é exibida.  
  
    4.  Na lista de recursos, expanda o **Internet Information Services** nó.  
  
    5.  Em **Internet Information Services**, expanda o **serviços da World Wide Web** nó.  
  
    6.  Em **serviços da World Wide Web**, clique em **segurança**.  
  
    7.  Clique em **autenticação do Windows**.  
  
    8.  Em **Internet Information Services**, expanda o **ferramentas de gerenciamento da Web** nó.  
  
    9. Em **ferramentas de gerenciamento da Web**, expanda o **compatibilidade de gerenciamento do IIS 6** nó e selecione o **da Metabase do IIS 6 e compatibilidade de configuração do IIS 6** caixa de seleção.  
  
    10. Em **ferramentas de gerenciamento da Web**, selecione **Console de gerenciamento IIS** e clique em **Okey.**  
  
    11. Reinicie o computador para que essas alterações tenham efeito.  
  
3.  Clique em **iniciar** e, em seguida, clique em **painel de controle**.  
  
4.  Clique em **exibição clássica**e, em seguida, clique duas vezes em **ferramentas administrativas**.  
  
5.  No **nome** coluna e clique duas vezes em **serviços de informações da Internet (IIS) Manager**.  
  
6.  No **conexões** coluna, expanda o nó para o servidor.  
  
     Um **Sites da Web** abre pasta sob o nome do servidor.  
  
7.  Expanda o **Sites da Web** nó e clique no site para o qual você deseja habilitar a autenticação integrada do Windows.  
  
8.  O título do painel central altera o nome do site que você selecionou. Nesse painel, sob o **IIS** título, clique duas vezes em **autenticação**.  
  
     O título do painel muda para **autenticação**.  
  
9. No **autenticação** painel, no **nome** coluna, clique com botão direito **autenticação do Windows** e, em seguida, clique em **habilitar**.  
  
10. Fechar o **serviços de informações da Internet (IIS) Manager** janela.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando aplicativos da Web: Erros e solução de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Autenticação Digest da Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Executando aplicativos da Web no Windows Vista com o IIS 7.0 e Visual Studio](http://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)