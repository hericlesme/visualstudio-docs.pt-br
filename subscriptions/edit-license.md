---
title: Editar assinaturas no Portal do administrador | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Saiba como os administradores podem editar atribuições de assinatura.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: e4ee209af97d09f5d7e2125d2111746f6fe491f5
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34476631"
---
# <a name="editing-visual-studio-subscription-assignments"></a>Editando atribuições de assinatura do Visual Studio

Como administrador de assinaturas, você pode fazer alterações nas assinaturas atribuídas às pessoas na organização.  Este artigo descreve os tipos de alterações que você pode fazer e fornece as etapas necessárias. 

## <a name="making-changes-to-subscriber-information"></a>Fazendo alterações nas informações do assinante
Você pode editar as informações do assinante para corrigir erros ou para atualizar as informações. 

Para editar um assinante, selecione as reticências (...) que aparecem ao lado do endereço de email do assinante ao passar o mouse sobre ele. Será exibida uma lista suspensa.  Selecione **Editar** para modificar os detalhes do assinante. Também é possível clicar duas vezes na linha do assinante na grade para abrir a janela de edição.

   <img alt="Select subscriber to edit" src="_img\edit-license\select-subscriber.png" style="border: 1px solid #CCCCCC" />
    
Você pode atualizar o nome, o sobrenome, o país, o idioma e os downloads do assinante. Edite as informações do assinante e, em seguida, clique em **Salvar**.

 
   <img alt="Edit subscriber details" src="_img\edit-license\edit-subscriber.png" style="border: 1px solid #CCCCCC" />
   > [!NOTE]
   > Se você precisar alterar o nível de assinatura de um assinante, será necessário excluir o usuário do portal e adicioná-lo novamente. Os níveis de assinatura não são editáveis.

## <a name="editing-multiple-subscribers-by-using-bulk-edit"></a>Editando vários assinantes por meio da edição em massa

Você pode editar vários assinantes de uma vez usando o processo de edição em massa. Esse recurso é usado principalmente para organizações que estão passando por alterações de endereço de email corporativo ou quando uma organização decide restringir o acesso a downloads. 

   > [!IMPORTANT]
   > Os níveis de assinatura (ou seja, Enterprise, Professional, etc.) e os GUIDs da assinatura não podem ser alterados.  Se você tentar um upload com esses itens alterados, o upload falhará.  

1.  Para editar vários assinantes de uma vez, navegue até a guia Assinantes. Na faixa de opções na parte superior, clique em **Editar em Massa**. 

    <img alt="Editing a License - Bulk Edits" src="_img\edit-license\edit-license-bulk-edit.png" style="border: 1px solid #CCCCCC" />

2.  A edição em massa usa um modelo do Excel para fazer edições nas informações dos assinantes. Na caixa Edição em Massa, clique em **Exportar este Excel** para baixar a lista atual de assinantes, incluindo todas as informações deles. 

    <img alt="Editing a License - Export Bulk Edits List" src="_img\edit-license\edit-license-bulk-edit-export.png" style="border: 1px solid #CCCCCC" />

3.  Em seguida, salve o arquivo localmente para que ele possa ser encontrado com facilidade e faça as alterações necessárias antes de carregá-lo. Para garantir um upload bem-sucedido, **não edite o nível de assinatura nem o GUID da assinatura**, pois isso causaria falha no upload. 

4.  Retorne ao Portal de Administração de Assinaturas do Visual Studio e na caixa de diálogo Edição em Massa, clique em **Procurar**. Selecione o arquivo do Excel que você salvou e clique em **OK**. O andamento do upload será exibido na tela.

    <img alt="Editing a License - Bulk Edits File Upload" src="_img\edit-license\edit-license-bulk-file-upload1.png" style="border: 1px solid #CCCCCC" />

5.  Depois de carregar o arquivo, será exibida uma notificação informando que o upload foi bem-sucedido. Neste ponto, suas edições serão refletidas nas informações do assinante. 

    <img alt="Editing a License - Bulk Edits Upload Complete" src="_img\edit-license\edit-license-bulk-upload-complete.png" style="border: 1px solid #CCCCCC" />

