---
title: "Segurança no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c9d546d4020cb9a8e73efdea77fdb85d77d6146d
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="security-in-visual-studio"></a>Segurança no Visual Studio

Você deve considerar a segurança em todos os aspectos do desenvolvimento do aplicativo, do design à implantação. Comece executando o Visual Studio com a máxima segurança possível. Consulte [Permissões de usuário](../ide/user-permissions-and-visual-studio.md).  
  
 Para que você desenvolva aplicativos efetivamente seguros, é preciso ter um entendimento básico dos conceitos e dos recursos de segurança das plataformas para as quais você está desenvolvendo. Também é preciso entender as técnicas de codificação segura.  
  
## <a name="understanding-security"></a>Noções básicas de segurança  
 [Segurança](/dotnet/standard/security/index)  
 Descreve a segurança de acesso do código, a segurança baseada em função, a política de segurança e as ferramentas de segurança do .NET Framework.  
  
 [Defenda seu código com as dez principais dicas de segurança que todo desenvolvedor deve conhecer](http://go.microsoft.com/fwlink/?LinkId=72877)  
 Descreve os problemas com os quais você deve tomar cuidado para que não comprometam os dados ou o sistema.  
  
## <a name="coding-for-security"></a>Codificação de segurança  
 A maioria dos erros de codificação resulta em vulnerabilidades de segurança que ocorrem porque os desenvolvedores fazem suposições incorretas ao trabalhar com a entrada do usuário ou porque eles não entendem completamente a plataforma para a qual estão desenvolvendo.  
  
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)  
 Fornece diretrizes de classificação de componentes para solucionar problemas de segurança.  
  
 [Práticas Recomendadas de segurança](/cpp/top/security-best-practices-for-cpp)  
 Aborda estouros de buffer e a visão completa do recurso de verificações de segurança do Microsoft Visual C++ fornecido pelo sinalizador de tempo de compilação /GS.

## <a name="building-for-security"></a>Compilação com segurança  
 A segurança também é uma consideração importante no processo de compilação.  Algumas etapas adicionais podem melhorar a segurança de um aplicativo implantado e ajudar a evitar engenharia reversa não autorizada, falsificação ou outros ataques.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Explica como configurar e começar a usar a Proteção Preemptiva gratuita - Dotfuscator Community Edition para proteger assemblies .NET contra o uso não autorizado e engenharia reversa (como depuração não autorizada).
  
 [Gerenciando Assinatura de Assembly e Manifesto](managing-assembly-and-manifest-signing.md)  
 Discute a assinatura de nome forte, que pode ser usada para identificar com exclusividade os componentes de software, impedindo a falsificação de nomes.