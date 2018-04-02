---
title: Inserir controles e modificar seu comportamento no Designer XAML | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: article
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- uwp
ms.openlocfilehash: 828b02daaed0b33bfa2f53cf16bee9b60be2f939
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Inserir controles e modificar seu comportamento no XAML Designer

Controles permitem que usuários interajam com seu aplicativo. Você pode usá-los para coletar informações e executar ações como animar um objeto ou consultar uma fonte de dados.

## <a name="add-controls-to-the-artboard"></a>Adicionar controles à prancheta

Você pode arrastar controles do painel **Ativos** para a **prancheta** e, em seguida, modificá-los na janela **Propriedades**.

![Mesclar &#45; Ativos &#45; FlipView](../designers/media/blend_assetsflipview_xaml.png "blend_AssetsFlipView_XAML")

Esses vídeos mostram como usar alguns dos controles mais comuns.

|Controle|Assista a um breve vídeo|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png)|![Ícone de reproduzir](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Adicionar os controles](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png)|![Ícone de reproduzir](../designers/media/bldadminconsoleinitialconfigicon.PNG)[Criar um botão](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png)|![Ícone de reproduzir](../designers/media/bldadminconsoleinitialconfigicon.PNG)[Adicionar imagens a um bloco de texto](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png)|![Ícone de reproduzir](../designers/media/bldadminconsoleinitialconfigicon.PNG)[Criar um controle deslizante com uma dica de ferramenta](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Fazer um controle de uma imagem, forma ou caminho

 Você pode transformar qualquer objeto em um controle.

 ![Combinar caixa de diálogo Transformar em controle](../designers/media/blend_makeintocontrol_xaml.png "blend_MakeIntoControl_XAML")

 Por exemplo, imagine uma imagem de uma televisão no centro da página. Você pode criar controles de imagens pequenas que se parecem com botões de televisão. Em seguida, os usuários podem clicar nesses botões para trocar de canal.

 Isso é possível porque os botões agora são controles. Com controles, você pode responder às interações do usuário; Nesse caso, quando o usuário clica em um botão.

 Para criar um controle, selecione um objeto. No menu **Ferramentas**, clique em **Transformar em Controle**.

## <a name="make-controls-do-things"></a>Fazer com que controles façam algo

 Controles podem executar ações quando os usuários interagem com eles. Por exemplo, eles podem iniciar uma animação, atualizar uma fonte de dados ou reproduzir um vídeo.

 Use *gatilhos*, *comportamentos* e *eventos* para fazer com que os controles façam coisas.

### <a name="triggers"></a>Gatilhos

 O *gatilho* altera uma propriedade ou executa uma tarefa em resposta a um evento ou uma alteração em outra propriedade. Por exemplo, você pode alterar a cor de um botão quando os usuários passarem o mouse sobre ele.

 ![O painel “Gatilhos”](../designers/media/custom_button_blend_propertytriggerinfo.png)

 **Assista a um vídeo curto:** ![Botão de reprodução](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Adicionar um gatilho de propriedade](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).

### <a name="behaviors"></a>Comportamentos

 Um *comportamento* é um pacote reutilizável de código. Ele pode fazer um pouco mais além de alterar as propriedades. Ele pode realizar ações como consultar um serviço de dados. A combinação vem com uma pequena coleção deles, mas você pode adicionar mais. Arraste um comportamento para qualquer objeto na sua prancheta e personalize o comportamento configurando propriedades.

 ![FluidMoveBehavior no painel Propriedades](../designers/media/b4_fluidmovebehaviorproperties_sample.png)

 **Assista a um vídeo curto:** ![Ícone de reprodução](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Dicas de blend: introdução ao uso de comportamentos Parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Eventos

 Para máxima flexibilidade, manipule um *evento*. Você precisará escrever um pouco de código.

 **Assista a um vídeo curto:** ![Botão de reprodução](../designers/media/bldadminconsoleinitialconfigicon.PNG) [Adicionar um evento de mouse](https://www.youtube.com/watch?v=2PMxAlb-x_E).