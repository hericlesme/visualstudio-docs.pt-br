---
title: 'CA1812: evitar classes internas sem instâncias'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf39d775c5602aaddf5b9487d175ddbbdd70d52e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: evitar classes internas sem instâncias
|||
|-|-|
|NomeDoTipo|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não recentes|

## <a name="cause"></a>Causa
 Uma instância de um tipo no nível de assembly não é criada pelo código no assembly.

## <a name="rule-description"></a>Descrição da Regra
 Essa regra tenta localizar uma chamada para um dos construtores de tipo e informa uma violação se nenhuma chamada for encontrada.

 Os seguintes tipos não são examinados por essa regra:

-   Tipos de valor

-   Tipos abstratos

-   Enumerações

-   Delegados

-   Tipos de matriz emitido pelo compilador

-   Tipos que não pode ser instanciado e que definem `static` (`Shared` no Visual Basic) somente métodos.

 Se você aplicar <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> para o assembly que está sendo analisado, esta regra não ocorrerá em qualquer construtores que são marcados como `internal` porque você não pode determinar se um campo está sendo usado por outro `friend` assembly.

 Embora você não é possível contornar essa limitação na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] análise de código, o FxCop autônomo externo ocorrerá em construtores internos se cada `friend` assembly está presente na análise.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, remova o tipo ou adicione o código que usa. Se o tipo contém apenas os métodos estáticos, adicione o seguinte para o tipo para impedir que o compilador emitindo um construtor de instância pública padrão:

-   Um construtor particular para tipos de destino [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versões 1.0 e 1.1.

-   O `static` (`Shared` no Visual Basic) modificador para tipos de destino [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 É seguro suprimir um aviso dessa regra. É recomendável que você suprime este aviso nas seguintes situações:

-   A classe é criada por meio de métodos de reflexão de associação tardia, como <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

-   A classe é criada automaticamente pelo tempo de execução ou [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Por exemplo, as classes que implementam <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> ou <xref:System.Web.IHttpHandler?displayProperty=fullName>.

-   A classe é passada como um parâmetro de tipo genérico que tem uma nova restrição. Por exemplo, o exemplo a seguir gerará esta regra.

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }
    // [...]
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

 Nessas situações, é recomendável que você suprime este aviso.

## <a name="related-rules"></a>Regras relacionadas
 [CA1811: evitar código privado não chamado](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: examinar parâmetros não usados](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)