---
title: Segurança no Visual Studio
ms.date: 02/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74e557fd0e92742f33c25d68862ae15254104963
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="security-in-visual-studio"></a>Segurança no Visual Studio

Você deve considerar a segurança em todos os aspectos do desenvolvimento do aplicativo, do design à implantação. Comece executando o Visual Studio com a máxima segurança possível. Confira [Permissões de usuário](../ide/user-permissions-and-visual-studio.md).

 Para que você desenvolva aplicativos efetivamente seguros, é preciso ter um entendimento básico dos conceitos e dos recursos de segurança das plataformas para as quais você está desenvolvendo. Também é preciso entender as técnicas de codificação segura.

## <a name="understand-security"></a>Noções sobre segurança
 [Segurança](/dotnet/standard/security/index) Descreve a segurança de acesso do código, a segurança baseada em função, a política de segurança e as ferramentas de segurança do .NET Framework.

 [Proteja seu código com as dez principais dicas de segurança que todo desenvolvedor precisa saber](http://go.microsoft.com/fwlink/?LinkId=72877) Descreve os problemas com os quais você deve tomar cuidado para que eles não comprometam os dados ou o sistema.

## <a name="code-for-security"></a>Codificar com segurança
 A maioria dos erros de codificação resulta em vulnerabilidades de segurança que ocorrem porque os desenvolvedores fazem suposições incorretas ao trabalhar com a entrada do usuário ou porque eles não entendem completamente a plataforma para a qual estão desenvolvendo.

 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines) Fornece diretrizes de classificação de componentes para solucionar problemas de segurança.

 [Práticas recomendadas de segurança](/cpp/top/security-best-practices-for-cpp) Aborda estouros de buffer e a visão completa do recurso de verificações de segurança do Microsoft Visual C++ fornecido pelo sinalizador de tempo de compilação /GS.

## <a name="build-for-security"></a>Compilar com segurança
 A segurança também é uma consideração importante no processo de compilação.  Algumas etapas adicionais podem melhorar a segurança de um aplicativo implantado e ajudar a evitar engenharia reversa não autorizada, falsificação ou outros ataques.

 [Dotfuscator CE (Community Edition)](dotfuscator/index.md) Explica como configurar e começar a usar a Proteção PreEmptive gratuita do Dotfuscator Community Edition para proteger assemblies .NET contra engenharia reversa e uso não autorizado (como depuração não autorizada).

 [Gerenciar assinatura de assembly e de manifesto](managing-assembly-and-manifest-signing.md) Aborda a assinatura de nome forte, que pode ser usada para identificar com exclusividade os componentes de software, impedindo a falsificação de nomes.