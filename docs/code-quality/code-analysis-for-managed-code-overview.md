---
title: "Análise de código para visão geral de código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d30f84194ef7a48de106698c9ad4569e947923c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="code-analysis-for-managed-code-overview"></a>Análise de código para visão geral de código gerenciado

Análise de código para código gerenciado analisa os assemblies gerenciados e relata informações sobre assemblies, como violações de programação e regras de design definidas as diretrizes de Design do Microsoft .NET Framework.

A ferramenta de análise representa as verificações de desempenho durante uma análise como mensagens de aviso. Mensagens de aviso identificam quaisquer problemas de programação e design relevantes e, quando for possíveis, forneça informações sobre como corrigir o problema.

## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)

Você pode executar a análise de código no seu projeto automaticamente ou manualmente.

Para executar a análise de código sempre que você compilar um projeto, selecione **habilitar análise de código no Build** na página de propriedades do projeto. Para obter mais informações, consulte [como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

Para executar a análise de código manualmente em um projeto, na barra de menus, escolha **analisar** > **executar análise de código** > **executar análise de código em <project>** . Para obter mais informações, consulte [como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Conjuntos de regras

Regras de análise de código para código gerenciado são agrupadas em *conjuntos de regras*. Você pode usar um dos conjuntos de regra padrão Microsoft, ou você pode criar uma regra personalizada definida para atender uma necessidade específica. Para obter mais informações, consulte [usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

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
> Se você migrar um projeto para Visual Studio de 2017, você pode encontrar repentinamente com um número excessivo de avisos da análise de código. Se você não estiver pronto para corrigir os avisos e deseja desativar temporariamente a análise de código, abra as páginas de propriedades do projeto (**projeto** > ***projeto* propriedades...** ) e vá para o **análise de código** guia. Desmarque **habilitar análise de código no Build**e, em seguida, recrie seu projeto. Como alternativa, você pode selecionar uma regra diferente, menor definida para ser executado com o código. Lembre-se de ativar a análise de código em quando estiver pronto para corrigir os avisos.

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Executar análise de código como parte da política de check-in

Como uma organização, você talvez queira exigem que todos os check-ins satisfazer certas políticas. Em particular, você deseja certificar-se de que você siga essas políticas:

- Não há nenhum erro de compilação no código que está sendo feito check-in.

- Análise de código é executada como parte da compilação mais recente.

Você pode fazer isso especificando políticas de check-in. Para obter mais informações, consulte [melhorando a qualidade do código com políticas de Check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integração do Team build

Você pode usar os recursos integrados de sistema de compilação para executar a ferramenta de análise como parte do processo de compilação. Para obter mais informações, consulte [Build e versão (VSTS)](/vsts/build-release/index).

## <a name="see-also"></a>Consulte também

[Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[Como: habilitar e desabilitar análise de código automática](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
