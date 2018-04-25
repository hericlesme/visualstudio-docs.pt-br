---
title: Especificar o percentual de usuários virtuais que usam dados de cache da Web para testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual users
ms.assetid: f66d5d43-4121-4487-b27f-d0a0baaf7601
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 76d611af76877a9638ed2815a7d8dc5f77e45c8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data"></a>Como especificar a porcentagem de usuários virtuais que usam dados de cache da Web

Depois de criar seu teste de carga com o **Novo Assistente de Teste de Carga**, você poderá alterar as propriedades dos cenários de forma a atender suas necessidades e objetivos de teste usando o **Editor de Teste de Carga**. Para obter uma lista completa das propriedades de cenário de teste da carga e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

A propriedade de **Percentual de novos usuários** é definida na janela Propriedades. Edite as propriedades de cenário do teste de carga no Editor de Testes de Carga.

A propriedade **Percentual de novos usuários** afeta a maneira como o teste de carga simula o armazenamento em cache que seria executado por um navegador da Web. Por padrão, a propriedade de **Percentual de novos usuários** é definida como 0%. Se o valor da propriedade **Percentual de novos usuários** for definido como 100%, cada execução de teste de desempenho Web em um teste de carga será tratada como um usuário de primeira vez no site que não tem nenhum conteúdo do site no cache de visitas anteriores do navegador. Assim, todas as solicitações do teste na Web, incluindo todas as solicitações dependentes como imagens, são baixadas.

> [!NOTE]
> Quando o mesmo recurso que pode ser armazenado em cache é solicitado mais de uma vez em um teste na Web, as solicitações não são baixadas.

Se você estiver testando a carga de um site que tem um número significativo de usuários de retorno que provavelmente têm imagens e outros conteúdos armazenados em cache localmente, uma configuração de 100% para a propriedade de **Percentual de novos usuários** gerará mais solicitações de download do que aconteceria no uso real. Nesse caso, você deve calcular o percentual de visitas ao site que são de usuários de primeira vez do site e definir a propriedade de **Percentual de novos usuários** adequadamente.

## <a name="to-specify-the-agents-to-use-for-a-scenario"></a>Para especificar os agentes a usar em um cenário

1.  Abra um teste de carga.

     O **Editor de Teste de Carga** é exibido. A árvore do teste de carga é exibida.

2.  Na pasta **Cenários** das árvores de teste de carga, escolha o nó do cenário para o qual deseja especificar os agentes a serem usados.

3.  No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades do cenário são exibidas na janela Propriedades.

4.  Defina o valor da propriedade **Percentual de novos usuários** digitando um número para o percentual de novos usuários.

5.  Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Percentual de novos usuários**.

## <a name="see-also"></a>Consulte também

- [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md)
- [Passo a passo: criar e executar um teste de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Controladores e agentes de teste](configure-test-agents-and-controllers-for-load-tests.md)
- [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md)
- [Editando padrões de carga para modelar atividades de usuário virtual](../test/edit-load-patterns-to-model-virtual-user-activities.md)