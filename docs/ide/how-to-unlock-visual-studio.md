---
title: Como desbloquear o Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e08831347c09d80427d1fba38c926f7d1b227f4
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2018
---
# <a name="how-to-unlock-visual-studio"></a>Como desbloquear o Visual Studio

Você pode avaliar o Visual Studio gratuitamente por até 30 dias. Entrar no IDE estende o período de avaliação para 90 dias. Para continuar usando o Visual Studio, desbloqueie o IDE:

- usando uma assinatura online

- inserindo uma chave do produto (Product Key)

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Para desbloquear o Visual Studio usando uma assinatura online

Para desbloquear o Visual Studio usando uma assinatura do MSDN ou do Visual Studio Team Service associada a uma conta da Microsoft ou uma conta corporativa ou de estudante:

1. Clique no botão "Entrar" no canto superior direito do IDE (ou acesse Arquivo > Configurações de Conta para abrir a caixa de diálogo Configurações de Conta e clique no botão "Entrar".)

1. Insira as credenciais para uma conta da Microsoft ou uma conta corporativa ou de estudante. O Visual Studio encontrará uma assinatura do Visual Studio ou uma assinatura do Visual Studio Team Services associada à sua conta.

> [!IMPORTANT]
> O Visual Studio procura automaticamente assinaturas online associadas ao se conectar a uma conta do Visual Studio Team Services pela janela de ferramentas do Team Explorer. Quando você se conecta a uma conta do Visual Studio Team Services, pode entrar usando contas da Microsoft ou corporativas ou de estudante. Se houver uma assinatura online para aquela conta de usuário, o Visual Studio automaticamente desbloqueará o IDE para você.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear o Visual Studio com uma chave do produto (Product Key)

1. Selecione **Arquivo**, **Configurações de Conta** para abrir a caixa de diálogo Configurações de Conta e clique no link **Licenciar com uma chave do produto (Product Key)**.

Insira a chave do produto (Product Key) no espaço fornecido.

> [!TIP]
> As versões de pré-lançamento do Visual Studio não têm chaves de produto. Você deve entrar no IDE para usar as versões de pré-lançamento.

## <a name="address-license-problem-states"></a>Tratar os estados de problema de licença

### <a name="update-stale-licenses"></a>Atualizar licenças obsoletas

 Você poderá ver a mensagem abaixo informando que sua licença está obsoleta no Visual Studio, indicando "Sua licença ficou obsoleta e deve ser atualizada".

 ![Mensagem de licença obsoleta do Visual Studio](../ide/media/vs2017_stale-license.png)

 Essa mensagem indica que embora sua assinatura ainda possa ser válida, o token de licença que o Visual Studio usa para manter sua assinatura atualizada ainda não foi atualizado e se tornou obsoleto devido a um dos motivos a seguir:

- Você não usou o Visual Studio ou não teve uma conexão com a Internet por um longo período.
- Você saiu do Visual Studio.

Antes de o token de licença se tornar obsoleto, o Visual Studio mostrará primeiro uma mensagem de aviso solicitando que você insira suas credenciais novamente.

Se você não digitar novamente suas credenciais, o token começará a ficar obsoleto e a caixa de diálogo Configurações da Conta informará quantos dias você ainda tem até seu token expirar totalmente. Depois que o token expirar, você precisará inserir novamente suas credenciais para esta conta ou licença com outro método acima para poder continuar usando o Visual Studio.

> [!Important]
> Se estiver usando o Visual Studio por longos períodos em ambientes com acesso limitado ou sem acesso à Internet, você deverá usar uma chave do produto (Product Key) para desbloquear o Visual Studio para evitar a interrupção.

### <a name="update-expired-licenses"></a>Atualizar licenças expiradas

 Se a sua assinatura tiver expirado completamente e você não tiver mais direitos de acesso ao Visual Studio, será necessário renovar sua assinatura ou adicionar outra conta que tenha uma assinatura. Para obter mais informações sobre a licença que você está usando, acesse **Arquivo**, **Configurações de Conta** e examine as informações de licença no lado direito da caixa de diálogo. Se você tiver outra assinatura associada a uma conta diferente, adicione essa conta à lista **Todas as Contas** no lado esquerdo da caixa de diálogo selecionando o link **Adicionar uma conta...**.

## <a name="see-also"></a>Consulte também

* [Signing in to Visual Studio](../ide/signing-in-to-visual-studio.md) (Entrando no Visual Studio)
