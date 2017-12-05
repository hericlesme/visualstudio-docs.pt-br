---
title: Comportamento do editor | Microsoft Docs
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 3515dfbf3a7cf8c23178aa9df243638f955593e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="editor-behavior"></a>Comportamento do Editor

Comportamentos do editor podem ser definidos para permitir que o código seja formatado à medida que ele é escrito. Essas ações são definidas em **Visual Studio > Preferências...> Editor de Texto > Comportamento**. Veja algumas das funções mais usadas descritas abaixo:

![Opções de Comportamento do Editor](media/source-editor-image9.png)

*  Chaves de fechamento podem ser adicionadas automaticamente ao código ao criar novas classes, métodos ou propriedades. Quando essa opção é selecionada, digitar `{` adicionará `}` automaticamente.
* A formatação de código em tempo real é disparada por pressionamentos de caracteres, como ponto e vírgula ou chaves, que emularão as preferências de formatação definidas.
* Também é possível formatar o arquivo ao salvá-lo, o que permite escrever código o código conforme desejado e deixar o IDE responsável pela formatação do código conforme definido pelas preferências existentes.
* O recuo pode ser definido para Nenhum, Automático ou Inteligente. Essas opções representam o seguinte:
 * Nenhum – define o cursor para o início da próxima linha
 * Automático– define o cursor para a mesma coluna na próxima linha
 * Inteligente – recua a próxima linha com base no código
* O comportamento de quebra de palavras é diferente entre os sistemas operacionais e, para fins de navegação, o editor de texto precisa saber onde as palavras começam e terminam. A formatação pode ser definida para Unix ou do Windows.

Também é possível definir regras de formatação para XML, CSS, HTML e JSON.