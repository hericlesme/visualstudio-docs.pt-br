---
title: Javascript
description: Informações sobre o suporte para Javascript no Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 21ff2211632cba63dafe2a7abf1964e7a89e87c3
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224030"
---
# <a name="javascript-support"></a>Suporte para Javascript

O Visual Studio para Mac dá suporte para Javascript e Typescript por meio do IntelliSense, da formatação de código e do realce de sintaxe. 

![Suporte para o Editor de TypeScript](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

Para obter mais informações sobre como escrever JavaScript, consulte os guias [Escrevendo código JavaScript](https://docs.microsoft.com/scripting/javascript/writing-javascript-code).

## <a name="adding-a-javascript-file"></a>Adicionando um arquivo JavaScript

Arquivos JavaScript frequentemente são adicionados a projetos do ASP.NET Core usando a caixa de diálogo **Novo Arquivo**. Para adicionar um arquivo JavaScript, clique com o botão direito do mouse no projeto e vá até **Adicionar > Novo Arquivo**: 

![Adicionando novos arquivos ao projeto](media/javascript-image1.png)

Na caixa de diálogo Novo Arquivo, selecione **Web > Arquivo JS Vazio** ou **Web > Arquivos TypeScript**. Dê um nome ao arquivo e, em seguida, escolha **Novo**:

![Criando um novo arquivo TypeScript usando o modelo](media/javascript-image2.png)

## <a name="intellisense"></a>Intellisense

O Visual Studio para Mac usa o [Serviço de Linguagem JavaScript](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense) para fornecer IntelliSense, permitindo que você tenha conclusão de código inteligente, informações de parâmetro e listas de membros ao escrever código.

O IntelliSense de JavaScript no Visual Studio para Mac pode ser baseado em inferência de tipos, JSDoc ou em declarações de TypeScript.

- **Inferência de tipos** – o tipo de um objeto é presumido com base no contexto do código ao redor. Para obter mais informações, consulte a seção do Visual Studio sobre [IntelliSense baseado na inferência de tipos](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference).
- **JSDoc** – há ocasiões em que a inferência de tipos não fornece as informações de tipo corretas. Nesses casos, as informações de tipo podem ser fornecidas explicitamente pelas anotações de [JSDoc](http://usejsdoc.org/about-getting-started.html). Para obter mais informações, consulte a seção do Visual Studio sobre [IntelliSense baseado no JSDoc](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc)
- **Arquivos de declaração de TypeScript** – arquivos `.d.ts` são usados para fornecer valores para o IntelliSense de JavaScript. Tipos declarados no arquivo podem ser usados como tipos em comentários de JSDoc. Para obter mais informações, consulte a seção do Visual Studio sobre [IntelliSense baseado em arquivos de declaração de TypeScript](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) ![adicionando um arquivo de definição de TypeScript](media/javascript-image3.png)