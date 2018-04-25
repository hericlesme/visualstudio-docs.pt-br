---
title: Mantendo a segurança do aplicativo no Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unauthorized access
- Baseline Security Analyzer
- Microsoft Baseline Security Analyzer
- security [.NET Framework], best practices
- MBSA (Microsoft Baseline Security Analyzer)
- security [.NET Framework], maintaining after deployment
ms.assetid: 621d10c1-842b-4902-be60-bb9719591751
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fb75bfe3c9e479e67c766137ee84e919f9a6710
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="maintaining-security"></a>Mantendo segurança

Costuma-se dizer que o preço da segurança é a vigilância constante. Apesar da sua dedicação à segurança durante o design e desenvolvimento de seu aplicativo, você deve supor que as falhas na segurança surgirão após a implantação. Ao auditar seu aplicativo e analisar os logs de evento, você pode descobrir algumas falhas anteriormente ocultas.

Além de ser vigilante com seu próprio aplicativo, você também deve se manter atualizado sobre as ameaças e falhas de segurança da plataforma na qual seu aplicativo é executado e de outros produtos dos quais seu aplicativo depende.

[Segurança, privacidade e contas](https://support.microsoft.com/products/microsoft-account?category=privacy#security-privacy-accounts-help=windows-8&v0h=winrttab1&v1h=win8tab1&v2h=win7tab1&v3h=winvistatab1)&mdash;Obtenha ajuda com segurança, privacidade e contas de usuário, incluindo informações sobre vírus, senhas, controles dos pais, firewalls e criptografia de unidade.

[Boletins de atualizações de segurança da Microsoft](https://technet.microsoft.com/security/bulletins.aspx)&mdash;Essa página facilita a localização de boletins lançados anteriormente. Destinados aos profissionais de TI, os boletins de segurança fornecem informações detalhadas sobre atualizações de segurança.

[Microsoft Baseline Security Analyzer](https://www.microsoft.com/download/details.aspx?id=7558)&mdash;O Microsoft Baseline Security Analyzer (MBSA) é uma ferramenta que permite a um usuário doméstico individual, um usuário corporativo ou um administrador verificar um ou mais computadores com Windows em busca de erros comuns de configuração de segurança.