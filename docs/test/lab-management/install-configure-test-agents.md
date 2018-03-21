---
title: Instalar e configurar agentes de teste no Visual Studio | Microsoft Docs
ms.date: 03/02/2018
ms.technology: vs-devops-test
ms.topic: article
helpviewer_keywords:
- configure test agents, test lab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 16e29676ec67bc3fd22313debe70ba8dbcd7fd76
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="install-and-configure-test-agents"></a>Instalar e configurar agentes de teste

Para cenários de teste que usam o Visual Studio e o Visual Studio Team Services (VSTS) ou o Team Foundation Server (TFS), não é necessário ter um controlador de teste. Agents para Visual Studio gerenciam a orquestração comunicando-se com VSTS ou TFS. Um cenário pode ser que você execute testes contínuos para fluxos de trabalho de compilação e lançamento no VSTS ou TFS.

Você também pode considerar mais fácil usar [o gerenciamento de compilação ou lançamento](use-build-or-rm-instead-of-lab-management.md) em vez do gerenciamento de laboratório.

## <a name="system-requirements"></a>Requisitos do sistema

| Item | Requisitos |
| ---- | ------------ |
| **Agente** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows XP Service Pack 3<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Versão 2, Service Pack 1 |
| **Controlador** | Windows 10<br />Windows 8, Windows 8.1<br />Windows 7 Service Pack 1<br />Windows Server 2012, Windows Server 2012 R2<br />Windows Server 2008 Versão 2, Service Pack 1 |
| **.NET Framework** | .NET Framework 4.5 |

## <a name="install-the-test-controller-and-test-agents"></a>Instalar o controlador de teste e agentes de teste

Você pode baixar agentes para o Visual Studio 2017 pelo site [visualstudio.com](https://www.visualstudio.com/downloads/?q=agents). Procure *Agents para Visual Studio de 2017* e selecione *Agente* ou *Controlador*. Você pode baixar agentes para Visual Studio 2015 e Visual Studio 2013 pela página [downloads mais antigos](https://www.visualstudio.com/vs/older-downloads/).

Esses instaladores estão disponíveis como arquivos ISO para a instalação fácil em máquinas virtuais.

## <a name="compatible-versions-of-tfs-microsoft-test-manager-the-test-controller-and-test-agent"></a>Versões compatíveis do TFS, do Microsoft Test Manager, do controlador de teste e do agente de teste

Você pode misturar versões diferentes do TFS, o Microsoft Test Manager (MTM), o controlador de teste e o agente de teste, conforme a tabela a seguir:

| TFS | MTM com a Central de Laboratório | Controlador | Agente |
| --- | -------------------------------------- | ---------- | ----- |
| 2017: atualizar do 2015 ou nova instalação | 2017 | 2017 | 2017 |
| 2017: atualizar do 2015 ou nova instalação | 2017 | 2013 Atualização 5 | 2013 Atualização 5 |
| 2017: atualizar do 2015 ou nova instalação | 2015 | 2013 Atualização 5 | 2013 Atualização 5 |
| 2015: atualizar do 2013 | 2013 | 2013 |2013 |
| 2015: nova instalação | 2013 | 2013 | 2013 |
| 2015: atualizar do 2013 ou nova instalação | 2015 | 2013 | 2013 |
| 2013 | 2015 | 2013 | 2013 |

## <a name="upgrade-from-visual-studio-2013-test-agents"></a>Atualizar de agentes de teste do Visual Studio 2013

É recomendável que você use agentes para Visual Studio em todos os novos cenários de teste automatizado. Você pode usar a tarefa de *Implantar Agentes de Teste* em uma definição de build para baixar e instalar os agentes de teste em seu computador.

A tabela a seguir mostra os cenários com suporte pelo Agents para o Visual Studio 2013 e as alternativas para o Team Foundation Server (TFS) 2015 e VSTS:

| Cenários com suporte pelo Agents para Visual Studio 2013 | Alternativa no TFS e VSTS |
| --- | --- |
| Fluxo de trabalho compilar-implantar-testar no Visual Studio | Os usuários podem usar uma [definição de build](/vsts/build-release/) (não um build XAML) para compilar, implantar e testar os cenários no TFS. |
| Teste de carga (teste de desempenho) usando computadores remotos locais | Use o Test Controller e o Test Agents 2013 Atualização 5 para executar os testes de carga locais. Para saber mais, veja [Uso de um Test Controller e Test Agents em um teste de carga](https://msdn.microsoft.com/library/ff400223.aspx). |
| Execução remota de testes automatizados do Microsoft Test Manager usando um ambiente de laboratório | Atualmente não há nenhuma alternativa para esse cenário. Recomendamos que você use a tarefa Executar Testes Funcionais nas definições de build e versão (não em um build XAML) para executar testes remotamente. |
| Desenvolvedores executando testes remotos no Visual Studio | Não há mais suporte. |

## <a name="see-also"></a>Consulte também

* [Configurar computadores e coletar informações de diagnóstico](https://msdn.microsoft.com/library/dd286743%28v=vs.140%29.aspx)
