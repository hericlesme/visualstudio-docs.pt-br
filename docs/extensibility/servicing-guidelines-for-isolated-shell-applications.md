---
redirect_url: shell/servicing-guidelines-for-isolated-shell-applications
title: "Manutenção diretrizes para isolar aplicativos do Shell | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2c5c8bc626f8a6aabe7fbc450067667d301f11c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Diretrizes de serviço para aplicativos do Shell isolado
Quando você distribui um aplicativo de shell do Visual Studio isolados, você deve ser capaz de fornecer atualizações de software para seu aplicativo após a instalação. Para fazer isso, você deve instalar o aplicativo usando um arquivo do Microsoft Installer (MSI). Esse tipo de instalação permite que as atualizações de software fornecidas pela Microsoft para ser redistribuído por Web baixarem e consumida por seus clientes sem intervenção personalizada.  
  
## <a name="servicing-requirements"></a>Requisitos de serviço  
 Você pode garantir que a instalação do shell isolado pode permitir atualizações, certificando-se de que seu programa de instalação atenda aos seguintes critérios de três.  
  
### <a name="redistribute-by-using-an-msi"></a>Redistribuir usando um MSI  
 Você deve usar um MSI para redistribuir o seu aplicativo, como um MSI preserva a identidade do produto e garante que o aplicativo tem um local físico no computador cliente. Módulos de mesclagem (arquivos. msm) não fornecem essas garantias e não devem ser usados.  
  
### <a name="accounting-for-custom-actions"></a>Estatísticas para ações personalizadas  
 Ações personalizadas são diretivas de instalação não padrão em um programa de instalação. Ações personalizadas alterar parâmetros como locais de arquivos, configurações do registro, as configurações do usuário ou outros itens de instalação. Ações personalizadas podem manipular os dados no momento da instalação.  
  
 Quando você usar ações personalizadas em um programa de instalação, certifique-se de que todas as ações personalizadas durante a instalação devem ter uma ação personalizada correspondente para desfazer a ação quando o usuário desinstala o aplicativo. Se o programa de instalação falha para fornecer correspondente desinstalar ação personalizada, removendo o aplicativo deixará parcialmente instalado.  
  
-   Uma ação personalizada que se baseia em uma versão específica de um arquivo ou hash valores falhará quando as atualizações de software alterar essas versões ou valores de hash. Nesse caso a ação personalizada deve atualizar manualmente esses valores. Um problema adicional ocorre se as versões de um arquivo ou hash de valores são compartilhadas entre versões do produto. Evite essa dependência sempre que possível.  
  
### <a name="accounting-for-shared-files"></a>Estatísticas para arquivos compartilhados  
 Arquivos compartilhados com os mesmos nomes e são instalados no mesmo local por vários produtos. Esses produtos podem diferir em versão, unidade de manter estoque (SKU) ou ambos, e os produtos podem coexistir em um determinado computador. No entanto, os arquivos compartilhados criar problemas de manutenção por vários motivos:  
  
-   Atualizar arquivos compartilhados pode causar problemas de compatibilidade do aplicativo, porque uma atualização para um aplicativo pode alterar a versão de um arquivo usado por um segundo aplicativo não foi atualizado. Instaladores de produtos que compartilham as referências de contagem de arquivos para os arquivos compartilhados. Portanto, desinstalar um produto não afeta arquivos compartilhados além diminuindo a contagem de instâncias instaladas.  
  
-   O instalador de engenharia QFE (Quick Fix) reverte versões de arquivos para as versões dos produtos que o instalador QFE atendido. Esse processo potencialmente quebras de um aplicativo que tinha entregues a um arquivo compartilhado atualizado.