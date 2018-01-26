---
title: "Definindo uma política de bloqueio para criar segmentos de somente leitura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6848f2c0b6c8d25fe7964fdb5519aa3f075bde57
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2018
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definindo uma política de bloqueio para criar segmentos somente leitura
A API de imutabilidade do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] visualização e modelagem SDK permite que um programa para bloqueio parte ou todo um modelo de linguagem específica de domínio (DSL) para que ele pode ser lida mas não alterado. Essa opção somente leitura pode ser usada, por exemplo, para que um usuário pode solicitar seus colegas para anotar e analisar um modelo DSL, mas pode não permiti-los alterando o original.  
  
 Além disso, como autor de uma DSL, você pode definir um *política de bloqueio.* Uma política de bloqueio define quais bloqueios são permitidas, não é permitido ou obrigatório. Por exemplo, quando você publica uma DSL, você pode encorajar os desenvolvedores de terceiros para estendê-lo com novos comandos. Mas você também pode usar uma política de bloqueio para impedir que alterar o status de somente leitura de partes específicas do modelo.  
  
> [!NOTE]
>  Uma política de bloqueio pode ser evitada por meio de reflexão. Ele fornece um limite claro para os desenvolvedores de terceiros, mas não fornece alta segurança.  
  
 Mais informações e exemplos estão disponíveis no Visual Studio [visualização e modelagem SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) site da Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Configuração e a obtenção de bloqueios  
 Você pode definir os bloqueios no repositório, em uma partição ou em um elemento individual. Por exemplo, esta instrução impedirá que um elemento de modelo que está sendo excluído e também impedirá que suas propriedades sejam alteradas:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Outros valores de bloqueio podem ser usados para impedir alterações em relações, criação de elemento, a movimentação entre partições e links de ordenação novamente em uma função.  
  
 Os bloqueios se aplicam às ações do usuário e ao código de programa. Se o código do programa tenta fazer uma alteração, um `InvalidOperationException` será lançada. Os bloqueios são ignorados em uma operação de desfazer ou refazer.  
  
 Você pode descobrir se um elemento tem um qualquer bloqueio em um determinado conjunto usando `IsLocked(Locks)` e você pode obter o conjunto atual de bloqueios em um elemento usando `GetLocks()`.  
  
 Você pode definir um bloqueio sem usar uma transação. O banco de dados de bloqueio não é parte do armazenamento. Se você definir um bloqueio em resposta a uma alteração de um valor no armazenamento, por exemplo em OnValueChanged, você deve permitir que as alterações que fazem parte de uma operação de desfazer.  
  
 Esses métodos são os métodos de extensão que estão definidos no <xref:Microsoft.VisualStudio.Modeling.Immutability> namespace.  
  
### <a name="locks-on-partitions-and-stores"></a>Bloqueios em partições e lojas  
 Bloqueios também podem ser aplicados a partições e o armazenamento. Um bloqueio que é definido em uma partição se aplica a todos os elementos na partição. Portanto, por exemplo, a instrução a seguir impedirá todos os elementos em uma partição que está sendo excluída, independentemente dos Estados de seus próprios bloqueios. No entanto, outros bloqueios como `Locks.Property` ainda pode ser definido em elementos individuais:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Um bloqueio que é definido no repositório se aplica a todos os seus elementos, independentemente das configurações de bloqueio em elementos e as partições.  
  
### <a name="using-locks"></a>Usar bloqueios  
 Você pode usar bloqueios para implementar esquemas, como os exemplos a seguir:  
  
-   Não permitir alterações para todos os elementos e relações, exceto aqueles que representam os comentários. Isso permite que os usuários anotar um modelo sem alterá-lo.  
  
-   Não permitir alterações na partição padrão, mas permitir que as alterações na partição de diagrama. O usuário pode reorganizar o diagrama, mas não é possível alterar o modelo subjacente.  
  
-   Não permitir alterações no repositório, exceto um grupo de usuários que são registrados em um banco de dados separado. Para outros usuários, o diagrama e o modelo são somente leitura.  
  
-   Não permitir alterações do modelo se uma propriedade booleana do diagrama é definida como true. Forneça um comando de menu para alterar essa propriedade. Isso ajuda a garantir que os usuários que eles não fazem alterações acidentalmente.  
  
