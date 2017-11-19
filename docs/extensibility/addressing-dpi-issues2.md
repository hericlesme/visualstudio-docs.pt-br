---
title: "Endereçamento de DPI Problemas2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 359184aa-f5b6-4b6c-99fe-104655b3a494
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e944c8a998a3e8bba46d5018faf1b9103a91240
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="addressing-dpi-issues"></a>Resolvendo problemas de DPI
Um número crescente de dispositivos é fornecidos com telas "alta resolução". Normalmente, essas telas têm mais de 200 pixels por polegada (ppi). Trabalhar com um aplicativo nesses computadores exigirá o conteúdo a ser expandido para atender às necessidades de exibir o conteúdo em uma distância de exibição normal para o dispositivo. A partir de 2014, o destino principal de alta densidade exibe é móvel (tablets, laptops clamshell e celulares) de dispositivos de computação.  
  
 Windows 8.1 e posterior contém vários recursos para habilitar esses computadores trabalhar com exibições e ambientes em que o computador está conectado a ambos alta densidade e densidade padrão exibe ao mesmo tempo.  
  
-   Windows podem permitir que você ao conteúdo de escala para o dispositivo usando o "Tornar texto e outros itens maiores ou menores" configuração (disponível desde o Windows XP).  
  
-   Windows 8.1 e mais recente será dimensionado automaticamente conteúdo para a maioria dos aplicativos a serem consistente quando movidos entre exibições de diferentes densidades de pixel. Quando o vídeo principal é alta densidade (200% scaling) e a exibição secundária é densidade padrão (100%), Windows será dimensionado automaticamente o conteúdo da janela de aplicativo para baixo na exibição do secundária (1 pixel exibido para cada 4 pixels processados pelo aplicativo).  
  
-   Windows padrão será o direito de dimensionamento para a densidade de pixels e exibindo a distância para a exibição (Windows 7 e superior, OEM configurável).  
  
-   Windows pode dimensionar automaticamente conteúdo para cima 250% em novos dispositivos que excedem 280 ppi (a partir do Windows 8.1 S14).  
  
 O Windows tem uma maneira de lidar com o aumento da interface do usuário para tirar proveito de contagens de pixel maior. Um aplicativo aceita a este sistema declarando próprio "sistema de reconhecimento de DPI." Aplicativos que não fazem isso são expandidos pelo sistema. Isso pode resultar em uma experiência de usuário "difusa" onde o aplicativo inteiro é ampliada de pixel uniformemente. Por exemplo:  
  
 ![Problemas de DPI difusa](../extensibility/media/dpi-issues-fuzzy.png "DPI emite difusa")  
  
 Visual Studio aceita sendo reconhecimento de dimensionamento de DPI e, portanto, não está "virtualizado."  
  
 Windows (e o Visual Studio) aproveitam várias tecnologias de interface do usuário, que têm diferentes maneiras de lidar com definido pelo sistema de fatores de dimensionamento. Por exemplo:  
  
-   WPF mede os controles de forma independente de dispositivo (unidades, não em pixels). WPF UI dimensiona automaticamente para o DPI atual.  
  
-   Todos os tamanhos de texto, independentemente da estrutura de interface do usuário são expressos em pontos e então são tratados pelo sistema como independentes de DPI. Texto em Win32, WinForms e WPF já escalar verticalmente corretamente quando desenhada para o dispositivo de vídeo.  
  
-   Janelas e caixas de diálogo do Win32/WinForms tem meios para habilitar o layout é redimensionado com texto - por exemplo, por meio de grade, fluxo e painéis de layout de tabela. Elas permitem evitar locais de pixel embutido que não são dimensionados quando os tamanhos de fonte são aumentados.  
  
-   Ícones fornecidos pelo sistema ou recursos com base nas métricas do sistema (por exemplo, SM_CXICON e SM_CXSMICON) já estão dimensionados para cima.  
  
