---
title: "Como: verificar as configurações de propriedade do IIS | Microsoft Docs"
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
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0d58ea851423e9239d8685f89890b5d9e152d53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-verify-iis-property-settings"></a>Como verificar as configurações de propriedade do IIS
Você pode definir as propriedades de um aplicativo Web usando a ferramenta de administração do IIS. Essas propriedades devem ser definidas corretamente para que o aplicativo seja executado, de modo que verificar essas configurações geralmente é uma etapa necessária na solução de problemas.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>Para verificar as configurações do IIS para o aplicativo Web  
  
1.  Abra o **ferramentas administrativas** janela: no **iniciar** , aponte para **programas**e, em seguida, clique em **ferramentas administrativas**. Se **ferramentas administrativas** não aparecer a **programas** menu, em seguida, procure por ele no **painel de controle**.  
  
    -   No Windows 2000, selecione **Gerenciador de serviços de Internet**.  
  
    -   No Windows XP, selecione **Internet Information Services**.  
  
    -   No Windows Server 2003, clique duas vezes em **gerenciar o servidor**.  
  
         O **Gerenciar servidor** janela será aberta. Em **Application Server**, clique em **gerenciar este servidor de aplicativo**.  
  
         O **Application Server** janela será aberta. Abra o **serviços de informações da Internet (IIS) Manager** nó no painel esquerdo.  
  
2.  Na caixa de diálogo, clique no nó de controle de árvore para seu computador. Clique o **Sites da Web** nó e selecione o nó do aplicativo da Web. Ele será um nó do site e, portanto, um irmão do **Default Web Site** ou um diretório virtual nó sob um nó do site da Web existente.  
  
3.  Clique no aplicativo Web e, no menu de atalho, clique em **propriedades**.  
  
4.  Verifique as configurações de segurança para o aplicativo Web:  
  
    1.  No aplicativo Web **propriedades** janela, clique no **segurança de diretório** guia e, em seguida, clique em **editar**.  
  
    2.  No **métodos de autenticação** caixa de diálogo, selecione **habilitar o acesso anônimo** e **autenticação integrada do Windows** se ainda não estiverem selecionados.  
  
    3.  Clique em **Okey** para fechar o **métodos de autenticação** caixa de diálogo.  
  
5.  Para um aplicativo do servidor ATL, verifique se o verbo DEBUG está associado à extensão ISAPI. Para obter mais informações, consulte [como: associar verbo DEBUG com extensão](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Para uma [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo, verifique se a pasta virtual para o aplicativo tem um nome de aplicativo definido em **serviços de informações da Internet (IIS) Manager**, **Gerenciador de serviços de Internet** ou  **Serviços de informações da Internet**.  
  
    1.  No aplicativo Web **propriedades** janela, selecione o **diretório** guia, se o aplicativo estiver em um diretório virtual, ou o **diretório base** guia, se o aplicativo está em um site da Web.  
  
    2.  Verifique o nome no **caminho Local** corresponde ao nome do diretório onde o aplicativo foi realmente implantado.  
  
    3.  Em **configurações do aplicativo**, digite o nome do diretório raiz que contém o aplicativo.  
  
    4.  Clique em **Okey** para fechar o **propriedades** caixa de diálogo.  
  
7.  Para uma [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo, clique no **ASP.NET** guia e verificar se a versão correta do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] for especificado.  
  
8.  Clique em **Okey** para fechar o **propriedades** caixa de diálogo.  
  
9. Clique em **Okey** para fechar o **serviços de informações da Internet (IIS) Manager**, **Gerenciador de serviços de Internet**, ou **Internet Information Services**caixa de diálogo.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas](../debugger/debugging-web-applications-troubleshooting.md)