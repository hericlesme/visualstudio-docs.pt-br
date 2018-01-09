---
title: "Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fbea34afa4e82ea360a0dfefe4f18dc74d11f19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Aplicar chaves do produto (Product Keys) durante a implantação do Visual Studio
É possível aplicar a chave do produto (Product Key) de forma programática como parte de um script usado para automatizar a implantação do Visual Studio. Você pode definir a chave do produto (Product Key) em um dispositivo de forma programática durante a instalação do Visual Studio ou após a conclusão de uma instalação.

## <a name="apply-the-license-after-installation"></a>Aplicar a licença após a instalação
 É possível ativar uma versão instalada do Visual Studio com uma chave do produto (Product Key) usando o utilitário `StorePID.exe` nos computadores de destino no modo sem confirmação. `StorePID.exe` é um utilitário instalado com o Visual Studio 2017 no seguinte local padrão: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Execute `StorePID.exe` com privilégios elevados, usando um agente do System Center ou em um prompt de comandos com privilégios elevados. Em seguida, informe a chave do produto (Product Key) e o MPC (código de produto da Microsoft).

>[!IMPORTANT]
> Verifique se você incluiu os traços na chave do produto (Product Key).

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 O exemplo a seguir mostra uma linha de comando para aplicar a licença ao Visual Studio 2017 Enterprise, que tem um MPC de 08860, uma chave do produto (Product Key) `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` e pressupõe um local padrão para a instalação:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 A seguinte tabela lista os códigos MPC para cada edição do Visual Studio:

| Edição do Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Se `StorePID.exe` aplicar a chave do produto (Product Key) com êxito, ele retornará um `%ERRORLEVEL%` de 0. Se encontrar erros, ele retornará um dos códigos a seguir, dependendo da condição de erro:

| Erro                     | Código |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também
 * [Instalar o Visual Studio](../install/install-visual-studio.md)
 * [Criar uma instalação offline do Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