## <a name="older-win32-gdi-gdi-and-winforms-based-ui"></a>Win32 mais antigos (GDI, GDI+) e a interface do usuário com base em WinForms  
 Enquanto o WPF reconhece já alto DPI, grande parte de nosso código baseado em Win32/GDI não foi gravado originalmente com reconhecimento DPI em mente. Windows fornece APIs de dimensionamento de DPI. Correções para problemas de Win32 devem usá-los consistente em todo o produto. O Visual Studio fornece um auxiliar de biblioteca de classes para evitar duplicação de funcionalidade e garantir a consistência em todo o produto.  
  
## <a name="high-resolution-images"></a>Imagens de alta resolução  
 Esta seção é principalmente para os desenvolvedores de estender o Visual Studio 2013. Para Visual Studio 2015, use o serviço de imagem que é criado no Visual Studio. Você também pode encontrar o que você precisa de suporte/destino várias versões do Visual Studio e, portanto, usando o serviço de imagem no 2015 não é uma opção porque ele não existe nas versões anteriores. Esta seção é também, em seguida, para você.  
  
## <a name="scaling-up-images-that-are-too-small"></a>O dimensionamento das imagens que são muito pequenas  
 Imagens que são muito pequenas podem ser "expandidas" e processadas GDI e WPF usando alguns métodos comuns. Classes de auxiliar DPI gerenciadas estão disponíveis para integradores de Visual Studio internos e externos para dimensionamento bitmaps, ícones, imagestrips e imagelists do endereço. Com base em Win32 nativo C / C++ auxiliares estão disponíveis para dimensionamento HICON, HBITMAP, HIMAGELIST e VsUI::GdiplusImage. Dimensionamento de um bitmap normalmente requer somente uma alteração de uma linha depois de incluir uma referência à biblioteca auxiliar. Por exemplo:  
  
```cpp  
(Unmanaged)  VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
```  
  
```csharp  
(WinForms) DpiHelper.LogicalToDeviceUnits(ref image);  
```  
  
 Dimensionar um imagelist depende de imagelist é concluída no tempo de carregamento, ou é acrescentada em tempo de execução. Se estiver concluída no tempo de carregamento, chame LogicalToDeviceUnits() com imagelist como faria com um bitmap. Quando o código precisa carregar um bitmap individual antes de composição de imagelist, certifique-se de expandir o tamanho da imagem de imagelist:  
  
```csharp  
imagelist.ImageSize = DpiHelper.LogicalToDeviceUnits(imagelist.ImageSize);  
```  
  
 No código nativo, as dimensões podem ser dimensionadas durante a criação de imagelist da seguinte maneira:  
  
```cpp  
ImageList_Create(VsUI::DpiHelper::LogicalToDeviceUnitsX(16),VsUI::DpiHelper::LogicalToDeviceUnitsY(16), ILC_COLOR32|ILC_MASK, nCount, 1);  
```  
  
 Funções na biblioteca permitem especificar o algoritmo de redimensionamento. Quando imagens de escala a serem colocados no imagelists, certifique-se de especificar a cor de plano de fundo que é usada para a transparência ou use NearestNeighbor escala (que fará com que distorções 125% e 150%).  
  
 Consulte o <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> documentação no MSDN.  
  
 A tabela a seguir mostra exemplos de como as imagens devem ser dimensionadas em DPI correspondente fatores de dimensionamento. As imagens em verde denotam nossa prática recomendada a partir do Visual Studio 2013 (100 a 200% dimensionamento de DPI):  
  
 ![Problemas DPI dimensionamento](../extensibility/media/dpi-issues-scaling.png "problemas DPI dimensionamento")  
  
## <a name="layout-issues"></a>Problemas de layout  
 Problemas comuns de layout podem ser evitados principalmente ao manter pontos na interface de usuário dimensionado e relativas a um outro, em vez de locais absolutos (especificamente, em unidades de pixel). Por exemplo:  
  
-   Posições de texto do layout precisam ajustar a conta para imagens expandidos.  
  
-   Colunas em grades precisam ter larguras ajustadas para o texto expandidos.  
  
-   Tamanhos embutido ou espaço entre os elementos também precisará ser dimensionado. Tamanhos com base apenas nas dimensões de texto são normalmente bem, porque as fontes são expandidas automaticamente.  
  
 Funções de auxiliar estão disponíveis a <xref:Microsoft.VisualStudio.PlatformUI.DpiHelper> classe para permitir que a escala do eixo X e Y:  
  
