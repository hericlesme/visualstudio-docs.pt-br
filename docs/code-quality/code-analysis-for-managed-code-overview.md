---
title: Análise de código para código gerenciado no Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b7b992dadb703cf1c4f73830324e9934d7525645
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-code-analysis-for-managed-code"></a>Visão geral da análise de código para código gerenciado

2017 do Visual Studio analisa o código gerenciado de duas maneiras: com herdado *FxCop* análise estática de assemblies gerenciados e com a plataforma de compilador .NET *analisadores*. Este tópico aborda a análise de código estático do FxCop. Para saber mais sobre a análise de código usando analisadores de plataforma de compilador do .NET, consulte [analisadores de visão geral do Roslyn](../code-quality/roslyn-analyzers-overview.md).

Análise de código para código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações de programação e regras de design definidas as diretrizes de Design do Microsoft .NET Framework.

A ferramenta de análise representa as verificações de desempenho durante uma análise como mensagens de aviso. Mensagens de aviso identificam quaisquer problemas de programação e design relevantes e, quando for possíveis, forneça informações sobre como corrigir o problema.

## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)

Você pode executar a análise de código no seu projeto automaticamente ou manualmente.

Para executar a análise de código sempre que você compilar um projeto, selecione **habilitar análise de código no Build** na página de propriedades do projeto. Para obter mais informações, consulte [como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para executar a análise de código manualmente em um projeto, na barra de menus, escolha **analisar** > **executar análise de código** > **executar análise de código em \<projeto >**.

## <a name="rule-sets"></a>Conjuntos de regras

Regras de análise de código para código gerenciado são agrupadas em [conjuntos de regras](../code-quality/using-rule-sets-to-group-code-analysis-rules.md). Você pode usar um dos conjuntos de regra padrão Microsoft, ou você pode [criar um conjunto de regras personalizado](../code-quality/how-to-create-a-custom-rule-set.md) para atender uma necessidade específica.

## <a name="suppress-warnings"></a>Suprimir avisos

Normalmente, é útil indicar que um aviso é não aplicável. Isso informará o desenvolvedor e outras pessoas que podem analisar o código mais tarde, que um aviso foi investigado e suprimido ou ignorado.

A supressão de avisos na origem é implementada por meio de atributos personalizados. Para suprimir um aviso, adicione o atributo `SuppressMessage` para o código-fonte conforme mostrado no exemplo a seguir:

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

Para obter mais informações, consulte [suprimir avisos](../code-quality/in-source-suppression-overview.md).

> [!NOTE]
> Se você migrar um projeto para Visual Studio de 2017, você pode encontrar repentinamente com um grande número de avisos da análise de código. Se você não estiver pronto para corrigir os avisos e deseja que se torne produtivo imediatamente, você pode *baseline* o estado de análise de seu projeto. Do **analisar** menu, selecione **executar análise de código e suprimir problemas ativos**.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in

Como uma organização, você talvez queira exigem que todos os check-ins satisfazer certas políticas. Em particular, você deseja certificar-se de que você siga essas políticas:

- Não há nenhum erro de compilação no código que está sendo feito check-in.

- Análise de código é executada como parte da compilação mais recente.

Você pode fazer isso especificando políticas de check-in. Para obter mais informações, consulte [melhorando a qualidade do código com políticas de Check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integração do Team build

Você pode usar os recursos integrados de sistema de compilação para executar a ferramenta de análise como parte do processo de compilação. Para obter mais informações, consulte [Build e versão (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Consulte também

- [Visão geral dos analisadores de Roslyn](../code-quality/roslyn-analyzers-overview.md)
- [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
