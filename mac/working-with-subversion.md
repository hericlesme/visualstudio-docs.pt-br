---
title: Trabalhando com o Subversion
description: Usando o Subversion no Visual Studio para Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: 1c03c4fac50c34cb96583a1fc8c16a403b7bbe1b
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
---
# <a name="working-with-subversion"></a>Trabalhando com o Subversion

O Subversion é o sistema de controle de versão centralizado que permite fazer check-out de uma única cópia mestra dos dados centralizados. Em contraste com o Git, fazer check-out de um repositório do Subversion não clona todo o repositório e cria apenas um instantâneo pontual.

O Subversion usa um modelo de copiar-modificar-mesclar para permitir que os usuários trabalhem simultaneamente no mesmo repositório. Isso significa que cada usuário cria uma cópia, local ou funcional, de dados centralizados na qual trabalham independentemente. As alterações nas cópias funcionais dos usuários são mescladas de forma cronológica.

Por exemplo, imagine que o usuário A e B fazem check-out de uma cópia do repositório remoto e cada um deles modifica os arquivos. O usuário A concluir as modificações e as confirma remotamente. Antes do usuário B confirmar seu trabalho, ele deverá atualizar sua cópia funcional com as alterações remotas, mesclando as alterações do usuário A.

As seções a seguir exploram como o Subversion pode ser usado para o controle de versão no Visual Studio para Mac.

A imagem a seguir ilustra as opções fornecidas pelo Visual Studio para Mac pelo item de menu de Controle de Versão:

![Itens de menu de Controle de versão](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Fazer check-out...

Antes de começar a usar um repositório remoto do Subversion, faça check-out do repositório para criar uma cópia funcional desse diretório em seu computador local.

Para saber mais sobre como usar o recurso de **Check-out** no Visual Studio para Mac, siga as etapas na seção [Configurando um repositório do Subversion](~/set-up-subversion-repository.md).

## <a name="update-solution"></a>Atualizar solução

Ao usar um repositório remoto, é importante lembrar que outros usuários podem estar modificando os arquivos, deixando sua cópia funcional desatualizada. Para se preparar para o conflito, sempre é recomendável para efetuar pull nas alterações do repositório em sua solução antes de começar a trabalhar e antes de confirmar. Para fazer alterações pull, selecione o item de menu **Controle de versão > Atualizar solução**.

## <a name="review-solution-and-commit"></a>Examinar e confirmar a solução

Para examinar as alterações nos arquivos, use as guias Alterações, Acusar, Registro em log e Mesclar em cada documento, como ilustrado na imagem a seguir:

![Guias de Controle de versão](media/version-control-vcTabs.png)

Examine todas as alterações em um projeto navegando para o item de menu **Controle de versão > Examinar e confirmar solução**:

![Examinar a solução](media/version-control-vcStatus.png)

Isso permite exibir todas as alterações em cada arquivo de um projeto com a opção de Reverter, Criar um Patch ou Confirmar.

Para confirmar um arquivo para o repositório remoto, pressione Confirmar..., digite uma mensagem de confirmação e confirme com o botão Confirmar:


![Confirmando um arquivo](media/version-control-svnCommit.png)

Isso enviará as alterações ao repositório em que elas criarão a nova revisão de todas as suas modificações.
