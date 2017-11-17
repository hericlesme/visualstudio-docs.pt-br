---
title: "ClickOnce e configurações de aplicativo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: fbe35de06ac09c95a045748a5d8ecb379779a20a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce e configurações de aplicativo
Configurações de aplicativo para Windows Forms torna fácil criar, armazenar e manter aplicativos personalizados e preferências do usuário no cliente. Este documento descreve o funcionam dos arquivos de configurações do aplicativo em um aplicativo ClickOnce, e como o ClickOnce migra as configurações quando o usuário é atualizado para a próxima versão.  
  
 As informações a seguir aplica-se somente para o provedor de configurações de aplicativo padrão, a <xref:System.Configuration.LocalFileSettingsProvider> classe. Se você fornecer um provedor personalizado, esse provedor determinam como ela armazena seus dados e como atualizar suas configurações entre versões. Para obter mais informações sobre provedores de configurações do aplicativo, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Arquivos de configurações do aplicativo  
 Configurações do aplicativo consome dois arquivos: *aplicativo*. exe e User. config, onde *aplicativo* é o nome do seu aplicativo do Windows Forms. User. config é criado na hora do cliente primeiro que seu aplicativo armazena configurações no escopo do usuário. *aplicativo*. exe, por outro lado, continuará a existir antes da implantação se você definir valores padrão para configurações. O Visual Studio incluirá esse arquivo automaticamente quando você usa seu **publicar** comando. Se você criar seu aplicativo ClickOnce usando Mage.exe ou MageUI.exe, você deve verificar se esse arquivo está incluído no seu aplicativo do outros arquivos quando você preencher o manifesto do aplicativo.  
  
 Em um aplicativo de Windows Forms não implantado usando o ClickOnce, um aplicativo *aplicativo*. exe é armazenado no diretório de aplicativo, enquanto o arquivo User. config está armazenado o usuário **Documents and Settings**  pasta. Em um aplicativo ClickOnce, *aplicativo*. exe reside no diretório do aplicativo dentro de cache do aplicativo ClickOnce e User. config reside no diretório de dados ClickOnce para o aplicativo.  
  
 Independentemente de como implantar seu aplicativo, as configurações do aplicativo garante a segurança de acesso de leitura ao *aplicativo*. exe e acesso de leitura/gravação seguro para User. config.  
  
 Em um aplicativo ClickOnce, o tamanho dos arquivos de configuração usados pelas configurações de aplicativo é restrito pelo tamanho do cache do ClickOnce. Para obter mais informações, consulte [visão geral de Cache do ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Atualizações de versão  
 Assim como cada versão de um aplicativo ClickOnce é isolada de todas as outras versões, as configurações do aplicativo para um aplicativo ClickOnce são isoladas de configurações para outras versões também. Quando o usuário é atualizado para uma versão posterior do seu aplicativo, as configurações do aplicativo compara as configurações de versão mais recente (número mais alto) com as configurações fornecidas com a versão atualizada e os mescla as configurações em um novo conjunto de arquivos de configuração.  
  
 A tabela a seguir descreve como as configurações do aplicativo decidir quais configurações para copiar.  
  
|Tipo de alteração|Ação de atualização|  
|--------------------|--------------------|  
|Configuração adicionada ao *aplicativo*. exe|A nova configuração será mesclada a versão atual *aplicativo*. exe|  
|Configuração removida do *aplicativo*. exe|A configuração antiga é removida da versão atual *aplicativo*. exe|  
|Padrão da configuração alterada; configuração local ainda definida como padrão original em User. config|A configuração é mesclada em User. config da versão atual com o novo padrão como o valor|  
|Padrão da configuração alterada; configuração definida como não-padrão em User. config|A configuração é mesclada em config da versão atual com o valor padrão não mantido|  
  
 Se você tiver criado suas próprias configurações de aplicativo classe wrapper e deseja personalizar a lógica de atualização, você pode substituir o <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> método.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce e configurações de Roaming  
 ClickOnce não funciona com as configurações de roaming, que permite que o arquivo de configurações a seguir você em computadores em uma rede. Se você precisar de configurações de roaming, será necessário implementar um provedor de configurações de aplicativo que armazena as configurações de rede ou desenvolver suas próprias classes de configurações personalizadas para armazenar as configurações em um computador remoto. Para obter mais informações em provedores de configurações, consulte [arquitetura de configurações do aplicativo](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Visão geral sobre configurações de aplicativo](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Visão geral do Cache do ClickOnce](../deployment/clickonce-cache-overview.md)   
 [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)