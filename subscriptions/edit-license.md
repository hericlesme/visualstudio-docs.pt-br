---
title: Editar assinaturas no portal do administrador | Visual Studio Marketplace
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "Saiba como os administradores podem editar atribuições de assinatura."
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 985dea7a301130d4641ef9ba3ca2c5ae67218ad4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="editing-visual-studio-subscription-assignments"></a>Editando atribuições de assinatura do Visual Studio

## <a name="making-changes-to-subscriber-information"></a>Fazendo alterações nas informações do assinante
Você pode editar as informações do assinante para corrigir erros ou para atualizar as informações. 
**Observe que a edição do endereço de email do assinante fará com que os benefícios existentes sejam redefinidos.**

Para editar um assinante, selecione as reticências (...) que aparecem ao lado do endereço de email do assinante ao passar o mouse sobre ele. Será exibida uma lista suspensa.  Selecione **editar** para modificar os detalhes do assinante. Você pode também clicar duas vezes na linha do assinante na grade para abrir a janela de edição.

![Selecione um assinante a ser editado](_img\edit-license\select-subscriber.png)

Você pode atualizar o nome, o sobrenome, o país, o idioma e os downloads do assinante. Edite as informações do assinante e, em seguida, clique em **Salvar**.

![Editar detalhes do assinante](_img\edit-license\edit-subscriber.png)

Observação: se você precisar alterar o nível de assinatura de um assinante, será necessário excluir o usuário do portal e adicioná-lo novamente. Os níveis de assinatura não são editáveis.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Editando vários assinantes por meio da edição em massa

Você pode editar vários assinantes de uma vez usando o processo de edição em massa. Esse recurso é usado principalmente para organizações que estão passando por alterações de endereço de email corporativo ou quando uma organização decide restringir o acesso a downloads. **IMPORTANTE:** os níveis de assinatura (ou seja, Enterprise, Professional, etc.) e os GUIDs da assinatura não podem ser alterados.  Se você tentar um upload com esses itens alterados, o upload falhará.  

1.  Para editar vários assinantes de uma vez, navegue até a guia Assinantes. Na faixa de opções na parte superior, clique em **Editar em Massa**. 

![Editando uma licença – edições em massa](_img\edit-license\edit-license-bulk-edit.png)

2.  A edição em massa usa um modelo do Excel para fazer edições nas informações dos assinantes. Na caixa Edição em Massa, clique em **Exportar este Excel** para baixar a lista atual de assinantes, incluindo todas as informações deles. 

![Editando uma licença – exportar a lista de edições em massa](_img\edit-license\edit-license-bulk-edit-export.png)

3.  Em seguida, salve o arquivo localmente para que ele possa ser encontrado com facilidade e faça as alterações necessárias antes de carregá-lo. Para garantir um upload bem-sucedido, **não edite o nível de assinatura nem o GUID da assinatura**, pois isso causaria falha no upload. 

4.  Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Edição em Massa, clique em **Procurar**. Selecione o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela.

![Editando uma licença – upload do arquivo de edições em massa](_img\edit-license\edit-license-bulk-file-upload.png)

5.  Depois de carregar o arquivo, será exibida uma notificação informando que o upload foi bem-sucedido. 

![Editando uma licença – conclusão do upload das edições em massa](_img\edit-license\edit-license-bulk-upload-complete.png)


