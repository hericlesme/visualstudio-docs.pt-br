---
title: 'Como: publicar um aplicativo ClickOnce usando o Assistente de publicação | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2943f2a9b0e5d23d40b05a481e45095ad52fc8a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078359"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Como: publicar um aplicativo ClickOnce usando o Assistente de publicação
Para disponibilizar um aplicativo ClickOnce para os usuários, você deve publicá-lo para um compartilhamento de arquivo ou caminho, servidor FTP ou mídia removível. Você pode publicar o aplicativo usando o Assistente de publicação; propriedades adicionais relacionadas à publicação estão disponíveis na **Publish** página do **Designer de projeto**. Para obter mais informações, consulte [aplicativos ClickOnce publicação](../deployment/publishing-clickonce-applications.md).  
  
 Antes de executar o Assistente de Publicação, configure as propriedades de publicação corretamente. Por exemplo, se você quiser designar uma chave para assinar o aplicativo ClickOnce, você pode fazer assim por diante a **Signing** página do **Designer de projeto**. Para obter mais informações, consulte [aplicativos ClickOnce Secure](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Quando você instala mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo em uma pasta chamada *arquivamento*, no local de publicação que você especificar. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Para publicar em um compartilhamento de arquivo ou caminho  
  
1.  Na **Gerenciador de soluções**, selecione o projeto de aplicativo.  
  
2.  Sobre o **compilar** menu, clique em **Publish** *Projectname*.  
  
     O Assistente de Publicação será exibido.  
  
3.  No **onde você deseja publicar o aplicativo?** página, insira um endereço válido do servidor FTP ou um caminho de arquivo válido usando um dos formatos mostrados e, em seguida, clique em **próxima**.  
  
4.  No **como os usuários instalarão o aplicativo?** , selecione o local onde os usuários irão instalar o aplicativo:  
  
    -   Se os usuários instalarão um site da Web, clique em **de um site da Web** e digite uma URL que corresponde ao caminho do arquivo digitado na etapa anterior. Clique em **Avançar**. (Essa opção geralmente é usada ao especificar um endereço FTP no local de publicação. O download direto do FTP não tem suporte. Portanto, é necessário inserir uma URL aqui.)  
  
    -   Se os usuários instalarão o aplicativo diretamente do compartilhamento de arquivos, clique em **compartilhamento de arquivo ou caminho de UNC de um**e, em seguida, clique em **próxima**. (Isso é para locais de publicação do formulário *c:\deploy\myapp* ou  *\\\server\myapp*.)  
  
    -   Se os usuários instalarão uma mídia removível, clique em **de um CD-ROM ou DVD-ROM**e, em seguida, clique em **próxima**.  
  
5.  Sobre o **o aplicativo estará disponível offline?** de página, clique na opção apropriada:  
  
    -   Se você quiser permitir que o aplicativo a ser executado quando o usuário estiver desconectado da rede, clique em **Sim, este aplicativo estará disponível online ou offline**. Um atalho na **iniciar** menu será criado para o aplicativo.  
  
    -   Se você quiser executar o aplicativo diretamente do local de publicação, clique em **não, este aplicativo está disponível apenas online**. Um atalho na **iniciar** menu não será criado.  
  
     Clique em **Próximo** para continuar.  
  
6.  Clique em **concluir** para publicar o aplicativo.  
  
     O status da publicação é exibido na área de notificação de status.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Publicar para um CD-ROM ou DVD-ROM  
  
1.  Na **Gerenciador de soluções**, clique com botão direito no projeto de aplicativo e clique em **propriedades**.  
  
     O **Designer de Projeto** é exibido.  
  
2.  Clique o **publicar** tab para abrir o **publicar** página no **Project Designer**e clique no **Assistente de publicação** botão.  
  
     O Assistente de Publicação será exibido.  
  
3.  No **onde você deseja publicar o aplicativo?** , insira o caminho do arquivo ou o local de FTP onde o aplicativo será publicado, por exemplo *d:\deploy*. Em seguida, clique em **próxima** para continuar.  
  
4.  Sobre o **como os usuários instalarão o aplicativo?** , clique em de um **CD-ROM ou DVD-ROM**e, em seguida, clique em **próxima**.  
  
    > [!NOTE]
    >  Se desejar que a instalação para executar automaticamente quando o CD-ROM é inserido na unidade, abra o **Publish** página na **Project Designer** e clique no **opções** botão e, em seguida, nos **opções de publicação** assistente, selecione **instalações para CD, iniciar automaticamente a instalação quando o CD é inserido**.  
  
5.  Ao distribuir o aplicativo em CD-ROM, você poderá desejar fornecer atualizações a partir de um site da Web. No **onde o aplicativo verificará atualizações?** , escolha uma opção de atualização:  
  
    -   Se o aplicativo verificará se há atualizações, clique em **o aplicativo verificará se há atualizações do seguinte local** e insira o local em que as atualizações serão postadas. Poderá ser um local de arquivo, um site ou um servidor FTP.  
  
    -   Se o aplicativo não verificará se há atualizações, clique em **o aplicativo não verificará se há atualizações**.  
  
     Clique em **Próximo** para continuar.  
  
6.  Clique em **concluir** para publicar o aplicativo.  
  
     O status da publicação é exibido na área de notificação de status.  
  
    > [!NOTE]
    >  Após a publicação estar concluída, será necessário utilizar um CD-Rewriter ou DVD-Rewriter para copiar os arquivos do local especificado na etapa 3 para a mídia de CD-ROM ou DVD-ROM.  
  
## <a name="see-also"></a>Consulte também  
 [Implantação e segurança do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implantando uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)