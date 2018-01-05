---
redirect_url: /visualstudio/csharp-ide/refactoring/rename
title: "Renomear a refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 42c5f99b3bf5ba95bc279cd5e117745ccc8e02c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="rename-refactoring-c"></a>Refatoração Renomear (C#)
**Renomear** é um recurso de refatoração no ambiente de desenvolvimento integrado (IDE) do Visual Studio que fornece uma maneira fácil para renomear identificadores para símbolos de código, como campos, variáveis locais, métodos, namespaces, propriedades e tipos. **Renomear** pode ser usado para alterar os nomes em comentários em cadeias de caracteres e para alterar as declarações e chamadas de um identificador.  
  
> [!NOTE]
>  Ao usar o controle de origem para o Visual Studio, obter a versão mais recente das fontes antes de tentar realizar a refatoração de renomeação.  
  
 Refatoração Renomear está disponível dos seguintes recursos do Visual Studio:  
  
|Recurso|Comportamento de refatoração no IDE|  
|-------------|----------------------------------------|  
|Editor de Códigos|No Editor de códigos, refatoração Renomear está disponível quando você posiciona o cursor em determinados tipos de símbolos de código. Quando o cursor está nessa posição, você pode chamar o **Renomear** comando digitando o atalho de teclado (Ctrl + R, Ctrl + R), ou selecionando o **Renomear** comando ações rápidas, o menu de atalho, ou **Refatorar** menu.|  
|Exibição de Classe|Quando você seleciona um identificador na exibição de classe, refatoração Renomear está disponível no menu de atalho e **refatorar** menu.|  
|Pesquisador de Objetos|Quando você seleciona um identificador no Pesquisador de objetos, refatoração Renomear só está disponível na **refatorar** menu.|  
|Grade de propriedade do Designer de formulários do Windows|No **grade de propriedade** do Designer de formulários do Windows, alterando o nome de um controle irá iniciar uma operação de renomeação para o controle. O **Renomear** caixa de diálogo não aparecerá.|  
|Gerenciador de Soluções|Em **Solution Explorer**, um **Renomear** comando está disponível no menu de atalho. Se o arquivo de origem selecionado contém uma classe cujo nome de classe é o mesmo que o nome do arquivo, você pode usar esse comando para renomear o arquivo de origem e execute a refatoração Renomear simultaneamente.<br /><br /> Por exemplo, se você criar um aplicativo baseado no Windows de padrão e, em seguida, renomeie Form1 para TestForm.cs, o nome do arquivo de origem Form1 será alterado para TestForm.cs e a classe Form1 e todas as referências para que a classe será renomeada para TestForm. **Observação:** o **desfazer** comando (CTRL + Z) somente desfazer refatoração Renomear no código e será não alterar o nome do arquivo de volta para o nome original. <br /><br /> Se o arquivo de origem selecionado não contém uma classe cujo nome é o mesmo que o nome do arquivo, o **Renomear** do **Solution Explorer** somente renomeará o arquivo de origem e não executará renomear refatoração.|  
  
## <a name="rename-operations"></a>Operações de renomeação  
 Quando você executar **Renomear**, o mecanismo de refatoração executa um específicos da operação de renomeação de cada símbolo de código, conforme descrito na tabela a seguir.  
  
|Símbolo de código|Operação de renomear|  
|-----------------|----------------------|  
|Campo|Altera a declaração e usos do campo para o novo nome.|  
|variável local|Altera a declaração e usos da variável para o novo nome.|  
|Método|Altera o nome do método e todas as referências a esse método para o novo nome. **Observação:** quando você renomeia um método de extensão, a operação de renomeação se propaga para todas as instâncias do método que estejam no escopo, independentemente se o método de extensão está sendo usado como um método estático ou um método de instância. Para obter mais informações, consulte [Métodos de extensão](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods).|  
|Namespace|Altera o nome do namespace para o novo nome na declaração de todos os `using` instruções e nomes totalmente qualificados. **Observação:** ao renomear um namespace, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também atualiza o **Namespace padrão** propriedade o **aplicativo** página do **Project Designer**. Essa propriedade não pode ser redefinida selecionando **desfazer** do **editar** menu. Para redefinir o **Namespace padrão** valor da propriedade, você deve modificar a propriedade no **Project Designer**. Para obter mais informações, consulte [página de aplicativo](../ide/reference/application-page-project-designer-csharp.md).|  
|Propriedade|Altera a declaração e usos da propriedade para o novo nome.|  
|Tipo|Altera todas as declarações e todos os usos do tipo para o novo nome, incluindo construtores e destruidores. Para tipos parciais, a operação de renomeação serão propagadas para todas as partes.|  
  
