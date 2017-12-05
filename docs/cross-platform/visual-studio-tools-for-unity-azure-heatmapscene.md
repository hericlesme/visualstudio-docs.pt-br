---
title: Passo a passo do HeatmapScene do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: E11DA08B-7341-4743-A817-0CAD59844305
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: f707052e0ec0b9cda60c111767800c1ce14d6103
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="heatmapscene-explanation"></a>Explicação sobre HeatmapScene

O HeatmapScene contém uma instância do prefab **LevelGeometry**. Dessa forma, as coordenadas das colisões carregadas do Azure são corretamente mapeadas para a arte de nível.

## <a name="heatmap-script"></a>Script do Mapa de Calor

### <a name="initializecrashlistasync"></a>InitializeCrashListAsync
`InitializeCrashListAsync` conecta-se à Tabela Fácil CrashInfo no Azure e usa <a href="https://msdn.microsoft.com/en-us/library/azure/jj554274(v=azure.10).aspx">`ToListAsync`</a> para adicionar todas as suas entradas a uma lista.

```
private async Task InitializeCrashListAsync()
 {
     Debug.Log("Downloading crash data from Azure...");

     for (int i = 0; i < numberOfAttempts; i++)
     {
         try
         {
             Debug.Log("Connecting... attempt " + (i +1));
             crashesFromServer = await crashesTable.ToListAsync();
             Debug.Log("Done downloading.");
             return;
         }
         catch (System.Exception e)
         {
             Debug.Log("Error connecting: " + e.Message);
         }

         if (i == numberOfAttempts - 1)
             Debug.Log("Connection failed. Check logs, try again later.");
         else
             await Task.Delay(500);
     }
 }
```

### <a name="spawnmarkersfromlist"></a>SpawnMarkersFromList
O `SpawnMarkersFromList` itera na lista de colisões recebidas do Azure e cria uma instância de um prefab de marcador de colisão para cada entrada.

```csharp
private void SpawnMarkersFromList()
{
    foreach (var item in crashesFromServer)
    {
        GameObject marker = GameObject.Instantiate(markerPrefab);
        marker.transform.position = new Vector3 { x = item.X, y = item.Y, z = item.Z };
    }
}
```

### <a name="deletecrashdataasync"></a>DeleteCrashDataAsync

O `DeleteCrashDataAsync` é chamado quando o usuário pressiona o botão **Limpar Dados**. Ele itera na lista local de colisões e chama <a href="https://msdn.microsoft.com/en-us/library/azure/jj554258(v=azure.10).aspx">`DeleteAsync`</a> para cada entrada. Isso define cada coluna de entrada **Deleted** na Tabela Fácil como **true**. `ToListAsync` ignora essas entradas excluídas.

```csharp
public async void DeleteCrashDataAsync()
{
    Debug.Log("Deleting crash data...");
    foreach (var item in crashesFromServer)
    {
        try
        {
            await crashesTable.DeleteAsync(item);
        }
        catch (System.Exception e)
        {
            Debug.Log("Error deleting crash data: " + e.Message);
        }
        Debug.Log("Done deleting crash data.");
    }
    SceneManager.LoadScene(SceneManager.GetActiveScene().name);
}
```

## <a name="next-step"></a>Próximas etapas

* [Explicação sobre LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)