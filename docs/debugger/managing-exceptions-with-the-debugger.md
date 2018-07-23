---
title: Gerenciar exceções com o depurador do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c514458d6b7e8cfd4837ca907d14055af8a624ce
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180212"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Gerenciar exceções com o depurador do Visual Studio

Uma exceção é uma indicação de um estado de erro que ocorre enquanto um programa está sendo executado. Você pode instruir o depurador quais exceções (ou conjuntos de exceções) para interromper no e no ponto em que você deseja que o depurador seja interrompido (quando o depurador for interrompido, ele mostra onde a exceção foi lançada). Você também pode adicionar ou excluir exceções. Com uma solução aberta no Visual Studio, use **Depurar > Windows > configurações de exceção** para abrir o **configurações de exceção** janela. 

Você pode e deve fornecer manipuladores que respondem às exceções mais importantes, mas é importante saber como configurar o depurador para interromper a execução de algumas exceções sempre.
  
Quando uma exceção ocorre, o depurador grava uma mensagem de exceção para a janela de saída. Ele pode interromper a execução nos seguintes casos:  
  
-   Quando uma exceção é lançada e não é tratada.  
  
-   Quando o depurador está configurado para interromper a execução antes que qualquer manipulador seja invocado.  
  
-   Se você tiver definido [Just My Code](../debugger/just-my-code.md), e o depurador está configurado para interromper qualquer exceção que não é tratada no código do usuário.  
  
