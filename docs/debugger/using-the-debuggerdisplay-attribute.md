---
title: Usando o atributo DebuggerDisplay | Microsoft Docs
ms.custom: 
ms.date: 08/09/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 11770efcc517b9ec713656f540d75b0a2c412ae7
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2018
---
# <a name="using-the-debuggerdisplay-attribute"></a>Usando o atributo DebuggerDisplay
O [classe DebuggerDisplayAttribute](/dotnet/api/system.diagnostics.debuggerdisplayattribute) controla como um objeto, propriedade ou campo é exibido nas janelas de variáveis do depurador. Esse atributo pode ser aplicado aos tipos delegados, propriedades, campos e assemblies.  
  
 O atributo `DebuggerDisplay` tem um único argumento, que é uma cadeia de caracteres a ser exibida na coluna de valor para instâncias do tipo. Essa cadeia de caracteres pode conter chaves (`{` e `}`). Texto dentro de um par de chaves é avaliado como um campo, propriedade ou método.  
  
 Se uma classe tiver um substituído `ToString()` método, o depurador usa o método substituído em vez do padrão `{<typeName>}`. Portanto, se você tiver substituído o `ToString()` método, o depurador usa o método substituído em vez do padrão`{<typeName>}`, e você não precisa usar `DebuggerDisplay`. Se você usar ambos, o `DebuggerDisplay` atributo tem precedência sobre substituído `ToString()` método.  
  
 Se o depurador avalia nesse implícita `ToString()` chamada depende de uma configuração de usuário no **Ferramentas / opções / depuração** caixa de diálogo. O Visual Basic não implementa esta avaliação de `ToString()` implícita.  
  
> [!IMPORTANT]
>  Se o **Mostrar estrutura bruta de objetos nas janelas de variáveis** caixa de seleção é marcada no **Ferramentas/opções / depuração** caixa de diálogo, em seguida, o `DebuggerDisplay` atributo é ignorado.  
  
 A tabela a seguir mostra alguns usos possíveis do atributo `DebuggerDisplay` e saídas de exemplo.  
  
|Atributo|Saída que aparecem na coluna de valor|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Usado em um tipo com campos `x` e `y`.|`x = 5 y = 18`|  
|A sintaxe do parâmetro `[DebuggerDisplay("String value is {getString()}")]`pode variar entre linguagens. Em virtude disso, use com cuidado.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` também pode aceitar parâmetros nomeados.  
  
|Parâmetros|Finalidade|  
|----------------|-------------|  
|`Name`, `Type`|Esses parâmetros afetam o **nome** e **tipo** colunas das janelas de variável. (Podem ser definidos como cadeias de caracteres usando a mesma sintaxe que o construtor.) Usar esses parâmetros demais ou usá-los incorretamente pode causar uma saída confusa.|  
|`Target`, `TargetTypeName`|Especifica o tipo de destino quando o atributo é usado no nível de assembly.|  
  
 O arquivo de autoexp.cs usa o atributo DebuggerDisplay no nível de assembly. O arquivo autoexp.cs determina as expansões padrão que usa o Visual Studio para objetos do .NET Framework. Você pode examinar o arquivo autoexp.cs para obter exemplos de como usar o atributo DebuggerDisplay, ou você pode modificar e compilar o arquivo autoexp.cs para alterar as expansões padrão. Faça backup do arquivo autoexp.cs antes de modificá-lo.  
  
 Para criar autoexp.cs, abra o backup de um Prompt de comando do desenvolvedor para VS2015 e execute os seguintes comandos  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 As alterações autoexp.dll serão escolhidas na próxima sessão de depuração.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Usando expressões em DebuggerDisplay  
 Embora você possa usar uma expressão geral entre as chaves em um atributo DebuggerDisplay, esta prática não é recomendada.  
  
 Uma expressão geral em DebuggerDisplay tem acesso implícito ao ponteiro `this` somente para a instância atual do tipo de destino. A expressão não tem acesso a alias, locais ou ponteiros. Se a expressão fizer referência a propriedades, os atributos nessas propriedades não serão processados. Por exemplo, o código c# `[DebuggerDisplay("Object {count - 2}")]` exibiria `Object 6` se o campo `count` foi 8.  
  
 Usar expressões em DebuggerDisplay pode resultar nos seguintes problemas:  
  
-   Avaliar expressões é a operação mais cara no depurador e a expressão é avaliada toda vez que é exibida. Isso pode causar problemas de desempenho ao depurar o código. Por exemplo, uma expressão complexa que é usada para exibir os valores em uma coleção ou lista poderá ser muito lenta quando o número de elementos for grande.  
  
-   As expressões são avaliadas pelo avaliador de expressão da linguagem do quadro de pilhas atual e não pelo avaliador da linguagem na qual a expressão foi gravada. Isso pode causar resultados imprevisíveis quando as linguagens são diferentes.  
  
-   Avaliar uma expressão pode alterar o estado do aplicativo. Por exemplo, uma expressão que define o valor de uma propriedade transforma o valor da propriedade no código de execução.  
  
 Uma maneira de reduzir os possíveis problemas de avaliação da expressão é criando uma propriedade privada que executa a operação e retorna uma cadeia de caracteres. O atributo DebuggerDisplay pode em seguida exibir o valor dessa propriedade privada. O exemplo a seguir implementa esse padrão:  
  
```csharp  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
public sealed class MyClass   
{      
    public int count { get; set; }      
    public bool flag { get; set; }      
    private string DebuggerDisplay  
   {         
        get  
        {  
             return string.Format("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar `DebuggerDisplay` junto com `DebuggerBrowseable` e `DebuggerTypeProxy`. Quando exibido em uma janela de variáveis do depurador, como o **inspecionar** janela, ela produz uma expansão parecida com esta:  
  
|**Nome**|**Value**|**Tipo**|  
|--------------|---------------|--------------|  
|Chave|"three"|object {string}|  
|Valor|3|object {int}|  
  
```csharp  
[DebuggerDisplay("{value}", Name = "{key}")]  
internal class KeyValuePairs  
{  
    private IDictionary dictionary;  
    private object key;  
    private object value;  
    public KeyValuePairs(IDictionary dictionary, object key, object value)  
    {  
        this.value = value;  
        this.key = key;  
        this.dictionary = dictionary;  
    }  
  
    public object Key  
    {  
        get { return key; }  
        set  
        {  
            object tempValue = dictionary[key];  
            dictionary.Remove(key);  
            key = value;  
            dictionary.Add(key, tempValue);  
        }  
    }  
  
    public object Value  
    {  
        get { return this.value; }  
        set  
        {  
            this.value = value;  
            dictionary[key] = this.value;  
        }  
    }  
}  
  
[DebuggerDisplay("{DebuggerDisplay,nq}")]  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable  
{  
    public Hashtable hashtable;  
  
    public MyHashtable()  
    {  
        hashtable = new Hashtable();    
    }
    
    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
    private class HashtableDebugView  
    {  
        private MyHashtable myhashtable;  
        public HashtableDebugView(MyHashtable myhashtable)  
        {  
            this.myhashtable = myhashtable;  
        }  
  
        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]  
        public KeyValuePairs[] Keys  
        {  
            get  
            {  
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];  
  
                int i = 0;  
                foreach (object key in myhashtable.hashtable.Keys)  
                {  
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);  
                    i++;  
                }  
                return keys;  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando o atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Especificadores de formato em c#](../debugger/format-specifiers-in-csharp.md)   
 [Aprimorando a depuração com os atributos de exibição do depurador](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
