---
title: "Definir padrões para implantações empresariais do Visual Studio | Microsoft Docs"
description: "Políticas de domínio e outras operações de configuração de implantação corporativa do Visual Studio."
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 11bcc331150b1e1ab9a8058b3538bca411345c19
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Definir padrões para implantações empresariais do Visual Studio

Você pode definir políticas de Registro que afetam a implantação do Visual Studio. Essas políticas são globais para o novo instalador e afetam:

- Quando alguns pacotes compartilhados com outras versões ou instâncias estão instalados
- Onde os pacotes são armazenados em cache
- Se todos os pacotes são armazenados em cache

Você pode definir algumas dessas políticas usando as [opções de linha de comando](use-command-line-parameters-to-install-visual-studio.md), definir valores de registro no computador ou até mesmo distribuí-los usando a Política de Grupo em toda a organização.

## <a name="registry-keys"></a>Chaves do Registro

Há vários locais em que você pode definir padrões empresariais, para habilitar o controle por meio da Política de Grupo ou diretamente no Registro. O Visual Studio procura sequencialmente para verificar se políticas empresariais foram definidas. Assim que um valor de política é descoberto na ordem abaixo, as chaves restantes são ignoradas.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (em sistemas operacionais de 64 bits)

> [!IMPORTANT]
> Se você não definir a chave `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` e, em vez disso, definir uma das outras chaves, defina as outras duas chaves em sistemas operacionais de 64 bits. Esse problema é abordado em uma atualização futura do produto.

Alguns valores de registro são definidos automaticamente na primeira vez em que são usados, caso ainda não estejam definidos. Isso garante que as instalações subsequentes usem os mesmos valores. Esses valores são armazenados na segunda chave do Registro, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`.

Você pode definir os valores de registro a seguir:

| **Nome** | **Tipo** | **Padrão** | **Descrição** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | O diretório em que os manifestos de pacote e opcionalmente, as cargas são armazenados. Leia sobre como [desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md) para obter mais informações. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Manter cargas de pacote, mesmo após a instalação. Você pode alterar o valor a qualquer momento. Desabilitar a política removerá quaisquer payloads de pacote em cache para a instância que você reparar ou modificar. Leia sobre como [desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md) para obter mais informações. |
| `SharedInstallationPath` | `REG_SZ` ou `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | O diretório em que alguns pacotes compartilhados entre versões de instâncias do Visual Studio estão instalados. Você pode alterar o valor a qualquer momento, mas isso afetará apenas instalações futuras. Todos os produtos já instalados no local antigo não devem ser movidos ou poderão não funcionar corretamente. |

> [!IMPORTANT]
> Se você alterar a política do Registro `CachePath` após qualquer instalação, deverá mover o pacote de cache para o novo local e verificar se ele está protegido para que `SYSTEM` e `Administrators` tenham controle total e `Everyone` tenha acesso de leitura.
> A falha ao mover o cache existente ou protegê-lo pode causar problemas com instalações futuras.

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, consulte a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md) para obter dicas de solução de problemas. Além disso, você pode relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), no IDE do Visual Studio ou compartilhar uma sugestão conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579). É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas. Também é possível interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio) (exige uma conta do [GitHub](https://github.com/)).

## <a name="see-also"></a>Consulte também

 * [Instalar o Visual Studio](install-visual-studio.md)
 * [Desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md)
 * [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
