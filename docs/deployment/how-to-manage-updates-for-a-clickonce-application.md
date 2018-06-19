---
title: 'Como: gerenciar atualizações para um aplicativo ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 388523a15ad4d1d4759287fcc1c8ddf32e7b464f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31562540"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Como gerenciar atualizações para um aplicativo ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos podem verificar se há atualizações automaticamente ou programaticamente. Como desenvolvedor, você tem muita flexibilidade para especificar quando e como executar verificações de atualização, se as atualizações são obrigatórias, e onde o aplicativo deve verificar se há atualizações.  
  
 Você pode configurar o aplicativo para verificar se há atualizações automaticamente antes do início do aplicativo ou em intervalos definidos depois que o aplicativo for iniciado. Além disso, você pode especificar uma versão mínima necessária; ou seja, uma atualização é instalada se a versão do usuário é menor do que a versão necessária.  
  
 Você pode configurar o aplicativo para verificar se há atualizações por meio de programação com base em um evento, como uma solicitação de usuário. O procedimento "para verificar se há atualizações programaticamente" neste tópico mostra como você escreve o código que usa o <xref:System.Deployment.Application.ApplicationDeployment> classe para verificar se há atualizações com base em um evento.  
  
 Você também pode implantar seu aplicativo de um local e atualizá-lo de outra. Consulte o procedimento "para especificar um local de atualização diferente."  
  
 Para obter mais informações, consulte [escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Comportamento de atualização é gerenciado no **atualizações do aplicativo** caixa de diálogo, disponível no **publicar** página do **Designer de projeto.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Para verificar se há atualizações antes do aplicativo for iniciado  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **atualizações** para abrir o **atualizações do aplicativo** caixa de diálogo.  
  
4.  No **atualizações do aplicativo** caixa de diálogo caixa, certifique-se de que o **o aplicativo deve verificar se há atualizações** caixa de seleção é marcada.  
  
5.  No **escolha quando o aplicativo deve verificar se há atualizações** seção, selecione **antes de inicia o aplicativo**. Isso garante que os usuários conectados à rede sempre executarem o aplicativo com as atualizações mais recentes.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Para verificar se há atualizações em segundo plano depois que o aplicativo for iniciado  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **atualizações** para abrir o **atualizações do aplicativo** caixa de diálogo.  
  
4.  No **atualizações do aplicativo** caixa de diálogo caixa, certifique-se de que a caixa de seleção **o aplicativo deve verificar se há atualizações** está selecionado.  
  
5.  No **escolha quando o aplicativo deve verificar seção atualizações**, selecione **depois que o aplicativo for iniciado**. O aplicativo será iniciado mais rapidamente, dessa forma, e, em seguida, ele verifica se há atualizações em segundo plano e somente notificar o usuário quando uma atualização está disponível. Uma vez instalado, as atualizações não terão efeito até que o aplicativo seja reiniciado.  
  
6.  No **especificar a frequência com a qual o aplicativo deve verificar se há atualizações** seção, selecione **Verifique sempre que o aplicativo é executado** (o padrão) ou **Verifique cada** e insira um intervalo de tempo e número.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Para especificar uma versão mínima necessária para o aplicativo  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **atualizações** para abrir o **atualizações do aplicativo** caixa de diálogo.  
  
4.  No **atualizações do aplicativo** caixa de diálogo caixa, certifique-se de que o **o aplicativo deve verificar se há atualizações** caixa de seleção é marcada.  
  
5.  Selecione o **especificar uma versão mínima necessária para este aplicativo** caixa de seleção e, em seguida, digite **principais**, **secundária**, **Build**e  **Revisão** números para o aplicativo.  
  
### <a name="to-specify-a-different-update-location"></a>Para especificar um local de atualização diferentes  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **atualizações** para abrir o **atualizações do aplicativo** caixa de diálogo.  
  
4.  No **atualizações do aplicativo** caixa de diálogo caixa, certifique-se de que o **o aplicativo deve verificar se há atualizações** caixa de seleção é marcada.  
  
5.  No **atualizar local** campo, digite o local de atualização com uma URL totalmente qualificada, usando o formato http://Hostname/ApplicationName, ou um caminho UNC no formato \\\Server\ApplicationName ou clique o **procurar** botão para procurar o local de atualização.  
  
### <a name="to-check-for-updates-programmatically"></a>Para verificar atualizações programaticamente  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique o **publicar** guia.  
  
3.  Clique o **atualizações** para abrir o **atualizações do aplicativo** caixa de diálogo.  
  
4.  No **atualizações do aplicativo** caixa de diálogo caixa, certifique-se de que o **o aplicativo deve verificar se há atualizações** caixa de seleção é desmarcada. (Opcionalmente, você pode selecionar essa caixa de seleção de verificação de atualizações por meio de programação e também permitem que o tempo de execução do ClickOnce verificar se há atualizações automaticamente).  
  
5.  No **atualizar local** campo, digite o local de atualização com uma URL totalmente qualificada, usando o formato http://Hostname/ApplicationName, ou um caminho UNC no formato \\\Server\ApplicationName ou clique o **procurar** botão para procurar o local de atualização. O local de atualização é onde o aplicativo irá procurar uma versão atualizada de si mesma.  
  
6.  Crie um botão, o item de menu ou outro item de interface do usuário em um Windows Form que selecionará os usuários para verificar se há atualizações. Manipulador de eventos do item, chame um método para verificar e instalar atualizações. Você pode encontrar um exemplo de código do Visual Basic e Visual c# para tal método em [como: verificar se há atualizações de aplicativo programaticamente usando a API de implantação do ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Crie seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Caixa de diálogo de atualizações de aplicativo](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Como publicar um Aplicativo ClickOnce usando o Assistente de Publicação](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Como verificar se há atualizações do aplicativo programaticamente usando a API de implantação do ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)