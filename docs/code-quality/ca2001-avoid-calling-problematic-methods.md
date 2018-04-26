---
title: 'CA2001: evitar métodos problemáticos de chamada'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc40f51fc0c5c3e2db428252d466760d9f297e23
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: evitar métodos problemáticos de chamada
|||
|-|-|
|NomeDoTipo|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Categoria|Microsoft.Reliability|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Um membro chama um método potencialmente perigoso ou problemático.

## <a name="rule-description"></a>Descrição da Regra
 Evite fazer chamadas de método desnecessários e potencialmente perigosos.

 Uma violação desta regra ocorre quando um membro chama um dos métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Chamar GC. Coletar pode afetar significativamente o desempenho do aplicativo e raramente é necessário. Para obter mais informações, consulte o [dados sobre o desempenho de Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) entrada de blog no MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e thread. resume foram substituídos por causa de seu comportamento imprevisível.  Usar outras classes de <xref:System.Threading> namespace, como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, e <xref:System.Threading.Semaphore> para sincronizar threads ou proteger os recursos.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|O método DangerousGetHandle representa um risco de segurança porque ele pode retornar um identificador que não é válido. Consulte o <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> e <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> métodos para obter mais informações sobre como usar o método DangerousGetHandle com segurança.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Esses métodos podem carregar assemblies de locais inesperados. Por exemplo, consulte as postagens no blog do Suzanne Cook .NET CLR notas [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [escolhendo um contexto de associação](http://go.microsoft.com/fwlink/?LinkId=164451) no site do MSDN para obter informações sobre os métodos que carregar assemblies.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Quando o código de usuário inicia a execução em um processo gerenciado, é muito tarde confiável chamar CoSetProxyBlanket. O common language runtime (CLR) executa ações de inicialização que podem impedir que os usuários P/Invoke bem-sucedida.<br /><br /> Se você precisar chamar CoSetProxyBlanket para um aplicativo gerenciado, é recomendável que você iniciar o processo por meio de um executável de código nativo (C++), chamar CoSetProxyBlanket no código nativo e inicie seu aplicativo de código gerenciado no processo. (Certifique-se de especificar um número de versão de tempo de execução.)|

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova ou substitua a chamada ao método perigoso ou problemática.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você deve suprimir mensagens dessa regra somente quando nenhum alternativas para o método problemático estão disponíveis.

## <a name="see-also"></a>Consulte também
 [Avisos de confiabilidade](../code-quality/reliability-warnings.md)