-   LogicalToDeviceUnitsX/LogicalToDeviceUnitsY (funções permitem que o dimensionamento de X / eixo Y)  
  
-   espaço de int = DpiHelper.LogicalToDeviceUnitsX (10);  
  
-   altura de int = VsUI::DpiHelper::LogicalToDeviceUnitsY(5);  
  
 Há sobrecargas LogicalToDeviceUnits para permitir o dimensionamento de objetos, como Rect, ponto e tamanho.  
  
## <a name="using-the-dpihelper-libraryclass-to-scale-images-and-layout"></a>Usando a biblioteca DPIHelper/classe para redimensionar imagens e o layout  
 A biblioteca de auxiliar de DPI do Visual Studio está disponível em formulários nativos e gerenciados e pode ser usada fora do shell do Visual Studio por outros aplicativos.  
  
 Para usar a biblioteca, vá para o [exemplos de extensibilidade do Visual Studio VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples) e clonar o exemplo de alta DPI_Images_Icons  
  
 Nos arquivos de origem incluem VsUIDpiHelper.h e chamar as funções estáticas da classe VsUI::DpiHelper:  
  
```cpp  
#include "VsUIDpiHelper.h"  
  
int cxScaled = VsUI::DpiHelper::LogicalToDeviceUnitsX(cx);  
VsUI::DpiHelper::LogicalToDeviceUnits(&hBitmap);  
  
```  
  
> [!NOTE]
>  Não use as funções auxiliares no nível de módulo ou classe variáveis estáticas. A biblioteca também usa estatísticas de sincronização de threads e você pode ter problemas de ordem de inicialização. Converta essas estatísticas para variáveis de membro não estáticos, ou encapsulá-los em uma função (de modo que eles obtenham construídos no primeiro acesso).  
  
 Para acessar as funções do auxiliar DPI do código gerenciado que será executado dentro do ambiente do Visual Studio:  
  
-   O consumo de projeto deve fazer referência a versão mais recente do MPF de Shell. Por exemplo:  
  
    ```csharp  
    <Reference Include="Microsoft.VisualStudio.Shell.14.0.dll" />  
    ```  
  
-   Certifique-se de que o projeto tiver referências a **System**, **PresentationCore**, e **PresentationUI**.  
  
-   No código, use o **Microsoft.VisualStudio.PlatformUI** namespace e chamar funções estáticas da classe DpiHelper. Tipos com suporte (pontos, tamanhos, retângulos e assim por diante), existem desde dimensionada de funções de extensão que retornam novos objetos. Por exemplo:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    double x = DpiHelper.LogicalToDeviceUnitsX(posX);  
    Point ptScaled = ptOriginal.LogicalToDeviceUnits();  
    DpiHelper.LogicalToDeviceUnits(ref bitmap);  
  
    ```  
  
## <a name="dealing-with-wpf-image-fuzziness-in-zoomable-ui"></a>Lidando com o grau de seleção de imagem WPF na interface de usuário de zoom  
 No WPF, bitmaps são redimensionados automaticamente pelo WPF para o nível de zoom atual DPI usando um algoritmo de alta qualidade bicúbica (padrão), que funciona bem para imagens ou capturas de tela grandes, mas não é apropriado para os ícones de item de menu porque ela introduz confusão percebido .  
  
 Recomendações:  
  
-   Para a arte da imagem e faixas de logotipo, o padrão <xref:System.Windows.Media.BitmapScalingMode> redimensionamento modo pode ser usado.  
  
-   Para itens de menu e imagens iconografia o <xref:System.Windows.Media.BitmapScalingMode> deve ser usado quando não fazem com que outros artefatos de distorção eliminar a confusão (em 200% e % de 300).  
  
-   Para grande zoom níveis não múltiplos de 100% (por exemplo, 250% ou % 350), dimensionando imagens iconografia com bicúbica resulta em difusa, Desbotado da interface do usuário. Um resultado melhor é obtido pela primeira dimensionar a imagem com NearestNeighbor para o múltiplo maior de 100% (por exemplo, 200% ou 300%) e dimensionamento com bicúbica de lá. Consulte o caso especial: prescaling imagens do WPF para grande DPI níveis para obter mais informações.  
  
 A classe DpiHelper no namespace Microsoft.VisualStudio.PlatformUI fornece um membro <xref:System.Windows.Media.BitmapScalingMode> que pode ser usado para associação. Isso permitirá que o shell do Visual Studio controlar o bitmap dimensionamento modo em todo o produto uniformemente, dependendo do fator de dimensionamento de DPI.  
  
 Para usá-lo em XAML, adicione:  
  
```xaml  
xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
  
