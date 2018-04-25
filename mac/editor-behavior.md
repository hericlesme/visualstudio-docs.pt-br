---
title: Comportamento do Editor
description: ''
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 5de50299ec1d79f28687e5f49d8169ecd3413279
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
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