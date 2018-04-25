---
title: Propriedades do depurador Android (C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 7d18125c6666a8eb68becd828da36ecdab077507
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="android-debugger-properties"></a>Propriedades do depurador Android

propriedade | Descrição | Opções
--- | ---| ---
Tipo de Depurador | Especifica o tipo de código a ser depurado. | **Somente nativo**<br>**Somente Java**<br>
Destino de depuração | Especifica o emulador ou o dispositivo a ser usado para depuração. Se nenhum emulador estiver em execução, use o 'Gerenciador de AVD (Dispositivo Virtual Android)' para iniciar um dispositivo.
Pacote a ser inicializado | Especifica o local do .apk que será depurado. Escolha esta opção para especificar que um pacote específico (APK) deverá ser iniciado quando o aplicativo for depurado.
Atividade de inicialização | A atividade do Android usada para iniciar o aplicativo deve corresponder à que foi usada no manifesto. Pressione Aplicar para recuperar a lista do AndroidManifest.xml e populá-la dinamicamente.
Caminhos de pesquisa de símbolo adicionais | Caminho de pesquisa adicional para símbolos de depuração.
Caminhos de pesquisa de origem Java adicionais | Caminhos de pesquisa adicionais para arquivos de origem Java. (Aplica-se somente quando o tipo de depurador é somente Java).
