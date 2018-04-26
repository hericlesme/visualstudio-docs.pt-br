---
title: 'CA2153: Evitar tratamento de exceções de estado corrompidas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ca36093afa0915352c6c6d90995bde99fb655c8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar tratamento de exceções de estado corrompidas

|||
|-|-|
|NomeDoTipo|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Categoria|Microsoft.Security|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa

[Corrompido exceções de estado (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indicar que a memória corrompidos no processo. Capturando esses em vez de permitir o processo a falha pode levar a vulnerabilidades de segurança se um invasor pode colocar uma exploração para a área de memória corrompidos.

## <a name="rule-description"></a>Descrição da Regra
 CSE indica que o estado de um processo foi corrompido e não foi detectado pelo sistema. No cenário de estado corrompido, um manipulador geral somente captura a exceção se você marcar o método com o próprio `HandleProcessCorruptedStateExceptions` atributo. Por padrão, o [Common Language Runtime (CLR)](/dotnet/standard/clr) não invoca manipuladores catch para CSEs.

 Permitir que o processo falhar sem capturando esses tipos de exceção é a opção mais segura, como o mesmo código de registro pode permitir que os invasores podem explorar bugs de corrupção de memória.

 Esse aviso é disparado quando capturando CSEs com um manipulador geral que captura todas as exceções, como catch(exception) ou catch (especificação de exceção).

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para resolver este aviso, você deve fazer o seguinte:

 1. Remover o `HandleProcessCorruptedStateExceptions` atributo. Isso será revertido para o comportamento de tempo de execução padrão onde CSEs não são passados para manipuladores catch.

 2. Remova o manipulador catch geral in preference of manipuladores que capturar tipos de exceção específica.  Isso pode incluir CSEs supondo que o código do manipulador possa gerenciá-las com segurança (muito raro).

 3. Gera novamente a CSE no manipulador catch que garante a exceção é passada para o chamador e resultará no encerramento do processo em execução.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="pseudo-code-example"></a>Exemplo de código pseudo

### <a name="violation"></a>Violação
 O pseudocódigo a seguir ilustra o padrão detectado por essa regra.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Solução 1
 Removendo o atributo HandleProcessCorruptedExceptions garante que as exceções não ocorrerão.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Solução 2
 Remova o manipulador catch geral e capturar somente os tipos de exceção específica.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Solução 3
 Gera novamente a exceção.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```