---
title: Propriedades de armazenamento calculado e personalizado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d8749e87a25cc9243cf7e76a99b027975673ab4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Propriedades calculadas e de armazenamento personalizado
Todas as propriedades de domínio em uma domínio específico DSL (linguagem) podem ser exibidas para o usuário no diagrama e no seu Gerenciador de idioma e podem ser acessadas pelo código do programa. No entanto, as propriedades diferem da forma que seus valores são armazenados.  
  
## <a name="kinds-of-domain-properties"></a>Tipos de propriedades de domínio  
 Na definição de DSL, você pode definir o **tipo** de uma propriedade de domínio, conforme listado na tabela a seguir:  
  
|Tipo de propriedade de domínio|Descrição|  
|--------------------------|-----------------|  
|**Padrão** (padrão)|Uma propriedade de domínio que é salvo o *armazenar* e serializado ao arquivo.|  
|**Calculado**|Uma propriedade de domínio somente leitura que não é salvos no repositório, mas é calculada a partir de outros valores.<br /><br /> Por exemplo, `Person.Age` pode ser calculado a partir `Person.BirthDate`.<br /><br /> Você precisa fornecer o código que executa o cálculo. Normalmente, você pode calcular o valor de outras propriedades de domínio. No entanto, você também pode usar recursos externos.|  
|**Armazenamento personalizado**|Uma propriedade de domínio que não é salvos diretamente no repositório, mas pode ser get e set.<br /><br /> Você precisa fornecer os métodos de obtém e definir o valor.<br /><br /> Por exemplo, `Person.FullAddress` podem ser armazenadas em `Person.StreetAddress`, `Person.City`, e `Person.PostalCode`.<br /><br /> Você também pode acessar recursos externos, por exemplo, para obter e definir valores de um banco de dados.<br /><br /> Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` é verdadeiro. Consulte [transações e Setters personalizados](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornecendo o código para uma propriedade de armazenamento calculado ou personalizado  
 Se você definir o tipo de uma propriedade de domínio calculado ou armazenamento personalizado, você precisa fornecer métodos de acesso. Quando você cria sua solução, um relatório de erros dirá o que é necessário.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Para definir uma calculado ou a propriedade de armazenamento personalizado  
  
1.  No DslDefinition.dsl, selecione a propriedade de domínio no diagrama ou no **DSL Explorer**.  
  
2.  No **propriedades** janela, defina o **tipo** campo **calculado** ou **armazenamento personalizado**.  
  
     Certifique-se de que você também tiver definido sua **tipo** para que você deseja.  
  
3.  Clique em **transformar todos os modelos de** na barra de ferramentas de **Gerenciador de soluções**.  
  
4.  No menu **Compilar**, clique em **Compilar Solução**.  
  
     A seguinte mensagem de erro: "*YourClass* não contém uma definição para Get*YourProperty*."  
  
5.  Clique duas vezes a mensagem de erro.  
  
     Dsl\GeneratedCode\DomainClasses.cs ou DomainRelationships.cs é aberto. Acima a chamada do método realçado, um comentário solicitará que você fornecer uma implementação para Get*YourProperty*().  
  
    > [!NOTE]
    >  Esse arquivo é gerado de DslDefinition.dsl. Se você editar esse arquivo, as alterações serão perdidas na próxima vez que você clicar em **transformar todos os modelos de**. Em vez disso, adicione o método necessário em um arquivo separado.  
  
6.  Criar ou abrir um arquivo de classe em uma pasta separada, por exemplo CustomCode\\*YourDomainClass*. cs.  
  
     Certifique-se de que o namespace é o mesmo que o código gerado.  
  
7.  O arquivo de classe, escreva uma implementação parcial da classe de domínio. Na classe, gravar uma definição para o ausente `Get` método semelhante ao exemplo a seguir:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Se você definir **tipo** para **armazenamento personalizado**, você também precisa fornecer um `Set` método. Por exemplo:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Seu código não deve definir valores no repositório quando `Store.InUndoRedoOrRollback` é verdadeiro. Consulte [transações e Setters personalizados](#setters).  
  
9. Criar e executar a solução.  
  
10. A propriedade de teste. Certifique-se de que você tente **desfazer** e **Refazer**.  
  
##  <a name="setters"></a>Transações e Setters personalizados  
 No método de conjunto de propriedade de armazenamento personalizado, você não precisa abrir uma transação, porque o método é chamado geralmente dentro de uma transação ativa.  
  
 No entanto, o método de conjunto também pode ser chamado se o usuário chama desfazer ou refazer, ou se uma transação está sendo revertida. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> for true, o método de conjunto deve se comportar da seguinte maneira:  
  
-   Ele não deve fazer alterações no armazenamento, como atribuindo valores a outras propriedades de domínio. O Gerenciador de desfazer definirá seus valores.  
  
-   No entanto, ele deve atualizar todos os recursos externos, como banco de dados de conteúdo do arquivo ou objetos fora da loja. Isso irá assegurar que eles são mantidos em synchronism com os valores no repositório.  
  
 Por exemplo:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Para obter mais informações sobre transações, consulte [navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Consulte também  
 [Navegar e atualizar um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Propriedades de domínio](../modeling/properties-of-domain-properties.md)   
 [Como definir uma linguagem específica de domínio](../modeling/how-to-define-a-domain-specific-language.md)