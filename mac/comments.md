---
title: Comentários
description: Este artigo descreve como usar comentários no editor de código-fonte do Visual Studio para Mac
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.openlocfilehash: 28c02f7f6347da67133a82c1d0aa71d44a4309d2
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224293"
---
# <a name="comments"></a>Comentários

Ao depurar ou fazer experimentos no código, pode ser útil comentar blocos de código ou temporariamente ou a longo prazo. 

Para comentar um bloco inteiro de código:

* Selecione o código e escolha **Ativar/desativar comentários da linha** no menu de contexto

OU

* Use a associação de tela `cmd + /` no código selecionado.

Esses métodos podem ser usados para comentar ou remover a marca de comentário de partes do código. Em arquivos de C#, níveis adicionais de comentários de linha podem ser adicionados, permitindo que regiões de códigos sejam comentadas e a marca de comentário seja removida, preservando ainda os comentários reais: 

 ![comentários de vários níveis](media/source-editor-image8.png)

Comentários também são úteis para documentar código para futuros desenvolvedores poderão vir a interagir com ele. Isso geralmente é feito na forma de comentário de várias linhas, que são adicionados da seguinte maneira em cada linguagem:

**C#**

``` cs
/*
 This is a multi-line
 comment in C#
*/
```
**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```
