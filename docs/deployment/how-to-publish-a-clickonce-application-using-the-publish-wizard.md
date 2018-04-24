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
ms.openlocfilehash: 613c576e895042055d5faee9eeb7c8ca27da078a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Como publicar um aplicativo ClickOnce usando o Assistente de Publicação
Para disponibilizar um aplicativo ClickOnce para os usuários, você deve publicá-lo para um compartilhamento de arquivos ou o caminho, o servidor FTP ou a mídia removível. Você pode publicar o aplicativo usando o Assistente de publicação; propriedades adicionais relacionadas à publicação estão disponíveis no **publicar** página do **Project Designer**. Para obter mais informações, consulte [publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md).  
  
 Antes de executar o Assistente de Publicação, configure as propriedades de publicação corretamente. Por exemplo, se você quiser designar uma chave para assinar seu aplicativo ClickOnce, você pode fazer isso no **assinatura** página do **Project Designer**. Para obter mais informações, consulte [Securing ClickOnce Applications](../deployment/securing-clickonce-applications.md) (Protegendo aplicativos ClickOnce).  
  
> [!NOTE]
>  Ao instalar mais de uma versão de um aplicativo usando o ClickOnce, a instalação moverá as versões anteriores do aplicativo para uma pasta chamada Arquivo, no local de publicação especificado. O arquivamento de versões anteriores dessa maneira mantém o diretório de instalação livre de pastas da versão anterior.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas. Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Para publicar em um compartilhamento de arquivo ou caminho  
  
1.  Em **Solution Explorer**, selecione o projeto de aplicativo.  
  
2.  Sobre o **criar** menu, clique em **publicar**`Projectname`.  
  
     O Assistente de Publicação será exibido.  
  
3.  No **onde você deseja publicar o aplicativo?** página, insira um endereço válido do servidor FTP ou um caminho de arquivo válido usando um dos formatos mostrados e, em seguida, clique em **próximo**.  
  
4.  No **como os usuários instalarão o aplicativo?** , selecione o local onde os usuários irão instalar o aplicativo:  
  
    -   Se os usuários a instalação de um site, clique em **de um site da Web** e digite uma URL que corresponde ao caminho do arquivo digitado na etapa anterior. Clique em **Avançar**. (Essa opção geralmente é usada ao especificar um endereço FTP no local de publicação. O download direto do FTP não tem suporte. Portanto, é necessário inserir uma URL aqui.)  
  
    -   Se os usuários instalarão o aplicativo diretamente do compartilhamento de arquivos, clique em **compartilhamento de arquivo ou caminho de UNC de um**e, em seguida, clique em **próximo**. (Isso é para publicação de locais de c:\deploy\myapp o formulário ou \\\server\myapp.)  
  
    -   Se os usuários forem instalar da mídia removível, clique em **de um CD-ROM ou DVD-ROM**e, em seguida, clique em **próximo**.  
  
5.  Sobre o **o aplicativo estará disponível offline?** página, clique na opção apropriada:  
  
    -   Se você quiser permitir que o aplicativo a ser executado quando o usuário é desconectado da rede, clique em **Sim, este aplicativo estará disponível online ou offline**. Um atalho de **iniciar** menu será criado para o aplicativo.  
  
    -   Se você quiser executar o aplicativo diretamente do local de publicação, clique em **não, este aplicativo está disponível apenas online**. Um atalho de **iniciar** menu não será criado.  
  
     Clique em **Próximo** para continuar.  
  
6.  Clique em **concluir** para publicar o aplicativo.  
  
     O status da publicação é exibido na área de notificação de status.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Publicar para um CD-ROM ou DVD-ROM  
  
1.  Em **Solution Explorer**, com o botão direito no projeto do aplicativo e clique em **propriedades**.  
  
     O **Designer de Projeto** é exibido.  
  
2.  Clique no **publicar** tab para abrir o **publicar** página o **Project Designer**e clique no **Assistente de publicação** botão.  
  
     O Assistente de Publicação será exibido.  
  
3.  No **onde você deseja publicar o aplicativo?** página, insira o caminho do arquivo ou local de FTP em que o aplicativo será publicado, por exemplo d:\deploy. Em seguida, clique em **próximo** para continuar.  
  
4.  No **como os usuários instalarão o aplicativo?** , clique em de um **CD-ROM ou DVD-ROM**e, em seguida, clique em **próximo**.  
  
    > [!NOTE]
    >  Se você quiser que a instalação para executar automaticamente quando o CD-ROM é inserido na unidade, abra o **publicar** página o **Project Designer** e clique no **opções** botão e, em seguida, no **opções de publicação** assistente, selecione **instalações do CD para iniciar o Setup automaticamente quando o CD é inserido**.  
  
5.  Ao distribuir o aplicativo em CD-ROM, você poderá desejar fornecer atualizações a partir de um site da Web. No **onde o aplicativo verificará as atualizações?** página, escolha uma opção de atualização:  
  
    -   Se o aplicativo vai procurar atualizações, clique em **o aplicativo vai procurar atualizações no seguinte local** e insira o local em que as atualizações serão postadas. Poderá ser um local de arquivo, um site ou um servidor FTP.  
  
    -   Se o aplicativo não vai procurar atualizações, clique em **o aplicativo não vai procurar atualizações**.  
  
     Clique em **Próximo** para continuar.  
  
6.  Clique em **concluir** para publicar o aplicativo.  
  
     O status da publicação é exibido na área de notificação de status.  
  
    > [!NOTE]
    >  Após a publicação estar concluída, será necessário utilizar um CD-Rewriter ou DVD-Rewriter para copiar os arquivos do local especificado na etapa 3 para a mídia de CD-ROM ou DVD-ROM.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Implantando uma solução do Office usando o ClickOnce](/office-dev/office-dev/deploying-an-office-solution-by-using-clickonce)