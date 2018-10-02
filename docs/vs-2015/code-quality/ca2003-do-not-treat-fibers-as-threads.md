---
title: 'CA2003: Não tratar fibras como threads | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6563537df74d9e392bad8c4f6ce28c85b8441546
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587326"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: não tratar fibras como threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2003: não tratar fibras como threads](https://docs.microsoft.com/visualstudio/code-quality/ca2003-do-not-treat-fibers-as-threads).

|||
|-|-|
|NomeDoTipo|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa
 Um thread gerenciado está sendo tratado como um thread do Win32.

## <a name="rule-description"></a>Descrição da Regra
 Não pressuponha que um thread gerenciado é um thread do Win32. É uma fibra. O common language runtime (CLR) será executado threads gerenciados como fibras no contexto de threads reais que são de propriedade de SQL. Esses threads podem ser compartilhados entre AppDomains e até mesmo bancos de dados no processo do SQL Server. Usando gerenciado funcionará armazenamento local de thread, mas não pode usar o armazenamento local de thread não gerenciado ou supor que seu código será executado novamente no thread atual do sistema operacional. Não altere as configurações como a localidade do thread. Não chame CreateCriticalSection ou CreateMutex via P/Invoke porque eles requerem que o thread que entra em um bloqueio também deve sair do bloqueio. Como esse não será o caso ao usar fibras, mutexes e seções críticas do Win32 será inútil em SQL. Com segurança, você pode usar a maioria do estado em um objeto System.Thread gerenciado. Isso inclui o armazenamento local de thread gerenciado e a cultura de interface do usuário do usuário atual do thread. No entanto, para a programação de motivos de modelo, você não poderá alterar a cultura atual de um thread quando você usa SQL; Isso será imposto por meio de uma nova permissão.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Examine o uso de threads e altere seu código adequadamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você não deve suprimir essa regra.



