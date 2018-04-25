---
title: Usando as classes Assert para teste de unidade no Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ff40f25e9beffa848185fe2c1f95df96928543d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="use-the-assert-classes"></a>Usar as classes Assert

Use as classes Assert do namespace UnitTestingFramework para verificar a funcionalidade específica. Um método de teste de unidade executa o código de um método em seu código de desenvolvimento, mas relata a exatidão do comportamento do código somente se você incluir instruções Assert.

## <a name="kinds-of-asserts"></a>Tipos de Assert
 O namespace <xref:Microsoft.VisualStudio.TestTools.UnitTesting> fornece vários tipos de classes Assert:

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 Em seu método de teste, é possível chamar qualquer quantidade de métodos da classe Assert, como Assert.AreEqual(). A classe Assert tem vários métodos disponíveis e muitos desses métodos têm várias sobrecargas.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 Use a classe CollectionAssert para comparar coleções de objetos e verificar o estado de uma ou mais coleções.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 Use a classe StringAssert para comparar cadeias de caracteres. Essa classe contém uma variedade de métodos úteis, como StringAssert.Contains, StringAssert.Matches e StringAssert.StartsWith.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 A exceção AssertFailedException é lançada sempre que um teste falhar. Um teste falhará se expirar, lançar uma exceção inesperada ou contiver uma instrução Assert que produz um resultado com Falha.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 A AssertInconclusiveException será lançada quando um teste produzir um resultado Inconclusivo. Normalmente, uma instrução Assert é adicionada a um teste em que você ainda está trabalhando para indicar que ele ainda não está pronto para ser executado.

> [!NOTE]
>  Uma estratégia alternativa seria marcar um teste que não está pronto para ser executado com o atributo Ignore. No entanto, a desvantagem é que não é fácil gerar um relatório sobre o número de testes que restaram para implementar.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Se você gravar uma nova classe de exceção de Assert, fazer com que essa classe herde da classe base UnitTestAssertException torna mais fácil identificar a exceção como uma falha de asserção em vez de uma exceção inesperada lançada do teste ou código de produção.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Decore um método de teste com o atributo ExpectedExceptionAttribute quando desejar que o método de teste verifique se uma exceção que você espera que seja lançada por um método em seu código de desenvolvimento, de fato, está sendo lançada nesse método.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)