<Setter Property="RenderOptions.BitmapScalingMode" Value="{x:Static vs:DpiHelper.BitmapScalingMode}" />  
  
```  
  
 Shell do Visual Studio já define essa propriedade em caixas de diálogo e janelas de nível superior. Interface de usuário com base em WPF em execução no Visual Studio já herdará-lo. Se a configuração não se propaga às suas partes específicas da interface do usuário, ele pode ser definido no elemento raiz da interface do usuário XAML/WPF. Locais onde isso ocorre incluem pop-ups, nos elementos pai de Win32 e designers windows que são executados fora do processam, como Blend.  
  
 Algumas interfaces do usuário podem ser dimensionados independentemente do nível de zoom DPI conjunto do sistema, como o editor de texto do Visual Studio e designers baseado no WPF (área de trabalho do WPF e da Windows Store). Nesses casos, DpiHelper.BitmapScalingMode não deve ser usado. Para corrigir esse problema no editor, a equipe IDE criada uma propriedade personalizada denominada RenderOptions.BitmapScalingMode. Defina o valor da propriedade HighQuality ou NearestNeighbor dependendo do nível de zoom combinado do sistema e a interface do usuário.  
  
## <a name="special-case-prescaling-wpf-images-for-large-dpi-levels"></a>Caso especial: prescaling imagens do WPF para níveis DPI grandes  
 Para os níveis de zoom muito grandes que não sejam múltiplos de 100% (por exemplo, 250%, 350% e assim por diante), dimensionando imagens de iconografia com resultados bicúbica na interface do usuário e Desbotado. A impressão dessas imagens junto com o texto é praticamente o mesmo que uma ilusão ótica. As imagens parecem ser mais próximo ao olho e fora de foco em relação ao texto. O resultado de dimensionamento nesse tamanho ampliada pode ser melhorado com o primeiro dimensionar a imagem com NearestNeighbor para o múltiplo maior de 100% (por exemplo, 200% ou 300%) e dimensionamento com bicúbica para o restante (50% adicionais).  
  
 A seguir está um exemplo de como as diferenças nos resultados, onde a primeira imagem é dimensionada com o algoritmo de dimensionamento duplo aprimorado 100% -> 200% -> 250%, e apenas a uma segunda bicúbica 100% -> 250%.  
  
 ![DPI emite duplo exemplo dimensionamento](../extensibility/media/dpi-issues-double-scaling-example.png "DPI emite exemplo escala duplo")  
  
 Para habilitar a interface de usuário usar essa escala duplo, a marcação XAML para exibir cada elemento de imagem precisará ser modificada. Os exemplos a seguir demonstram como usar o dimensionamento de duplo em WPF no Visual Studio usando a biblioteca de DpiHelper e Shell.12/14.  
  
 Etapa 1: Prescale a imagem para 200%, 300% e assim por diante usando NearestNeighbor.  
  
 Prescale a imagem usando qualquer um conversor aplicado em uma associação, ou com uma extensão de marcação XAML. Por exemplo:  
  
```xaml  
<vsui:DpiPrescaleImageSourceConverter x:Key="DpiPrescaleImageSourceConverter" />  
  
<Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
  
<Image Source="{vsui:DpiPrescaledImage Images/Help.png}" Width="16" Height="16" />  
  
```  
  
 Se a imagem também precisa ser com tema (a maioria, se não todas, deve), a marcação pode usar um conversor de diferente que primeiro faz o tema da imagem e, em seguida, o dimensionamento previamente. A marcação pode usar o <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageConverter> ou <xref:Microsoft.VisualStudio.PlatformUI.DpiPrescaleThemedImageSourceConverter>, dependendo da saída de conversão desejada.  
  
```xaml  
<vsui:DpiPrescaleThemedImageSourceConverter x:Key="DpiPrescaleThemedImageSourceConverter" />  
  