#### <a name="to-rename-an-identifier"></a>Para renomear um identificador  
  
1.  Criar um aplicativo de console chamado `RenameIdentifier`e, em seguida, substitua `Program` com o código de exemplo a seguir.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Coloque o cursor na `MethodB`, na declaração de método ou a chamada do método.  
  
3.  Do **refatorar** menu, selecione **Renomear**. O **Renomear** caixa de diálogo é exibida.  
  
     Você pode também clique o cursor, aponte para **refatorar** no menu de contexto e depois clique em **Renomear** para exibir o **Renomear** caixa de diálogo.  
  
4.  No **novo nome** , digite `MethodC`.  
  
5.  Selecione o **pesquisa nos comentários** caixa de seleção.  
  
6.  Clique em **OK**.  
  
7.  No **visualizar alterações** caixa de diálogo, clique em **aplicar**.  
  
#### <a name="to-rename-an-identifier-using-quick-actions"></a>Para renomear um identificador usando ações rápidas  
  
1.  Criar um aplicativo de console chamado `RenameIdentifier`e, em seguida, substitua `Program` com o código de exemplo a seguir.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Na declaração de `MethodB`, tipo ou a tecla backspace sobre o identificador do método. Uma lâmpada ações rápidas será exibido na margem.  
  
    > [!NOTE]
    >  Você só pode invocar refatoração Renomear usando ações rápidas da declaração de um identificador.  
  
3.  Digite o atalho de teclado **Alt + Shift + F10** para exibir o menu de ações rápidas.  
  
     -ou-  
  
     Clique no triângulo preto ao lado de lâmpada para exibir o menu de ações rápidas.  
  
4.  Selecione o **renomear '\<identifer1 >' para '\<identifier2 >'** item de menu para invocar refatoração Renomear. Todas as referências a  **\<identifer1 >** serão atualizados automaticamente para  **\<identifier2 >**.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="renaming-implemented-or-overridden-members"></a>Renomeando implementado ou membros substituídos  
 Quando você **Renomear** um membro que implementa/substituições ou é implementado/substituído por membros em outros tipos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] exibe uma caixa de diálogo que diz que a operação de renomeação fará com que as atualizações em cascata. Se você clicar em **continuar**, a refatoração recursivamente mecanismo localiza e renomeia todos os membros na base de dados e tipos derivados que têm implementa/substituições relações com o membro que está sendo renomeado.  
  
 O exemplo de código a seguir contém membros com relações implementa/substituições.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../csharp-ide/codesnippet/CSharp/rename-refactoring-csharp_1.cs)]  
  
 No exemplo anterior, renomeando `C.Method()` também renomeia `Ibase.Method()` porque `C.Method()` implementa `Ibase.Method()`. Em seguida, o mecanismo de forma recursiva refatorar vê que `Ibase.Method()` é implementado por `Derived.Method()` e renomeia `Derived.Method()`. O mecanismo de refatoração Renomear não `Base.Method()`, pois `Derived.Method()` não substitui `Base.Method()`. O mecanismo de refatoração aqui interrompe a menos que você tenha **Renomear sobrecargas** check-in a **Renomear** caixa de diálogo.  
  
 Se **Renomear sobrecargas** estiver marcada, o mecanismo de refatoração renomeia `Derived.Method(int i)` porque sobrecarrega `Derived.Method()`, `Base.Method(int i)` porque ele é substituído pelo `Derived.Method(int i)`, e `Base.Method()` porque é uma sobrecarga `Base.Method(int i)`.  
  
> [!NOTE]
>  Quando você renomeia um membro que foi definido em um assembly referenciado, uma caixa de diálogo explica que a renomeação causará erros de compilação.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Renomear as propriedades de tipos anônimos  
 Quando você renomeia uma propriedade em tipos anônimos, a operação de renomeação serão propagadas às propriedades de outros tipos anônimos que têm as mesmas propriedades. Os exemplos a seguir ilustram esse comportamento.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 No código anterior, renomeando `ID` alterará `ID` em ambas as instruções porque eles têm o mesmo tipo anônimo subjacente.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 No código anterior, renomeando `ID` renomeará apenas uma instância de `ID` porque `companyIDs` e `orderIDs` não têm as mesmas propriedades.  
  
## <a name="see-also"></a>Consulte também  
 [Refatoração (C#)](refactoring-csharp.md)   
 [Tipos Anônimos](/dotnet/csharp/programming-guide/classes-and-structs/anonymous-types)