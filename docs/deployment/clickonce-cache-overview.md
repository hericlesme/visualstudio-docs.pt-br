---
title: Visão geral do Cache do ClickOnce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff72cd106f39b4573a0e1d61715dad4f8c65140
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-cache-overview"></a>Visão geral do cache do ClickOnce
Todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos, se eles são instalados localmente ou hospedados online, são armazenados no computador cliente em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplicativo *cache*. Um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache é uma família de diretórios sob o diretório de configurações Local da pasta de documentos e as configurações do usuário atual. Esse cache contém todos os arquivos do aplicativo, incluindo assemblies, arquivos de configuração, aplicativo e as configurações de usuário e diretório de dados. O cache também é responsável para migrar o diretório de dados do aplicativo para a versão mais recente. Para obter mais informações sobre migração de dados, consulte [acesso Local e remoto de dados em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
 Fornecendo um único local para armazenamento de aplicativos, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] assume a tarefa de gerenciar a instalação física de um aplicativo do usuário. O cache também ajuda a isolar os aplicativos, mantendo os assemblies e arquivos de dados para todos os aplicativos e suas versões distintos separam uns dos outros. Por exemplo, quando você atualiza um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo, versão e seus recursos de dados são fornecidos com seus próprios diretórios no cache.  
  
## <a name="cache-storage-quota"></a>Cota de armazenamento do cache  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos hospedados online são restritos na quantidade de espaço que podem ocupar por uma que restringe o tamanho da cota de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cache. O tamanho do cache se aplica a todos os aplicativos do usuário online; um único aplicativo parcialmente confiável, online é limitado a que ocupa a metade do espaço de cota. Aplicativos instalados não são limitados pelo tamanho do cache e não contam em relação ao limite de cache. Para todos os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos, o cache mantém apenas a versão atual e a versão instalada anteriormente.  
  
 Por padrão, os computadores cliente têm 250 MB de armazenamento para on-line [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos. Arquivos de dados não contam para esse limite. Um administrador de sistema pode ampliar ou reduzir essa cota em um computador cliente específico, alterando a chave do registro, HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB, que é um valor DWORD que expressa o tamanho do cache em quilobytes. Por exemplo, para reduzir o tamanho do cache a 50 MB, você deve alterar esse valor para 51200.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)