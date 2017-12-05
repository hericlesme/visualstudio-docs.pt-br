---
title: "Passo a passo de segurança do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d036d180fddcce443debe3d7917415380187994c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Atualizar o repositório de certificados de segurança do Unity Mono

O Unity Mono vem com um repositório de certificados vazio e, portanto, não confia em nenhum site. Você pode ler mais sobre isso em [Mono security FAQ](http://www.mono-project.com/docs/faq/security/) (Perguntas frequentes sobre segurança no Mono).

Para se conectar ao Azure sem ignorar o protocolo TLS/SSL, o repositório de certificados do Unity Mono deve ser atualizado.

## <a name="using-mozroots-to-install-certificates"></a>Usar mozroots para instalar certificados

A ferramenta mozroots está incluída no Mono. Ele baixa e instala a lista do Mozilla de certificados raiz.

1. Abra o terminal do prompt de comando.

2. No terminal, navegue até o diretório **C:\Program Files\Unity\Editor\Data\MonoBleedingEdge\bin>**. O local exato pode ser diferente dependendo de onde você instalou o Unity em seu computador local.

3. Digite o seguinte comando e pressione **Enter** para executá-lo:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Você verá a seguinte saída (embora o número ou certificados adicionados possa ser diferente):

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Agora, você deve conseguir executar o projeto de exemplo sem receber erros relacionados ao TLS.

## <a name="next-step"></a>Próximas etapas

* [Testar a conexão de cliente](visual-studio-tools-for-unity-azure-connection.md)
