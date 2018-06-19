---
title: Localizando o Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- deployment, VSIX
ms.assetid: 680c3b25-7901-4768-8363-6d1fcd1ea636
ms.author: heaths
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed6125c69b9068ebfb3d776ccbefaf88043f83a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138607"
---
# <a name="locating-visual-studio"></a>Localizando o Visual Studio

A partir do Visual Studio de 2017, você pode instalar várias instâncias da mesma versão ou edição mesmo. Isso é útil quando você deseja visualizar a nova funcionalidade no computador de desenvolvimento principal enquanto retém a instalação anterior. Devido a essas alterações, não há nenhum valor de variável ou registro único ambiente que você pode usar para localizar uma instância. Em vez disso, você pode usar um [API de consulta COM](https://msdn.microsoft.com/library/microsoft.visualstudio.setup.configuration.aspx) para localizar instâncias com base em critérios relevantes para sua extensão.

Esta é uma API rápida, somente leitura com pacotes do NuGet para código nativo e gerenciado.

| Código | Pacote |
| ---- | --- |
| Nativo | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Native |
| Gerenciado | https://nuget.org/packages/Microsoft.VisualStudio.Setup.Configuration.Interop |

Você pode localizar uma única instância, dada um caminho ou o processo atual, ou enumerar todas as instâncias. Consulte [nossos exemplos](https://github.com/Microsoft/vs-setup-samples) para conclusão exemplos de como localizar o Visual Studio.

## <a name="tools"></a>Ferramentas

Para localizar o Visual Studio e outras ferramentas em ambientes de desenvolvimento, scripts do PowerShell, instaladores e mais cenários, temos um número de ferramentas de software livre, você pode usar diretamente ou redistribuir junto com seus próprios scripts.

| Projeto | Descrição |
| ------- | ----------- |
| [vswhere](https://github.com/Microsoft/vswhere) | Arquivo único executável nativo para localizar instâncias que atendem aos critérios, como versão ou versão de pré-lançamento, o produto foi instalado e que cargas de trabalho estão instaladas. Também oferece suporte a localizar o Visual Studio 2010 e mais recente, embora menos informações são retornadas que para 2017 do Visual Studio e mais recente. Consulte o [wiki](https://github.com/Microsoft/vswhere/wiki) para obter exemplos. |
| [Cmdlets de VSSetup](https://github.com/Microsoft/vssetup.powershell) | Suporte para cmdlets do PowerShell 2.0 e mais recente que retornam informações detalhadas como objetos que você pode usar para localizar instâncias com base nos mesmos critérios como _vswhere_ e para descobrir as propriedades ainda mais sobre as instâncias. Consulte o [wiki](https://github.com/Microsoft/vssetup.powershell/wiki) para obter exemplos. |
| [VSIXBootstrapper](https://github.com/Microsoft/vsixbootstrapper) | Localiza automaticamente _VSIXInstaller_ e passa a linha de comando por meio de instalar um _*.vsix_ arquivo. Isso pode ser útil em instaladores que não têm suporte direto para os APIs de consulta. Consulte o [wiki](https://github.com/Microsoft/vsixbootstrapper/wiki) para obter exemplos. |

## <a name="see-also"></a>Consulte também

* [Alterações na configuração de 2017 Visual Studio](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup)
