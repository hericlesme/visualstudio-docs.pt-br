---
title: Manipuladores de eventos propagam alterações fora do modelo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ac748cae6bf36a95b95c5d9a27aa9469ae440eed
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Manipuladores de eventos propagam alterações fora do modelo

Na visualização e modelagem SDK, você pode definir manipuladores de eventos de armazenamento para propagar alterações aos recursos fora da loja, como modelos em outros repositórios ou outros, arquivos, variáveis de armazenamento não [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensões. Manipuladores de eventos de armazenamento são executados após o término da transação na qual ocorreu o evento de disparo. Elas também são executadas em uma operação de desfazer ou refazer. Portanto, ao contrário das regras de repositório de eventos de armazenamento são mais úteis para atualizar os valores que estão fora da loja. Ao contrário de eventos do .NET, manipuladores de eventos de armazenamento são registrados para escutar em uma classe: você não precisa registrar um manipulador separado para cada instância. Para obter mais informações sobre como escolher entre diferentes maneiras para controlar alterações, consulte [respondendo a e propagando alterações](../modeling/responding-to-and-propagating-changes.md).

A superfície de gráfica e outros controles de interface do usuário são exemplos de recursos externos que podem ser tratados pelo repositório de eventos.

### <a name="to-define-a-store-event"></a>Para definir um evento de armazenamento

1.  Escolha o tipo de evento que você deseja monitorar. Para obter uma lista completa, examine as propriedades de <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Cada propriedade corresponde a um tipo de evento. O mais usados são de tipos de evento:

    -   `ElementAdded` -disparado quando um elemento de modelo, o link de relação, forma ou conector é criado.

    -   ElementPropertyChanged - disparado quando o valor de um `Normal` propriedade de domínio é alterada. O evento é disparado somente se os valores novos e antigos não são iguais. O evento não pode ser aplicado a propriedades de armazenamento calculado e personalizado.

         Ele não pode ser aplicado às propriedades de função que correspondem aos links de relação. Em vez disso, use `ElementAdded` para monitorar a relação de domínio.

    -   `ElementDeleted` -disparado depois de um elemento de modelo, relação, forma ou o conector foi excluído. Você ainda pode acessar os valores de propriedade do elemento, mas ele terá nenhuma relação com outros elementos.

2.  Adicione uma definição de classe parcial para *YourDsl * DocData** em um arquivo de código separado no **DslPackage** projeto.

3.  Escreva o código do evento como um método, como no exemplo a seguir. Ele pode ser `static`, a menos que você deseja acessar `DocData`.

4.  Substituir `OnDocumentLoaded()` para registrar o manipulador. Se você tiver mais de um manipulador, você pode registrá-los todos no mesmo local.

O local do código de registro não é crítico. `DocView.LoadView()` é um local alternativo.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usar eventos para fazer ajustes não podem ser executados no repositório

Repositório de eventos não são usados normalmente para propagar as alterações dentro do armazenamento, porque o manipulador de eventos é executado depois que a transação for confirmada. Em vez disso, você usaria uma regra do repositório. Para obter mais informações, consulte [regras propagar as alterações no modelo de](../modeling/rules-propagate-changes-within-the-model.md).

No entanto, você pode usar um manipulador de eventos para fazer atualizações adicionais para o armazenamento, se desejar que o usuário seja capaz de desfazer as atualizações adicionais separadamente a partir do evento original. Por exemplo, suponha que letras minúsculas são a convenção comum para títulos de álbum. Você pode escrever um manipulador de eventos de armazenamento que corrige o título em letras minúsculas, depois que o usuário tiver digitado em letras maiusculas. Mas o usuário pode usar o comando Desfazer para cancelar a correção, restaurando os caracteres de letras maiusculas. Remove um segundo desfazer a alteração do usuário.

Por outro lado, se você escreveu uma regra do repositório para fazer a mesma coisa, a alteração do usuário e a correção poderá ser na mesma transação, para que o usuário não foi possível desfazer o ajuste sem perder a alteração original.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Se você gravar um evento que atualiza o armazenamento:

-   Use `store.InUndoRedoOrRollback` para evitar alterações a elementos de modelo em Desfazer. O Gerenciador de transações definirá tudo no repositório de volta ao seu estado original.

-   Use `store.InSerializationTransaction` para evitar alterações enquanto o modelo está sendo carregado do arquivo.

-   Suas alterações fará com que mais eventos a ser disparada. Certifique-se de que você evite um loop infinito.

## <a name="store-event-types"></a>Armazenar tipos de evento

Cada tipo de evento corresponde a uma coleção em Store.EventManagerDirectory. Você pode adicionar ou remover manipuladores de eventos a qualquer momento, mas é comum para adicioná-las quando o documento é carregado.

|`EventManagerDirectory` Nome da propriedade|Executado quando|
|-------------------------------------------|-------------------|
|ElementAdded|Uma instância de uma classe de domínio, o relacionamento de domínio, forma, conector ou diagrama é criada.|
|ElementDeleted|Um elemento de modelo foi removido do diretório do elemento da loja e não está mais na origem ou destino de qualquer relação. O elemento não é realmente excluído da memória, mas é mantido no caso de um Desfazer futuras.|
|ElementEventsBegun|Chamado no final de uma transação externa.|
|ElementEventsEnded|Chamado quando todos os outros eventos foram processados.|
|ElementMoved|Um elemento de modelo foi movido de um repositório de partição para outra.<br /><br /> Isso não está relacionado ao local de uma forma no diagrama.|
|ElementPropertyChanged|O valor de uma propriedade de domínio foi alterado. Isso é executado somente se os valores novos e antigos são diferentes.|
|RolePlayerChanged|Uma das duas funções (termina) de um relacionamento faz referência a um novo elemento.|
|RolePlayerOrderChanged|Em uma função com multiplicidade maior que 1, a sequência de links foi alterado.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Consulte também

- [Respondendo a alterações e propagando-as](../modeling/responding-to-and-propagating-changes.md)
- [Código de exemplo: diagramas de circuito](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]