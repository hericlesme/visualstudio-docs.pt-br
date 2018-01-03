---
title: "Passo a passo da conexão do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs"
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 516A8FB2-8DFF-4BAB-8116-FDCD1C228DB3
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: cb2ce447f21231b98d6464824ba7d088fee16cce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="test-the-client-connection"></a>Testar a conexão de cliente

Agora que o singleton AzureMobileServiceClient foi criado, é hora de testar a conexão de cliente.

## <a name="create-the-testclientconnection-script"></a>Criar o script TestClientConnection

1. Na pasta **Scripts** no Unity, crie um novo script em C# chamado **TestClientConnection**.

2. Abra o script no Visual Studio, exclua qualquer código de modelo e adicione o seguinte:

  ```csharp
  using System.Collections.Generic;
  using UnityEngine;
  using System.Threading.Tasks;
  using System;
  using System.Linq;
  using Microsoft.WindowsAzure.MobileServices;

  public class TestClientConnection : MonoBehaviour
  {
      void Start()
      {
          Task.Run(TestTableConnection);
      }

      private async Task TestTableConnection()
      {
          var table = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

          Debug.Log("Testing ToListAsync...");
          await TestToListAsync(table);

          Debug.Log("Testing InsertAsync...");
          await TestInsertAsync(table);

          Debug.Log("Testing DeleteAsync...");
          await TestDeleteAsync(table);

          Debug.Log("All testing complete.");
      }

      private async Task TestInsertAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await TestToListAsync(table);
              var initialCount = allEntries.Count();

              await table.InsertAsync(new CrashInfo { X = 1, Y = 2, Z = 3 });

              allEntries = await TestToListAsync(table);
              var newCount = allEntries.Count();

              Debug.Assert(newCount == initialCount + 1, "InsertAsync failed!");
          }
          catch (Exception)
          {
              throw;
          }
      }

      private async Task<List<CrashInfo>> TestToListAsync(IMobileServiceTable<CrashInfo> table)
      {
          try
          {
              var allEntries = await table.ToListAsync();
              Debug.Assert(allEntries != null, "ToListAsync failed!");
              return allEntries;
          }
          catch (Exception)
          {

              throw;
          }
      }

      private async Task TestDeleteAsync(IMobileServiceTable<CrashInfo> table)
      {
          var allEntries = await TestToListAsync(table);

          foreach (var item in allEntries)
          {
              try
              {
                  await table.DeleteAsync(item);
              }
              catch (Exception)
              {
                  throw;
              }
          }

          allEntries = await TestToListAsync(table);

          Debug.Assert(allEntries.Count() == 0, "DeleteAsync failed!");
      }
  }
  ```

3. No menu **GameObject** do Unity, selecione **GameObject > Criar Vazio** para criar um GameObject vazio na cena Unity. Renomeie-o como **TestClientConnection**.

4. **Arraste** o script TestClientConnection da janela **Projeto** do Unity para o GameObject TestClientConnection na janela **Hierarchy**.

5. No menu do Unity, selecione **Arquivo > Salvar cena como...**. Nomeie a cena como **Teste de Conexão de Cliente** e clique em **Salvar**.

5. Clique no botão **Reproduzir** no Unity e observe a janela do Console. Confirme se nenhuma das asserções falharam.

6. Abra a Tabela Fácil CrashInfo no Portal do Azure. Agora, ela deve ter uma entrada com coordenadas **X, Y, Z** iguais a **(1, 2, 3)** e um valor de **true** na coluna **deleted**. Sempre que você executar o teste, uma nova entrada com os mesmos valores, mas uma ID exclusiva, deverá ser adicionada à tabela.

  ![Entrada da Tabela Fácil](media/vstu_azure-test-client-connection-image1.png)

## <a name="next-step"></a>Próximas etapas
* [Importar os ativos de jogos de exemplo](visual-studio-tools-for-unity-azure-game-assets.md).
