---
title: Propriedades do depurador Android (C++) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: a296ea142b13b9bdcda888a7f382de9eeb17a40a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="android-debugger-properties"></a>Propriedades do depurador Android

Propriedade | Descrição | Opções
--- | ---| ---
Tipo de Depurador | Especifica o tipo de código a ser depurado. | **Somente nativo**<br>**Somente Java**<br>
Destino de depuração | Especifica o emulador ou o dispositivo a ser usado para depuração. Se nenhum emulador estiver em execução, use o 'Gerenciador de AVD (Dispositivo Virtual Android)' para iniciar um dispositivo.
Pacote a ser inicializado | Especifica o local do .apk que será depurado. Escolha esta opção para especificar que um pacote específico (APK) deverá ser iniciado quando o aplicativo for depurado.
Atividade de inicialização | A atividade do Android usada para iniciar o aplicativo deve corresponder à que foi usada no manifesto. Pressione Aplicar para recuperar a lista do AndroidManifest.xml e populá-la dinamicamente.
Caminhos de pesquisa de símbolo adicionais | Caminho de pesquisa adicional para símbolos de depuração.
Caminhos de pesquisa de origem Java adicionais | Caminhos de pesquisa adicionais para arquivos de origem Java. (Aplica-se somente quando o tipo de depurador é somente Java).