> [!NOTE]
>  O ASP.NET tem um manipulador de exceção de nível superior que mostra páginas de erro em um navegador. Ele não interromper a execução, a menos que **Just My Code** está ativado. Por exemplo, consulte [definindo o depurador para continuar em exceções sem tratamento do usuário](../debugger/managing-exceptions-with-the-debugger.md#BKMK_UserUnhandled) abaixo.  
  
> [!NOTE]
>  Em um aplicativo Visual Basic, o depurador gerencia todos os erros como exceções, mesmo se você usar em manipuladores de erro de estilo de erro.    
  
## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Instruir o depurador para interromper quando uma exceção é lançada  
O depurador pode interromper a execução no ponto em que uma exceção é lançada, dando a você a oportunidade de examinar a exceção antes de um manipulador é invocado.  
  
No **configurações de exceção** janela (**Depurar > Windows > configurações de exceção**), expanda o nó para uma categoria de exceções (por exemplo, **exceções Common Language Runtime**, que significa que as exceções .NET) e marque a caixa de seleção para uma exceção específica dentro dessa categoria (por exemplo **System. AccessViolationException**). Você também pode selecionar uma categoria inteira de exceções.  
  
![Checked AccessViolationException](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")  

> [!TIP]
> Você pode encontrar exceções específicas usando o **pesquisa** janela na **configurações de exceção** barra de ferramentas, ou usar Pesquisar para filtrar para namespaces específicos (por exemplo **System.IO**).
  
Se você selecionar uma exceção na **configurações de exceção** janela, a execução do depurador interromperá sempre que a exceção é lançada, independentemente se ele é tratado ou sem tratamento. Neste ponto, a exceção é chamada uma exceção de primeira chance. Por exemplo, aqui estão alguns cenários:  
  
*  O seguinte c# aplicativo de console, o método Main lança um **AccessViolationException** dentro de um `try/catch` bloco:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        try  
        {  
            throw new AccessViolationException();  
            Console.WriteLine("here");  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("caught exception");  
        }  
        Console.WriteLine("goodbye");  
    }  
    ```  
  
     Se você tiver **AccessViolationException** check-in **configurações de exceção**, quando você executa esse código na execução do depurador será interrompido no `throw` linha. Em seguida, você pode continuar a execução. O console deverá exibir as duas linhas:  
  
    ```cmd
    caught exception  
    goodbye  
    ```  
  
     mas ele não exibe o `here` linha.  
  
*  Um aplicativo de console c# faz referência a uma biblioteca de classes com uma classe que tem dois métodos, um método que lança uma exceção e lida com isso e um segundo método que gera a mesma exceção e não tratá-la:  
  
    ```csharp 
    public class Class1  
    {  
        public void ThrowHandledException()  
        {  
            try  
            {  
                throw new AccessViolationException();  
            }  
            catch (AccessViolationException ave)  
            {  
                Console.WriteLine("caught exception" + ave.Message);  
            }  
        }  
  
        public void ThrowUnhandledException()  
        {  
            throw new AccessViolationException();  
        }  
    }  
    ```  
  
     Aqui está o método Main () do aplicativo de console:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Class1 class1 = new Class1();  
        class1.ThrowHandledException();  
        class1.ThrowUnhandledException();  
    }  
    ```  
  
     Se você tiver **AccessViolationException** check-in **configurações de exceção**, quando você executa esse código na execução do depurador será interrompido no `throw` linha em ambos os  **ThrowHandledException()** e **ThrowUnhandledException()**.  
  
 Se você quiser restaurar as configurações de exceção para os padrões, você pode clicar na **restaurar** na barra de ferramentas:  
  
 ![Restaurar padrões nas configurações de exceção](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")  
  
##  <a name="BKMK_UserUnhandled"></a> Instruir o depurador para continuar em exceções sem tratamento do usuário  
 Se você estiver depurando código do .NET ou JavaScript com [Just My Code](../debugger/just-my-code.md), você pode instruir o depurador não para interromper as exceções que não são manipuladas no código do usuário, mas são tratadas em outro lugar.  
  
1.  No **configurações de exceção** janela, abra o menu de contexto clicando duas vezes na janela e, em seguida, selecionando **Mostrar colunas**. (Se você tiver desativado **Just My Code**, você não verá esse comando.)  
  
2.  Você deve ver uma segunda coluna chamada **ações adicionais**. Esta coluna exibe **continuar quando não for tratado pelo código do usuário** sobre exceções específicas, o que significa que o depurador não é interrompido se essa exceção não é tratada no código do usuário, mas é tratada no código externo.  
  
3.  Você pode alterar essa configuração para uma determinada exceção (selecione a exceção botão direito do mouse e selecionar/anular seleção **continuar quando não for tratado no código do usuário**) ou para uma categoria inteira de exceções (por exemplo, todas as comuns Exceções de tempo de execução de linguagem).  
  
 Por exemplo, aplicativos web ASP.NET manipulam exceções convertendo-os em um código de status HTTP 500 ([tratamento de exceções em API ASP.NET](http://www.asp.net/web-api/overview/error-handling/exception-handling)), que não podem ajudá-lo a determinar a origem da exceção. No exemplo a seguir, o código do usuário faz uma chamada para `String.Format()` que gera um <xref:System.FormatException>. Execução quebra da seguinte maneira:  
  
 ![quebra no usuário&#45;exceção unhanlded](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")  
  
## <a name="add-and-delete-exceptions"></a>Adicionar e excluir exceções  
 Você pode adicionar e excluir exceções. Você pode excluir qualquer tipo de exceção de qualquer categoria selecionando a exceção e clicando na **exclua** botão (o sinal de subtração) o **configurações de exceção** barra de ferramentas ou clicando duas vezes a exceção e selecionando **excluir** no menu de contexto. Excluir uma exceção tem o mesmo efeito que ter a exceção não verificada, que é que o depurador não será interrompido quando ela é gerada.  
  
 Para adicionar uma exceção: na **configurações de exceção** janela, selecione uma das categorias de exceção (por exemplo, **Common Language Runtime**) e clique no **Add** botão. Digite o nome da exceção (por exemplo. **System.UriTemplateMatchException**). A exceção é adicionada à lista (em ordem alfabética) e é marcada automaticamente.  
  
 Se você quiser adicionar uma exceção para as exceções de acesso de memória de GPU, exceções de tempo de execução do JavaScript ou categorias de exceções do Win32, você precisa incluir o código de erro, bem como a descrição.  
  
> [!TIP]
>  Verifique a ortografia! O **configurações de exceção** janela não verifica a existência de uma exceção adicionada. Portanto, se você digitar **Sytem.UriTemplateMatchException**, você obterá uma entrada para essa exceção (e não para **System.UriTemplateMatchException**).  
  
 Configurações de exceção são persistidas no arquivo. suo da solução, para que elas se aplicam a uma determinada solução. É possível reutilizar configurações de exceção específicos em soluções. Neste ponto, apenas as exceções adicionadas são persistentes; não são excluídos de exceções. Em outras palavras, você pode adicionar uma exceção, feche e reabra a solução e a exceção ainda estará lá. Mas se você excluir uma exceção e fechar/reabrir a solução, a exceção reaparecerá.  
  
 O **configurações de exceção** janela dá suporte a tipos de exceção genérica em c#, mas não no Visual Basic. Para interromper as exceções, como `MyNamespace.GenericException<T>`, você deve adicionar a exceção como **MyNamespace.GenericException'1**. Ou seja, se você tiver criado uma exceção como este:  
  
```csharp  
public class GenericException<T> : Exception  
{  
    public GenericException() : base("This is a generic exception.")  
    {  
    }  
}  
```  
  
 Você pode adicionar a exceção **configurações de exceção** semelhante a esta:  
  
 ![Adicionar exceção genérica](../debugger/media/addgenericexception.png "AddGenericException")  

## <a name="add-conditions-to-an-exception"></a>Adicionar condições a uma exceção

Você pode definir condições de exceções na **configurações de exceção** caixa de diálogo. Condições com suporte no momento incluem os nomes de módulo para incluir ou excluir da exceção. Ao definir nomes de módulo como condições, você pode optar por interromper a exceção apenas em módulos de código específico, ou você pode evitar a quebra de módulos específicos.

> [!NOTE]
> Adicionar condições a uma exceção é nova no [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]

Para adicionar exceções condicionais, escolha o **Editar condição** ícone na caixa de diálogo Configurações de exceção caixa ou a exceção botão direito do mouse e escolha **editar condições**.

![Condições em uma exceção](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")
  
## <a name="see-also"></a>Consulte também  
 [Continuando a execução após uma exceção](../debugger/continuing-execution-after-an-exception.md)   
 [Como: examinar o código do sistema após uma exceção](../debugger/how-to-examine-system-code-after-an-exception.md)   
 [Como: usar verificações de tempo de execução nativas](../debugger/how-to-use-native-run-time-checks.md)   
 [Usar o tempo de execução verifica sem a biblioteca de tempo de execução C](../debugger/using-run-time-checks-without-the-c-run-time-library.md)   
 [Noções básicas do depurador](../debugger/getting-started-with-the-debugger.md)
