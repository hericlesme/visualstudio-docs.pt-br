---
title: "Criar stubs de método de teste de unidade com o comando Criar Testes de Unidade | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9016006f9774c4a9eff2937f32543b9f8d9f5fb8
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-microsoft-intellitest"></a>Introdução ao Microsoft IntelliTest

* Se esta for a primeira vez que você trabalha com o IntelliTest:
  * assista ao [vídeo do Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * leia esta [visão geral na MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * leia nossa [documentação](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Fazer perguntas sobre [Stack Overflow](http://stackoverflow.com/questions/tagged/intellitest)
* Leia o restante deste manual de referência
* Imprima esta página para referência rápida

## <a name="important-attributes"></a>Atributos importantes

* [PexClass](attribute-glossary.md#pexclass) marca um tipo que contém **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) marca um **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) marca um parâmetro não nulo

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) associa um projeto de teste a um projeto
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) especifica um assembly para instrumentar

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a> Classes auxiliares estáticas importantes

* [PexAssume](static-helper-classes.md#pexassume) avalia suposições (filtragem de entrada)
* [PexAssert](static-helper-classes.md#pexassert) avalia declarações
* [PexChoose](static-helper-classes.md#pexchoose) gera novas opções (entradas adicionais)
* [PexObserve](static-helper-classes.md#pexobserve) registra valores dinâmicos para os testes gerados

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Recebeu comentários?

Poste suas ideias e solicitações de recursos em [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).
