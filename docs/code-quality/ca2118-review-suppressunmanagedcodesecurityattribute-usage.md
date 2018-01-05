---
title: 'CA2118: Revisar uso de SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a6c5e60ed84a79e6e81d4cd066d75b1270bdb71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: revisar uso de SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|NomeDoTipo|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## <a name="cause"></a>Causa  
 Um tipo público ou protegido ou membro tem o <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> atributo.  
  
## <a name="rule-description"></a>Descrição da Regra  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>Altera o comportamento do sistema de segurança padrão para os membros que execute o código não gerenciado usando invocação de plataforma ou interoperabilidade COM. Em geral, o sistema faz uma [dados e modelagem](/dotnet/framework/data/index) para permissão de código não gerenciado. Essa demanda ocorre em tempo de execução para cada invocação do membro e verifica se todos os chamadores na pilha de chamadas para a permissão. Quando o atributo estiver presente, o sistema faz uma [demandas de Link](/dotnet/framework/misc/link-demands) para a permissão: as permissões do chamador imediato são verificadas quando o chamador é a compilação JIT.  
  
 Esse atributo é usado principalmente para aumentar o desempenho; no entanto, os ganhos de desempenho acompanham riscos de segurança significativos. Se você colocar o atributo em membros públicos que chamam métodos nativos, os chamadores na pilha de chamadas (que não seja o chamador imediato) não precisa de permissão de código não gerenciado para executar código não gerenciado. Dependendo do membro público ações e manipulação de entrada, ele pode permitir que chamadores não confiáveis para a funcionalidade de acesso restringido normalmente ao código confiável.  
  
 O [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] se baseia em verificações de segurança para impedir que os chamadores tenham acesso direto ao espaço de endereço do processo atual. Como esse atributo ignora normais de segurança, o seu código representa uma ameaça grave se ele pode ser usado para ler ou gravar em memória do processo. Observe que o risco não está limitado a métodos que intencionalmente fornecem acesso para processar memória; Ele também está presente em qualquer cenário em que um código mal-intencionado pode obter acesso por qualquer meio, por exemplo, fornecendo entrada surpreendente, malformada ou inválida.  
  
 A política de segurança padrão não conceder permissão de código não gerenciado a um assembly, a menos que ele está em execução no computador local ou um membro de um dos seguintes grupos:  
  
-   Grupo de códigos de zona Meu computador  
  
-   Grupo de códigos do Microsoft forte nome  
  
-   Grupo de códigos de nome de alta segurança ECMA  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Leia com atenção o seu código para garantir que esse atributo é absolutamente necessário. Se você não estiver familiarizado com a segurança de código gerenciado ou não entende as implicações de segurança de usar esse atributo, removê-lo do seu código. Se o atributo é necessário, você deve garantir que os chamadores não é possível usar seu código maliciosamente. Se seu código não tem permissão para executar código não gerenciado, esse atributo não tem nenhum efeito e deve ser removido.  
  
## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos  
 Para suprimir com segurança um aviso dessa regra, você deve garantir que seu código não fornece os chamadores acessem operações nativo ou recursos que podem ser usados de forma destrutivas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir viola a regra.  
  
 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `DoWork` método fornece um caminho de código publicamente acessível para o método de invocação de plataforma `FormatHardDisk`.  
  
 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o método público `DoDangerousThing` faz com que uma violação. Para resolver a violação, `DoDangerousThing` devem ser feitas em particular, e o acesso a ele deve ser por meio de um método público protegido por uma exigência de segurança, conforme ilustrado pelo `DoWork` método.  
  
 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)   
 [Dados e modelagem](/dotnet/framework/data/index)  
 [Demandas de link](/dotnet/framework/misc/link-demands)  
  