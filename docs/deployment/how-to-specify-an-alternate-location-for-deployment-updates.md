---
title: 'Como: especificar um local alternativo para implantação de atualizações | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14c6778d5cad698e6eea541b94df6f8eb793746c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31561344"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Como especificar um local alternativo para atualizações da implantação
Você pode instalar o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo inicialmente de um CD ou um compartilhamento de arquivos, mas o aplicativo deve verificar se há atualizações periódicas na Web. Você pode especificar um local alternativo para atualizações em seu manifesto de implantação para que seu aplicativo possa atualizar próprio da Web após sua instalação inicial.  
  
> [!NOTE]
>  Seu aplicativo deve ser configurado para instalar localmente para usar esse recurso. Para obter mais informações, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Além disso, se você instalar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo da rede, definindo um local alternativo causas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para usar esse local para a instalação inicial e todas as atualizações subsequentes. Se você instalar o aplicativo localmente (por exemplo, a partir de um CD), a instalação inicial é executada usando a mídia original e todas as atualizações subsequentes usarão o local alternativo.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Especificando um local alternativo para atualizações usando MageUI.exe (utilitário baseado em Windows Forms)  
  
1.  Abra um prompt de comando do .NET Framework e digite:  
  
     **MageUI.exe**  
  
2.  Sobre o **arquivo** menu, escolha **abrir** para abrir o manifesto de implantação do aplicativo.  
  
3.  Selecione o **opções de implantação** guia.  
  
4.  Na caixa de texto denominada **local iniciar**, digite a URL para o diretório que contém o manifesto de implantação para atualizações de aplicativos.  
  
5.  Salve o manifesto de implantação.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Especificando um local alternativo para atualizações usando Mage.exe  
  
1.  Abra um prompt de comando do .NET Framework.  
  
2.  Defina o local de atualização usando o comando a seguir. Neste exemplo, **HelloWorld.exe.application** é o caminho para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto do aplicativo, que sempre tem a extensão. Application, e **http://adatum.com/Update/Path** é a URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] irá verificar se há atualizações do aplicativo.  
  
     **Imagem-atualizar HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3.  Salve o arquivo.  
  
    > [!NOTE]
    >  Agora, você precisa entrar novamente o arquivo com Mage.exe. Para obter mais informações, consulte [passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Se você instalar o aplicativo de uma mídia offline, como um CD, e o computador está online, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] primeiro verifica a URL especificada pelo `<deploymentProvider>` marca no manifesto de implantação para determinar se o local de atualização contém uma versão mais recente do aplicativo. Em caso afirmativo, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instala o aplicativo diretamente a partir daí, em vez do diretório de instalação inicial, e o common language runtime (CLR) determina a relação de confiança do aplicativo usando o nível `<deploymentProvider>`. Se o computador estiver offline, ou `<deploymentProvider>` está inacessível, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalações do CD e o CLR concede confiança com base no ponto de instalação; para uma instalação do CD, isso significa que seu aplicativo recebe confiança total. Todas as atualizações subsequentes herdarão o nível de confiança.  
  
 Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos que usam `<deploymentProvider>` deve declarar explicitamente as permissões necessárias no manifesto do aplicativo, para que o aplicativo não receba a diferentes níveis de confiança em computadores diferentes.  
  
## <a name="see-also"></a>Consulte também  
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)  (Instruções passo a passo: implantando manualmente um aplicativo ClickOnce)  
 [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Escolhendo uma estratégia de atualização do ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)