-   Não permitir a adição e exclusão de elementos e relações de classes específicos, mas permitir que as alterações de propriedade. Isso fornece aos usuários uma forma fixa no qual eles podem preencher as propriedades.  
  
## <a name="lock-values"></a>Valores de bloqueio  
 Bloqueios podem ser definidos em um repositório, partição ou ModelElement individual. Bloqueios é um `Flags` enumeração: você pode combinar seus valores usando ' &#124;'.  
  
-   Bloqueios de depósito sempre incluem os bloqueios de sua partição.  
  
-   Bloqueios de uma partição sempre incluem os bloqueios do armazenamento.  
  
 Não é possível definir um bloqueio em uma partição ou repositório e ao mesmo tempo, desabilite o bloqueio em um elemento individual.  
  
|Valor|Que significa se `IsLocked(Value)` é verdadeiro|  
|-----------|------------------------------------------|  
|Nenhum|Nenhuma restrição.|  
|Propriedade|Propriedades do domínio de elementos não podem ser alteradas. Isso não se aplicam a propriedades que são geradas pela função de uma classe de domínio em uma relação.|  
|Adicionar|Novos elementos e links não pode ser criado em uma partição ou repositório.<br /><br /> Não aplicável a `ModelElement`.|  
|Mover|Elemento não pode ser movido entre partições se `element.IsLocked(Move)` for true, ou se `targetPartition.IsLocked(Move)` for true.|  
|Excluir|Um elemento não pode ser excluído se esse bloqueio é definido no próprio elemento ou em qualquer um dos elementos para que a exclusão propagará, tais como formas e os elementos inseridos.<br /><br /> Você pode usar `element.CanDelete()` para descobrir se um elemento pode ser excluído.|  
|Reordenar|A ordem dos links em uma roleplayer não pode ser alterada.|  
|RolePlayer|O conjunto de links que são originados nesse elemento não pode ser alterado. Por exemplo, os novos elementos não podem ser inseridos nesse elemento. Isso não afeta os links para os quais esse elemento é o destino.<br /><br /> Se esse elemento é um link, sua origem e destino não são afetados.|  
|Todos|OR bit a bit dos outros valores.|  
  
## <a name="locking-policies"></a>Políticas de bloqueio  
 Como autor de uma DSL, você pode definir um *política de bloqueio*. Uma política de bloqueio moderates a operação de SetLocks(), para que você pode impedir bloqueios específicos que está sendo definido ou exigem que os bloqueios específicos devem ser definidos. Normalmente, você usaria uma política de bloqueio para evitar que usuários ou desenvolvedores de contravening acidentalmente o uso pretendido de uma DSL, da mesma maneira que você pode declarar uma variável `private`.  
  
 Você também pode usar uma política de bloqueio para definir os bloqueios em todos os elementos depende do tipo do elemento. Isso ocorre porque `SetLocks(Locks.None)` é chamado quando um elemento é criado ou desserializado do arquivo.  
  
 No entanto, você não pode usar uma política para variar os bloqueios em um elemento durante sua vida útil. Para obter esse efeito, você deve usar chamadas para `SetLocks()`.  
  
 Para definir uma política de bloqueio, você precisa:  
  
-   Criar uma classe que implementa <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Adicione esta classe para os serviços que estão disponíveis por meio do DocData do seu DSL.  
  
### <a name="to-define-a-locking-policy"></a>Para definir uma política de bloqueio  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>tem a seguinte definição:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Esses métodos são chamados quando é feita uma chamada para `SetLocks()` em um repositório, partição ou ModelElement. Cada método, terá um conjunto proposto de bloqueios. Você pode retornar o conjunto de proposta, ou você pode adicionar e subtrair bloqueios.  
  
 Por exemplo:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 Para certificar-se de que os usuários sempre podem excluir elementos, mesmo se outro código chama`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Para impedir a alteração em todas as propriedades de cada elemento de MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Para disponibilizar a política como um serviço  
 No seu `DslPackage` projeto, adicione um novo arquivo que contém o código que se parece com o exemplo a seguir:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```
