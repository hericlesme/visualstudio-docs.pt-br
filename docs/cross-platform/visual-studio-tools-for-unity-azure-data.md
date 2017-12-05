---
title: Passo a passo de modelo de dados do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="create-data-model-classes"></a>Criar classes de modelo de dados

O projeto do Unity deve conter classes de modelo de dados que correspondam com as tabelas criadas no back-end de Aplicativo Móvel do Azure.

## <a name="create-the-crashinfo-class"></a>Criar a classe CrashInfo

1. No Unity, adicione uma nova pasta no diretório **Ativos** raiz, denominada **Scripts**. Dentro da nova pasta Scripts, criar outra pasta denominada **Modelos de dados**. Isso é somente para organização.

2. Dentro da nova pasta Modelos de Dados, crie um novo script em C# chamado **CrashInfo**.

3. Abra o novo script `CrashInfo`, exclua qualquer código de modelo, incluindo a declaração de classe e instruções using, e adicione o seguinte:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Para que o passo a passo funcione corretamente, o nome da classe de modelo de dados deve corresponder ao nome da Tabela Fácil criada no back-end de Aplicativo Móvel do Azure.

## <a name="create-the-highscoreinfo-class"></a>Criar a classe HighScoreInfo

1. Na pasta Modelos de dados, crie um novo script em C# chamado **HighScoreInfo**.

2. Abra o novo script `HighScoreInfo`, exclua qualquer código de modelo, incluindo a declaração de classe e instruções using, e adicione o seguinte:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Próximas etapas

  * [Implementar o MobileServiceClient do Azure](visual-studio-tools-for-unity-azure-mobile-client.md)
