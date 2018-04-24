---
title: 'CA2003: não tratar fibras como threads'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf33bf27036400bd75b3c61960f35448df3abead
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: não tratar fibras como threads
|||
|-|-|
|NomeDoTipo|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um thread gerenciado está sendo tratado como um thread do Win32.

## <a name="rule-description"></a>Descrição da Regra
 Não suponha que um thread gerenciado é um thread do Win32. É uma fibra. O common language runtime (CLR) serão executados threads gerenciados como fibras no contexto de threads reais que pertencem ao SQL. Esses threads podem ser compartilhados entre AppDomains e até mesmo bancos de dados no processo do SQL Server. Usando gerenciado funcionará armazenamento local de thread, mas não pode usar o armazenamento local de thread não gerenciado ou suponha que seu código será executado novamente no thread atual do sistema operacional. Não altere as configurações como a localidade do thread. Não chame CreateCriticalSection ou CreateMutex por meio de P/Invoke porque eles requerem que o thread que insere um bloqueio também deve fechar o bloqueio. Como esse não será o caso quando você usar fibras, mutexes e seções críticas do Win32 serão inúteis em SQL. Com segurança, você pode usar a maioria do estado em um objeto System.Thread gerenciado. Isso inclui o armazenamento local de thread gerenciado e a cultura de interface do usuário do usuário atual do thread. No entanto, para a programação de motivos de modelo, você não poderá alterar a cultura atual de um thread quando você usar o SQL; Isso será imposto por meio de uma nova permissão.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Examine o uso de threads e alterar seu código.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você não deve suprimir essa regra.