<Image Width="16" Height="16">  
  <Image.Source>  
    <MultiBinding Converter="{StaticResource DpiPrescaleThemedImageSourceConverter}">  
      <Binding Path="Icon" />  
      <Binding Path="(vsui:ImageThemingUtilities.ImageBackgroundColor)"    
               RelativeSource="{RelativeSource Self}" />  
      <Binding Source="{x:Static vsui:Boxes.BooleanTrue}" />  
    </MultiBinding>  
  </Image.Source>  
</Image>  
```  
  
 Etapa 2: Verifique se que o tamanho final está correto para o DPI atual.  
  
 Porque WPF dimensionará a interface do usuário para o DPI atual usando a propriedade BitmapScalingMode definir o UIElement, deve ser um controle de imagem usando uma imagem prescaled como sua fonte aparecerá duas ou três vezes maior do que ele. A seguir estão algumas maneiras para esse efeito do contador:  
  
-   Se você souber que a dimensão da imagem original em 100%, você pode especificar o tamanho exato do controle de imagem. Esses tamanhos refletirá que o tamanho da interface do usuário antes de escalar é aplicado.  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" Width="16" Height="16" />  
    ```  
  
-   Se o tamanho da imagem original não for conhecido, um LayoutTransform pode ser usado para reduzir o objeto de imagem final. Por exemplo:  
  
    ```xaml  
    <Image Source="{Binding Path=SelectedImage, Converter={StaticResource DpiPrescaleImageSourceConverter}}" >  
        <Image.LayoutTransform>  
         <ScaleTransform  
             ScaleX="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}"  
             ScaleY="{x:Static vsui:DpiHelper.PreScaledImageLayoutTransformScale}" />  
        </Image.LayoutTransform>  
    </Image>  
    ```  
  
