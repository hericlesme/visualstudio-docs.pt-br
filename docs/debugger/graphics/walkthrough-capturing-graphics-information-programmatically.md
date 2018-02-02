---
title: "Passo a passo: Capturando informações de gráficos de forma programática | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a5a8aeec2421b92057ba414b5cf23b1770b1f761
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>Instruções passo a passo: capturando informações de gráfico de forma programática
É possível usar o Diagnóstico de Gráficos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para capturar de forma programática informações gráficas de um aplicativo Direct3D.  
  
 Captura programática é útil em cenários como:  
  
-   Iniciar captura programaticamente quando seu aplicativo de gráficos não usa a cadeia de troca presente, como quando ele processa uma textura.  
  
-   Iniciar captura programaticamente quando seu aplicativo não seja processada, como quando ele usa DirectCompute para executar cálculos.  
  
-   Chamar `CaptureCurrentFrame`quando um problema de processamento é difícil de prever e capturar em testes manuais, mas pode ser previsto programaticamente usando informações sobre o estado do aplicativo em tempo de execução.  
  
##  <a name="CaptureDX11_2"></a>Captura programática no Windows 10  
 Esta parte do passo a passo demonstra Captura programática em aplicativos que usam a API do DirectX 11.2 no Windows 10, que usa o método de captura robusta.
  
 Esta seção mostra como fazer estas tarefas:  
  
-   Preparando o aplicativo para usar a captura programática  
  
-   Obtendo a interface IDXGraphicsAnalysis  
  
-   Capturando informações de gráficos  
  
> [!NOTE]
>  As implementações anteriores do Captura programática baseava-se em ferramentas remotas para Visual Studio para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para fornecer a funcionalidade de captura.
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>Preparando o aplicativo para usar a captura programática  
 Para usar a captura programática em seu aplicativo, ele deve incluir os cabeçalhos necessários. Esses cabeçalhos são parte do SDK do Windows 10.  
  
##### <a name="to-include-programmatic-capture-headers"></a>Para incluir cabeçalhos de captura programática  
  
-   Inclua estes cabeçalhos no arquivo de origem em que a interface IDXGraphicsAnalysis será definida:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Não inclua a cabeçalho arquivo vsgcapture.h—which dá suporte à captura programática em Windows 8.0 e anterior — realizem captura programática em seus aplicativos do Windows 10. Esse cabeçalho não é compatível com o DirectX 11.2. Se esse arquivo é incluído após o cabeçalho d3d11_2.h for incluído, o compilador emite um aviso. Se houver vsgcapture.h antes de d3d11_2.h, o aplicativo não será iniciado.  
  
    > [!NOTE]
    >  Se o junho de 2010 DirectX SDK está instalado em seu computador e o caminho de inclusão do seu projeto contém `%DXSDK_DIR%includex86`, mova-o para o final do caminho de inclusão. Faça o mesmo com o caminho da biblioteca.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>Obtendo a interface IDXGraphicsAnalysis  
 Antes de capturar informações de gráficos do DirectX 11.2, você precisa obter a interface de depuração DXGI.  
  
> [!IMPORTANT]
>  Ao usar a captura programática, você ainda deve executar seu aplicativo com o diagnóstico de gráficos (Alt + F5 no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]) ou o [a ferramenta de captura de linha de comando](command-line-capture-tool.md).  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>Para obter a interface IDXGraphicsAnalysis  
  
-   Use o código a seguir para ligar a interface IDXGraphicsAnalysis à interface de depuração DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Não se esqueça de verificar o `HRESULT` retornado por `DXGIGetDebugInterface1` para garantir que você obtenha uma interface válida antes de usá-la:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Se `DXGIGetDebugInterface1` retorna `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`), verifique se o aplicativo está em execução com o diagnóstico de gráficos (Alt + F5 em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]).  
  
### <a name="capturing-graphics-information"></a>Capturando informações de gráficos  
 Agora que você tem uma interface `IDXGraphicsAnalysis` válida, é possível usar `BeginCapture` e `EndCapture` para capturar informações gráficas.  
  
##### <a name="to-capture-graphics-information"></a>Para capturar informações gráficas  
  
-   Para iniciar a captura de informações gráficas, use `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     A captura começa assim que `BeginCapture` é chamado e não aguarda o início do próximo quadro. A captura para quando o quadro atual é apresentado ou quando você chama `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="next-steps"></a>Próximas etapas  
 Este passo a passo demonstrou como capturar informações gráficas de forma programática. Como próxima etapa, considere esta opção:  
  
-   Aprenda a analisar informações gráficas capturadas usando as ferramentas de diagnóstico de gráficos. Consulte [visão geral](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Capturando informações de gráficos](walkthrough-capturing-graphics-information.md)   
 [Capturando informações de gráficos](capturing-graphics-information.md)   
 [Ferramenta de captura de linha de comando](command-line-capture-tool.md)