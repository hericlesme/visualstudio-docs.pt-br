---
title: "Como: impor um código com uma política de Check-in do análise código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7b1a6d953128317e89672d5d9b175ce7acc1b63f
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Como: impor um código com uma política de check-in do analysis código

Os desenvolvedores podem usar a ferramenta de avaliação de código para medir a complexidade e facilidade de manutenção de seu código, mas você não pode invocar as métricas de código como parte de uma política de check-in. No entanto, você pode habilitar as regras de análise de código que verificam a conformidade do seu código com os padrões de métricas de código e impor as regras por meio de políticas de check-in. Para obter mais informações sobre as métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

Você pode habilitar a profundidade de herança, acoplamento de classe, o índice de facilidade de manutenção e regras de complexidade para impor um código por meio de uma política de check-in de análise de código. Todos os quatro essas regras são encontrados na categoria "Regras de facilidade de manutenção" no editor de política de análise de código.

Os administradores de controle de versão do Team Foundation podem adicionar as regras de facilidade de manutenção de análise de código para os requisitos de política de check-in. Esses check-in políticas exigirem que os desenvolvedores executar a análise de código com base em alterações essas regras antes de iniciar um check-in.

## <a name="to-open-the-code-analysis-policy-editor"></a>Para abrir o editor de política de análise de código

1. Em **Team Explorer**, o projeto de equipe, clique **as configurações de projeto de equipe**e, em seguida, clique em **controle de origem**.

     O **controle de origem** caixa de diálogo é exibida.

2. Sobre o **política de Check-in** guia e, em seguida, clique em **adicionar**.

     O **adicionar política de Check-in** caixa de diálogo é exibida.

3. No **política de Check-in** lista, selecione o **análise de código** caixa de seleção e, em seguida, clique em **Okey**.

     O **Editor de política de análise de código** caixa de diálogo é exibida.

## <a name="to-enable-code-analysis-maintainability-rules"></a>Para habilitar regras de facilidade de manutenção de análise de código

1. No **Editor de política de análise de código** caixa de diálogo **configurações de regra**, expanda o **regras de facilidade de manutenção** nó.

2. Marque as caixas de seleção para as seguintes regras:

    -   Profundidade: **CA1501 AvoidExcessiveInheritance** -limite: aviso em mais de 5 níveis de profundidade

    -   Complexidade: **CA1502 AvoidExcessiveComplexity** -limite: aviso em mais de 25

    -   Índice de facilidade de manutenção: **CA1505 AvoidUnmaintainableCode** -limite: aviso em menos de 20

    -   Acoplamento de classes: **CA1506 AvoidExcessiveClassCoupling** -limite: aviso em mais de 80 para uma classe e mais de 30 para um método

    Além disso, se você quiser que uma violação de regra para impedir que uma compilação bem-sucedida, selecione o **tratar aviso como um erro** caixa de seleção ao lado da descrição da regra.

3. Clique em **OK**. A nova política de check-in agora se aplica ao check-ins futuras.

## <a name="see-also"></a>Consulte também

- [Valores de métricas de código](../code-quality/code-metrics-values.md)
- [Criando e usando políticas do check-in de análise de código](../code-quality/creating-and-using-code-analysis-check-in-policies.md)