## <a name="enabling-hdpi-support-to-the-weboc"></a>Habilitar o suporte para o WebOC HDPI  
 Por padrão, controles WebOC (como o controle WebBrowser no WPF ou a interface de IWebBrowser2) não habilitam a detecção de HDPI e suporte. O resultado será um controle inserido com o conteúdo de vídeo é muito pequeno em uma exibição de alta resolução. A seguir descreve como habilitar o suporte a alto DPI em uma instância de WebOC web específico.  
  
 Implementa a interface IDocHostUIHandler (consulte o artigo do MSDN sobre o [IDocHostUIHandler](http://msdn.microsoft.com/library/aa753260.aspx) interface):  
  
```idl  
[ComImport, InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("BD3F23C0-D43E-11CF-893B-00AA00BDCE1A")]  
public interface IDocHostUIHandler  
{  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowContextMenu(  
        [In, MarshalAs(UnmanagedType.U4)] int dwID,  
        [In] POINT pt,  
        [In, MarshalAs(UnmanagedType.Interface)] object pcmdtReserved,  
        [In, MarshalAs(UnmanagedType.IDispatch)] object pdispReserved);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetHostInfo([In, Out] DOCHOSTUIINFO info);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ShowUI(  
        [In, MarshalAs(UnmanagedType.I4)] int dwID,  
        [In, MarshalAs(UnmanagedType.Interface)] object activeObject,  
        [In, MarshalAs(UnmanagedType.Interface)] object commandTarget,  
        [In, MarshalAs(UnmanagedType.Interface)] object frame,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int HideUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int UpdateUI();  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int EnableModeless([In, MarshalAs(UnmanagedType.Bool)] bool fEnable);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnDocWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int OnFrameWindowActivate([In, MarshalAs(UnmanagedType.Bool)] bool fActivate);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int ResizeBorder(  
        [In] COMRECT rect,  
        [In, MarshalAs(UnmanagedType.Interface)] object doc,  
        bool fFrameWindow);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateAccelerator(  
        [In] ref MSG msg,  
        [In] ref Guid group,  
        [In, MarshalAs(UnmanagedType.I4)] int nCmdID);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetOptionKeyPath(  
        [Out, MarshalAs(UnmanagedType.LPArray)] string[] pbstrKey,  
        [In, MarshalAs(UnmanagedType.U4)] int dw);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetDropTarget(  
        [In, MarshalAs(UnmanagedType.Interface)] IOleDropTarget pDropTarget,  
        [MarshalAs(UnmanagedType.Interface)] out IOleDropTarget ppDropTarget);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int GetExternal([MarshalAs(UnmanagedType.IDispatch)] out object ppDispatch);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int TranslateUrl(  
        [In, MarshalAs(UnmanagedType.U4)] int dwTranslate,  
        [In, MarshalAs(UnmanagedType.LPWStr)] string strURLIn,  
        [MarshalAs(UnmanagedType.LPWStr)] out string pstrURLOut);  
    [return: MarshalAs(UnmanagedType.I4)]  
    [PreserveSig]  
    int FilterDataObject(  
        IDataObject pDO,  
        out IDataObject ppDORet);  
    }   
```  
  
 Opcionalmente, implemente a interface ICustomDoc (consulte o artigo do MSDN sobre o [ICustomDoc](http://msdn.microsoft.com/library/aa753272.aspx) interface):  
  
```idl  
[InterfaceType(ComInterfaceType.InterfaceIsIUnknown),  
 Guid("3050F3F0-98B5-11CF-BB82-00AA00BDCE0B")]  
public interface ICustomDoc  
{  
    void SetUIHandler(IDocHostUIHandler pUIHandler);  
}   
```  
  
 Associe a classe que implementa IDocHostUIHandler com documentos do WebOC. Se você implementou a interface ICustomDoc acima, assim que a propriedade de documento do WebOC for válida, converta-o para um ICustomDoc e chame o método SetUIHandler, passando a classe que implementa IDocHostUIHandler.  
  
```csharp  
// "this" references that class that owns the WebOC control and in this case also implements the IDocHostUIHandler interface  
ICustomDoc customDoc = (ICustomDoc)webBrowser.Document;  
customDoc.SetUIHandler(this);  
  
```  
  
 Se você não implementou a interface ICustomDoc, em seguida, assim que a propriedade de documento do WebOC for válida, você precisará convertê-lo para um IOleObject e chame o método SetClientSite, passando a classe que implementa IDocHostUIHandler. Defina o sinalizador DOCHOSTUIFLAG_DPI_AWARE no DOCHOSTUIINFO passado para a chamada do método do GetHostInfo:  
  
```csharp  
public int GetHostInfo(DOCHOSTUIINFO info)  
{  
    // This is what the default site provides.  
    info.dwFlags = (DOCHOSTUIFLAG)0x5a74012;  
    // Add the DPI flag to the defaults  
    info.dwFlags |=.DOCHOSTUIFLAG.DOCHOSTUIFLAG_DPI_AWARE;  
    return S_OK;  
}  
```  
  
 Isso deve ser tudo o que você precisa obter seu controle WebOC para dar suporte a HPDI.  
  
## <a name="tips"></a>Dicas  
  
1.  Se a propriedade de documento no controle WebOC for alterado, você precisará reassociar o documento com a classe IDocHostUIHandler.  
  
2.  Se as opções acima não funcionar, há um problema conhecido com o WebOC não separação a mudança para o sinalizador DPI. É a maneira mais confiável de corrigir isso alternar o zoom óptico de WebOC, duas chamadas significado com dois valores diferentes para a porcentagem de zoom. Além disso, se essa solução alternativa é necessária, pode ser necessário para executá-lo em todas as chamadas de navegar.  
  
    ```csharp  
    // browser2 is a SHDocVw.IWebBrowser2 in this case  
    // EX: Call the Exec twice with DPI%-1 and then DPI% as the zoomPercent values  
    IOleCommandTarget cmdTarget = browser2.Document as IOleCommandTarget;  
    if (cmdTarget != null)  
    {  
        object commandInput = zoomPercent;  
        cmdTarget.Exec(IntPtr.Zero,  
                       OLECMDID_OPTICAL_ZOOM,  
                       OLECMDEXECOPT_DONTPROMPTUSER,  
                       ref commandInput,  
                       ref commandOutput);  
    }  
    ```