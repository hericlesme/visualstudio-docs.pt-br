---
title: "Visão geral de supressão de origem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: "40"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f35833df8e84a4e4caba8fd46f8daea8dd5119a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="in-source-suppression-overview"></a>Visão geral de supressão na origem
Supressão na origem é a capacidade para suprimir ou ignorar violações de análise de código em código gerenciado, adicionando o **SuppressMessage** para os segmentos de código que causam a violação de atributo. O **SuppressMessage** é um atributo condicional que é incluído nos metadados do seu assembly de código gerenciado IL somente se o símbolo de compilação CODE_ANALYSIS é definido em tempo de compilação.  
  
 Em C + + CLI, use as macros CA_SUPPRESS_MESSAGE ou CA_GLOBAL_SUPPRESS_MESSAGE no arquivo de cabeçalho, para adicionar o atributo.  
  
 Você não deve usar as supressões do código-fonte em compilações de versão para impedir que os metadados de supressão na origem de envio acidentalmente. Devido ao custo de processamento de supressão de código-fonte, o desempenho do seu aplicativo pode ser degradado, incluindo os metadados de supressão na origem.  
  
> [!NOTE]
>  Você não tem manualmente código esses atributos por conta própria. Para obter mais informações, consulte [como: suprimir avisos usando o Item de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). O item de menu não está disponível para o código C++.  
  
## <a name="suppressmessage-attribute"></a>Atributo SuppressMessage  
 Quando você clica um aviso de análise de código no **lista de erros** e, em seguida, clique em **suprimir mensagem (NS)**, um **SuppressMessage** atributo é adicionado no seu código ou para o arquivo de supressões globais do projeto.  
  
 O **SuppressMessage** atributo tem o seguinte formato:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 Sendo que:  
  
-   **Categoria de regra** -a categoria na qual a regra está definida. Para obter mais informações sobre categorias de regras de análise de código, consulte [análise de código para avisos de código gerenciado](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id de regra** -o identificador da regra. O suporte inclui tanto um nome curto e longo para o identificador de regra. O nome curto é CAXXXX; o nome longo é CAXXXX:FriendlyTypeName.  
  
-   **A justificação** -o texto que é usado para documentar o motivo para suprimir a mensagem.  
  
-   **Id de mensagem** -identificador exclusivo de um problema para cada mensagem.  
  
-   **Escopo** -o destino no qual o aviso está sendo suprimido. Se o destino não for especificado, ele é definido como o destino do atributo. Escopos com suporte incluem o seguinte:  
  
    -   Módulo  
  
    -   Namespace  
  
    -   Recurso  
  
    -   Tipo  
  
    -   Membro  
  
-   **Destino** - um identificador que é usado para especificar o destino no qual o aviso está sendo suprimido. Ele deve conter um nome totalmente qualificado de item.  
  
## <a name="suppressmessage-usage"></a>Uso de SuppressMessage  
 Avisos da análise de código são suprimidos no nível ao qual uma instância do **SuppressMessage** atributo é aplicado. O objetivo desse é acoplar totalmente as informações de supressão no código onde ocorre a violação.  
  
 A forma geral de supressão inclui a categoria de regra e um identificador de regra que contém uma representação legível opcional do nome da regra. Por exemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Se houver motivos de desempenho estrito para minimizar os metadados de supressão na origem, o nome da regra pode ser removido. A categoria de regra e sua ID da regra juntos constituem um identificador de regra suficientemente exclusivo. Por exemplo,  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Esse formato não é recomendado devido a questões de facilidade de manutenção.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Suprimindo várias violações dentro de um corpo de método  
 Atributos só podem ser aplicados a um método e não podem ser inseridos dentro do corpo de método. No entanto, você pode especificar o identificador como a ID de mensagem para distinguir várias ocorrências de uma violação de dentro de um método.  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-csharp[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## <a name="generated-code"></a>Código gerado  
 Compiladores de código gerenciado e algumas ferramentas de terceiros geram código para facilitar o desenvolvimento rápido de código. Código gerado pelo compilador que aparece nos arquivos de origem geralmente é marcado com o **GeneratedCodeAttribute** atributo.  
  
 Você pode escolher se deseja suprimir avisos de análise de código e erros de código gerado. Para obter informações sobre como suprimir esses erros e avisos, consulte [como: suprimir avisos para código gerado pelo](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Observe que a análise de código ignora **GeneratedCodeAttribute** quando ele é aplicado a um assembly ou um único parâmetro. Essas situações ocorrerem raramente.  
  
## <a name="global-level-suppressions"></a>Supressões no nível global  
 A ferramenta de análise de código gerenciado examina **SuppressMessage** atributos aplicados no nível de assembly, módulo, tipo, membro ou parâmetro. Também será acionado violações em relação a recursos e namespaces. Essas violações devem ser aplicadas no nível global no escopo e são direcionadas. Por exemplo, a seguinte mensagem suprime uma violação de namespace:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Quando você suprimir um aviso com escopo de namespace, ele suprime o aviso no namespace em si. Ele não suprime o aviso contra tipos no namespace.  
  
 Qualquer supressão pode ser expresso com a especificação de um escopo explícito. Esses supressões devem residir no nível global. Você não pode especificar a supressão de nível de membro de decoração de um tipo.  
  
 Supressões no nível global são a única maneira de suprimir mensagens que fazem referência ao código gerado pelo compilador que não é mapeado para a origem de usuário fornecido explicitamente. Por exemplo, o código a seguir suprime uma violação em um construtor emitido pelo compilador:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  O destino sempre contém o nome totalmente qualificado de item.  
  
## <a name="global-suppression-file"></a>Arquivo de supressão global  
 O arquivo de supressão global mantém supressões supressões no nível global ou supressões que não especificam um destino. Por exemplo, supressões de violações de nível de assembly são armazenadas nesse arquivo. Além disso, alguns supressões do ASP.NET são armazenadas neste arquivo porque as configurações de nível de projeto não estão disponíveis para o código por trás de um formulário. Uma supressão global é criada e adicionada ao seu projeto na primeira vez que você selecionar o **no arquivo de supressão do projeto** opção do **suprimir mensagem (NS)** comando na janela lista de erros. Para obter mais informações, consulte [como: suprimir avisos usando o Item de Menu](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.CodeAnalysis>