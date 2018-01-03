---
title: Passo a passo do RaceScene do Azure para as Ferramentas do Visual Studio para Unity | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1F9304E8-0F1B-4325-8BED-FE3EB0ADCE8D
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 7dc57628774624975cc6ede5bd241f322472bfe6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="racescene-explanation"></a>Explicação sobre o RaceScene

O RaceScene usa [ativos padrão](https://www.assetstore.unity3d.com/en/#!/content/32351) de Unity para compor a jogabilidade e o nível básicos de corrida. Nesta seção, os GameObjects relevantes e seus scripts serão explicados na ordem em que estão listados na hierarquia do RaceScene, conforme exibido na captura de tela abaixo.

![RaceScene](media/vstu_azure-racescene-explanation-image1.png)

## <a name="multipurposecamerarig"></a>MultipurposeCameraRig

O **MultipurposeCameraRig** provém do pacote de recursos padrão **Cameras**. Suas propriedades de Inspetor foram ajustadas para seguir o Carro a uma velocidade apropriada.

## <a name="levelgeometry"></a>LevelGeometry

O prefab LevelGeometry é um GameObject vazio usado para organização. Seu GameObjects filho compõe o espaço jogável. O pisos, paredes, rampas e obstáculos são todos criados com base em prefabs no pacote de recursos padrão **Prototyping**.

**Uma observação importante** é que, para que um objeto seja testado quanto a colisões que são registradas no Azure, ele deve ter a marca **Wall** aplicada.

![RaceScene](media/vstu_azure-racescene-explanation-image2.png)

## <a name="car"></a>Car

O prefab **Car** é do pacote de recursos padrão **Vehicles**. A única modificação é que o componente de script **RecordCrashInfo** é adicionado.

### <a name="recordcrashinfo"></a>RecordCrashInfo

Esse script verifica as colisões em `OnCollisionEnter` e as registra em uma lista. `crashRecordingCooldown` e `crashRecordingMinVelocity` limitam o que o jogo considera uma colisão para manter um conjunto de dados relevante.

Quando o evento `RaceFinished` é acionado, o `UploadNewCrashDataAsync` envia cada colisão da lista para a Tabela Fácil CrashInfo no Azure.

```Csharp
using System.Collections;
using System.Collections.Generic;
using System.Threading.Tasks;
using UnityEngine;

public class RecordCrashInfo : MonoBehaviour
{
    [Tooltip("Time in seconds after a crash before a new crash can be recorded.")]
    [SerializeField]
    private float crashRecordingCooldown = 1;

    [Tooltip("How fast car must be traveling before crash can be recorded.")]
    [SerializeField]
    private float crashRecordingMinVelocity = 8;

    [SerializeField]
    private Rigidbody carRigidbody;

    [SerializeField]
    private GameObject crashMarkerPrefab;

    [Tooltip("If turned on, crash markers spawn when the player crashes.")]
    [SerializeField]
    private bool spawnDebugMarkers = false;

    private bool isOnCooldown = false;
    private bool meetsMinVelocity = false;
    private bool isRaceFinished = false;

    private List<CrashInfo> newCrashes = new List<CrashInfo>();

    private void LateUpdate()
    {
        // We have to update this in LateUpdate as opposed to checking in OnCollisionEnter.
        // The car's velocity has already decreased from crashing by the time
        // OnCollisionEnter gets called.

        meetsMinVelocity = carRigidbody.velocity.magnitude >= crashRecordingMinVelocity;
    }

    private void OnCollisionEnter(Collision collision)
    {
        if (!isRaceFinished && collision.gameObject.tag == "Wall" && !isOnCooldown && meetsMinVelocity)
        {
            Debug.Log("Collided with wall!");

            newCrashes.Add(new CrashInfo
            {
                X = collision.transform.position.x,
                Y = collision.transform.position.y,
                Z = collision.transform.position.z
            });

            if (spawnDebugMarkers && Debug.isDebugBuild)
                Instantiate(crashMarkerPrefab, collision.transform.position, Quaternion.identity);

            isOnCooldown = true;
            StartCoroutine(Cooldown());
        }  
    }

    private IEnumerator Cooldown()
    {
        yield return new WaitForSeconds(crashRecordingCooldown);

        isOnCooldown = false;
    }

    private void OnRaceFinished()
    {
        Task.Run(UploadNewCrashDataAsync);
    }

    private async Task UploadNewCrashDataAsync()
    {
        var crashTable = AzureMobileServiceClient.Client.GetTable<CrashInfo>();

        try
        {
            Debug.Log("Uploading crash data to Azure...");

            foreach (var item in newCrashes)
            {
                await crashTable.InsertAsync(item);
            }
            Debug.Log("Finished uploading crash data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading crash data: " + e.Message);
        }

    }

    private void OnEnable()
    {
        Checkpoint.RaceFinished += OnRaceFinished;
    }

    private void OnDisable()
    {
        Checkpoint.RaceFinished -= OnRaceFinished;
    }

}
```

## <a name="checkpoints"></a>checkpoints

O nível tem quatro GameObjects com o componente de script **Checkpoint**. Os pontos de verificação garantem que o jogador não possa concluir a corrida percorrendo a pista na direção incorreta. Eles também detectam quando o jogador termina a corrida. Nesse momento é quando o evento `RaceFinished` é invocado.

## <a name="invisible-collision"></a>Colisão invisível

Cubos primitivos padrão, com seus componentes MeshRenderer desabilitados, são usados como colisão invisível a fim de manter o jogador dentro dos limites. Além disso, o material físico **Bouncy** é aplicado para garantir que os carros em voo rebatam nas paredes invisíveis de forma satisfatória e para impedir que o jogador bata em uma parede invisível, deslizando nela e repousando sobre uma parede visível.

## <a name="recordhighscore"></a>RecordHighScore

Esse script verifica se o jogador alcançou um novo recorde. Se ele alcançou, o script exibe o `enterNamePopup`, que permite que o jogador insira seu nome e clique em **Enviar**.

Quando o nome de um jogador é enviado, o `UploadNewHighScoreAsync` é chamado e o novo recorde é enviado para a Tabela Fácil HighScoreInfo no Azure.

```csharp
using System.Collections;
using System.Collections.Generic;
using Microsoft.WindowsAzure.MobileServices;
using UnityEngine;
using System.Threading.Tasks;
using System;
using System.Linq;
using UnityEngine.UI;

public class RecordHighScore : MonoBehaviour
{
    [SerializeField]
    private InputField nameInputField;

    [SerializeField]
    private CanvasGroup enterNamePopup;

    private List<HighScoreInfo> highScores;
    private string playerName = string.Empty;

    private async void Start()
    {
        ShowEnterNamePopup(false);
        highScores = await Leaderboard.GetTopHighScoresAsync();
    }

    private void ShowEnterNamePopup(bool shouldShow)
    {
        enterNamePopup.alpha = shouldShow ? 1 : 0;
        enterNamePopup.interactable = shouldShow;
    }

    public void SubmitButtonClicked()
    {
        playerName = nameInputField.text;
    }

    private async void OnAfterMostRecentScoreSet(float newScore)
    {
        bool isNewHighScore = CheckForNewHighScore(newScore);

        if (isNewHighScore)
        {
            Debug.Log("New High Score!");
            await GetPlayerNameAsync();
            await UploadNewHighScoreAsync(newScore);
        }
        else
        {
            Debug.Log("No new high score.");
        }
    }

    private async Task GetPlayerNameAsync()
    {
        // Wait a bit before showing the popup.
        // This just helps the player experience feel
        // less jarring.
        await Task.Delay(2000);
        ShowEnterNamePopup(true);

        // Wait until the player enters a name and clicks submit.
        // OnSubmitButtonClicked will set the playerName.
        while (playerName == string.Empty)
        {
            await Task.Delay(100);
        }

        ShowEnterNamePopup(false);
    }

    private bool CheckForNewHighScore(float newScore)
    {
        Debug.Log("Checking for a new high score...");

        bool isHighScoreListFull = highScores.Count >= Leaderboard.SizeOfHighScoreList;
        var lowerScores = highScores.Where(x => x.Time > newScore);

        return lowerScores.Count() > 0 || !isHighScoreListFull;
    }

    private async Task UploadNewHighScoreAsync(float newScore)
    {
        var newHighScoreInfo = new HighScoreInfo { Name = playerName, Time = newScore };

        try
        {
            Debug.Log("Uploading high score data to Azure...");

            await Leaderboard.HighScoreTable.InsertAsync(newHighScoreInfo);

            Debug.Log("Finished uploading high score data.");
        }
        catch (System.Exception e)
        {
            Debug.Log("Error uploading high score data: " + e.Message);
        }
    }

    private void OnEnable()
    {
        LapTimer.AfterMostRecentScoreSet += OnAfterMostRecentScoreSet;
    }

    private void OnDisable()
    {
        LapTimer.AfterMostRecentScoreSet -= OnAfterMostRecentScoreSet;
    }

}
```

## <a name="next-step"></a>Próximas etapas

* [Explicação sobre HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md).
