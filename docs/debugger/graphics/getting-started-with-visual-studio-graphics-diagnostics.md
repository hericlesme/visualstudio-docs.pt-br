---
title: "Guia de Introdução ao diagnóstico de gráficos do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59131181-1caa-4b7f-be4b-e84709634edf
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 577fd16d93bdfd1ad15bb3469495fdd1342a6994
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Guia de Introdução ao diagnóstico de gráficos do Visual Studio
Nesta seção você preparará usar o diagnóstico de gráficos pela primeira vez, em seguida, você capturar quadros de um aplicativo Direct3D e examine-os no analisador de gráficos.  
  
## <a name="requirements"></a>Requisitos  
 Para usar o diagnóstico de gráficos no Visual Studio, você deve usar o Visual Studio Enterprise, Visual Studio Professional ou Visual Studio Community.  Outras edições, incluindo o código do Visual Studio, não contém esse recurso.
 
 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]  
  
### <a name="windows-10-prerequisites"></a>Pré-requisitos do Windows 10  
 O recurso opcional do Windows *ferramentas de gráficos* fornece a infraestrutura de captura e reprodução que é exigida pelo diagnóstico de gráficos no Windows 10.  
  
 Para obter informações sobre como instalar as ferramentas de gráficos, consulte [instalar ferramentas de gráficos para 10 Windows](#InstallGraphicsTools).  
  
### <a name="windows-81-prerequisites"></a>Pré-requisitos do Windows 8.1  
 O Windows Software Development Kit (SDK) para Windows 8.1 fornece a infraestrutura de captura e reprodução que é exigida pelo diagnóstico de gráficos no Windows 8.1 e dá suporte ao desenvolvimento para Windows 8.1 e Windows 8.  
  
 [Baixe o Windows Software Development Kit (SDK) para Windows 8.1](https://msdn.microsoft.com/en-us/windows/desktop/bg162891.aspx)  
  
 Para usar uma máquina de reprodução remota que está executando o Windows 10 de uma máquina de desenvolvimento executando Windows 8.1, você deve instalar o SDK do Windows 10 no computador de desenvolvimento e o recurso opcional de ferramentas de gráficos no computador de reprodução.  
  
##  <a name="InstallGraphicsTools"></a>Instalar ferramentas de gráficos para Windows 10  
 No Windows 10, a infraestrutura de diagnóstico de gráficos é fornecida por um recurso opcional do Windows chamado *ferramentas de gráficos*. Este recurso é necessário para capturar e reproduzir informações de gráficos no Windows 10, independentemente se o aplicativo que está sendo capturado destinos de uma versão anterior do windows ou a versão do Direct3D que ele usa. Você pode optar por instalar o recurso ferramentas de gráficos antecipadamente; Caso contrário, será instalado sob demanda na primeira vez que você iniciar uma sessão de diagnóstico de gráficos do Visual Studio.  
  
#### <a name="to-install-graphics-tools-for-windows-10"></a>Para instalar as ferramentas de gráficos para o Windows 10  
  
1.  Na pesquisa, digite **aplicativos e recursos** e, em seguida, abra o **aplicativos e recursos** configurações.
  
3.  No lado direito do **aplicativos e recursos** caixa de diálogo, escolha **gerenciar recursos opcionais** (em **aplicativos e recursos**).

    O **gerenciar recursos opcionais** caixa de diálogo é exibida.
  
4.  No **gerenciar recursos opcionais** caixa de diálogo, escolha **adicionar um recurso**. É exibida uma lista de recursos opcionais que você pode instalar.  
  
5.  Selecione **ferramentas de gráficos** da lista de recursos, em seguida, escolha **instalar**.  
  
 O recurso ferramentas de gráficos também é instalado automaticamente quando você instala o SDK do Windows 10.  
  
> [!TIP]
>  O recurso ferramentas de gráficos opcional do Windows 10 fornece a funcionalidade de captura e reprodução leve — como o programa de captura de linha de comando **dxcap.exe**— que pode ser usado em cenários de diagnósticos em, teste e suporte computadores nos quais ferramentas de desenvolvedor não estiverem instaladas. Para obter mais informações, consulte o [a ferramenta de captura de linha de comando](command-line-capture-tool.md) tópico.  
  
## <a name="using-graphics-diagnostics-for-the-first-time"></a>Usando o diagnóstico de gráficos pela primeira vez  
 Agora que você tem tudo o que você precisa, você está pronto para começar a usar o diagnóstico de gráficos. Basta seguir estas etapas.  
  
### <a name="1---create-a-direct3d-app"></a>1 - criar um aplicativo Direct3D  
 Se você já tem seu próprio aplicativo Direct3D para explorar o diagnóstico de gráficos, muito bem! Caso contrário, use um dos seguintes:

- O **aplicativo do DirectX 11 (Universal do Windows)** ou **aplicativo do DirectX 12 (Universal do Windows)** modelos de projeto para Windows 10.
- O **DirectX App (Windows 8.1)** modelo de projeto para Windows 8.1.
- [Exemplo de Direct3D 12 UAP](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f) para Windows 10.  
- O [exemplo do jogo marble maze DirectX](https://code.msdn.microsoft.com/windowsapps/DirectX-Marble-Maze-Game-e4806345) para Windows 8.1.  
  
 Verifique se que você pode criar o aplicativo antes de continuar.  
  
### <a name="2---start-a-graphics-diagnostics-session"></a>2 - Inicie uma sessão de diagnóstico de gráficos  
 Agora você está pronto para começar a primeira sessão de diagnóstico de gráficos. No Visual Studio, no menu principal, escolha **depurar, gráficos, iniciar depuração de gráficos**, ou apenas pressione **Alt + F5**. Isso inicia o aplicativo com o diagnóstico de gráficos e exibe as janelas de sessão de diagnóstico no Visual Studio.  
  
> [!IMPORTANT]
>  Se você estiver executando o aplicativo no Windows 10 e ainda não tiver instalado o recurso opcional de ferramentas de gráficos, você será solicitado a fazê-lo agora. Você deve instalá-lo antes de poder usar o diagnóstico de gráficos no Windows 10.  
  
### <a name="3---capture-frames"></a>3 - capturar quadros  
 Você está pronto para capturar os quadros assim que seu aplicativo é iniciado.  
  
#### <a name="to-capture-single-frames"></a>Para capturar quadros único  
  
-   No Visual Studio, escolha o **capturar quadro** botão na janela de sessão de barra de ferramentas ou diagnóstico de gráficos. Ou, se seu aplicativo tiver foco, basta pressionar o **Print Screen** chave em seu teclado.
  
#### <a name="to-capture-a-sequence-of-frames"></a>Para capturar uma sequência de quadros  
  
-   No Visual Studio, na janela sessão de diagnóstico, defina **quadros a serem capturados** para o número de quadros que você deseja capturar na sequência, em seguida, capturar a sequência usando qualquer um dos métodos descritos acima para capturar quadros individuais.  
  
     Para capturar os quadros único novamente, defina **quadros a serem capturados** para *1*.  
  
 Quando você tiver terminado a captura de quadros apenas sair do aplicativo ou escolha o **parar** botão da barra de ferramentas de gráficos ou janela de sessão de diagnóstico.  
  
### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 - examine quadros capturados no analisador de gráficos  
 Agora você está pronto para examinar os quadros que acabou de ser capturada. Para iniciar a análise de um quadro, escolha o número do quadro do quadro que você deseja examinar na janela de sessão de diagnóstico. Isso abre o quadro de **analisador de gráficos**, onde você pode usar as ferramentas de diagnóstico de gráficos para examinar como o seu aplicativo usa Direct3D para rastrear problemas de renderização, ou usar o **análise de quadros** ferramenta para Entenda o desempenho.  
  
 Se você selecionou o quadro errado na janela de sessão de diagnóstico ou você deseja examinar um quadro diferente, você pode selecionar um novo do analisador de gráficos. No **renderizar destino** guia da janela de log de gráficos, abaixo da imagem de destino de renderização, expanda o **lista quadro** e, em seguida, escolha um quadro diferente para examinar.  
  
 Para saber mais sobre como usar as ferramentas do analisador de gráficos juntos, consulte o [exemplos](graphics-diagnostics-examples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Direct3D 12 gráficos](http://msdn.microsoft.com/en-us/52094ae3-3b44-4689-9ee7-1ba1b3a779cb)