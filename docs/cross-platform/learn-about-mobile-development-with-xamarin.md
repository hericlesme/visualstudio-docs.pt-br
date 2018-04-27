---
title: Saiba mais sobre desenvolvimento móvel com o Xamarin | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.prod: xamarin
ms.technology: xamarin-tools
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: abeac53d6907603d6158c483095152d0f4ab2c5e
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Saiba mais sobre desenvolvimento móvel com o Xamarin

Este artigo lista várias visões gerais que podem ajudá-lo a entender o desenvolvimento de aplicativos móveis multiplataforma com o Xamarin. Se você não ainda tiver instalado o Visual Studio e o Xamarin, inicie primeiro o processo de [Instalação](../cross-platform/setup-and-install.md), depois volte aqui para trabalhar com esses recursos enquanto os instaladores estão em execução.  
  
> [!NOTE]
> Salvo indicação contrária, inicialmente é possível ler somente as páginas vinculadas diretamente daqui e não páginas secundárias. Se o processo de instalação ainda estiver em execução após você concluir esta lista, fique à vontade para voltar e explorar tópicos adicionais.  
>   
> Também fique à vontade para examinar os tópicos marcados como "Fundamentos" e para voltar aos tópicos de "Aprofundamento" mais tarde.  
  
## <a name="essentials-introduction-to-xamarin"></a>Fundamentos: Introdução ao Xamarin  

*10 a 20 minutos*  
  
1.  [Aplicativos móveis no Visual Studio com Xamarin](https://www.visualstudio.com/xamarin/) (visualstudio.com) fornece um rápido resumo das principais características do Xamarin.  
  
2.  [Building Cross-Platform Mobile Apps using C# and Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Criando aplicativos móveis de plataforma cruzada usando C# e Visual Studio) (Channel9, 15m16s) com o grande especialista em Xamarin, James Montemagno. Os primeiros três minutos são uma visão geral do Xamarin, seguida de demonstrações de código.  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>Fundamentos: Visão geral do ambiente do Visual Studio e do Xamarin  

*5 a 15 minutos*  
  
-   Você fará a maior parte do trabalho no computador Windows com o Visual Studio e o Xamarin instalados. Nesse computador, você cria aplicativos Android e Windows, executa e depura esses aplicativos na área de trabalho, em dispositivos ou em emuladores diretamente. Também é possível criar, executar e depurar aplicativos iOS remotamente usando o Mac. O Visual Studio no computador Windows também pode se conectar ao designer de storyboard iOS e ao simulador de iOS.  
  
-   O Mac com o Xcode e o Visual Studio para Mac instalados funciona como o host de build, o host de assinatura e o ambiente de tempo de execução para aplicativos iOS. O computador Windows delega os builds do iOS a esse Mac. O aplicativo é executado em um simulador do iOS no Mac, ou diretamente em um dispositivo vinculado conectado ao Mac. Você pode interagir com o aplicativo no Mac, mas realizar a experiência de depuração no Visual Studio.
  
Essas relações são ilustradas abaixo.  
  
![O relacionamento entre computadores de desenvolvimento Windows e Mac em um ambiente de Xamarin](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Saiba 1")  

> [!NOTE]
> O Windows Phone é mostrado neste diagrama para fins de integridade. Ao usar a plataforma Xamarin, a opção de compartilhamento de código recomendada é uma biblioteca .NET Standard 2.0, que é incompatível com dispositivos Windows Phone ou Windows 10 Mobile. 

Leia mais sobre como trabalhar com aplicativos iOS em [Introdução ao Xamarin.iOS para Visual Studio](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/).
  
## <a name="essentials-how-projects-are-structured"></a>Fundamentos: Como projetos são estruturados  

*10 a 30 minutos*  
  
1.  [Opções de compartilhamento de código](/xamarin/cross-platform/app-fundamentals/code-sharing/). Para novos aplicativos, você deve usar uma biblioteca do .NET Standard para compartilhar o código. A maior parte do código da lógica de negócios reside na biblioteca do .NET Standard, incluindo o acesso a bancos de dados, chamadas a APIs REST e chamadas a componentes portáteis do Xamarin. (Confira [Aprofundamento: componentes do Xamarin](#components) no final deste artigo). O código da interface do usuário comum escrito com o Xamarin.Forms também reside em uma biblioteca do .NET Standard.  
  
2.  (Opcional) O [Estudo de caso: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) descreve algumas práticas recomendadas para o design e a estrutura de um aplicativo completo, incluindo a estruturação do projeto com um código compartilhado que separa os dados, acesso a dados e camadas de negócios.  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>Fundamentos: camadas de interface do usuário nativas e do Xamarin.Forms  

*10 a 40 minutos*  
  
O Xamarin oferece duas maneiras de criar excelentes aplicativos: Xamarin nativo e Xamarin.Forms.  
  
Com o Xamarin nativo, você escreve um código de interface do usuário separado para cada plataforma de destino: iOS, Android e Windows.  Com essa abordagem, você tem acesso direto às APIs específicas da plataforma para projetar uma experiência de interface do usuário personalizada para cada plataforma.  Você também tem acesso completo aos controles e ao designer nativo para cada plataforma para ajudar na compilação da interface do usuário respectiva.  
  
O Xamarin.Forms fornece um conjunto geral de APIs que permite escrever uma camada de interface do usuário compartilhada para todas as plataformas em uma única biblioteca do .NET Standard.  O Xamarin.Forms executa a renderização para controles nativos em cada plataforma de destino para fornecer uma aparência nativa.  Em vez de usar um designer, você cria a interface do usuário usando C# e XAML.  

A maioria dos desenvolvedores usam o Xamarin.Forms. Essa é a rota recomendada para desenvolvedores novos no Xamarin. A abordagem do Xamarin nativo é mais difícil e requer um conhecimento maior das plataformas de destino.
  
Não é necessário decidir qual abordagem adotar antecipadamente; os aplicativos podem ser implementados usando uma combinação de Xamarin nativo e Xamarin.Forms:  
  
-   Use o Xamarin.Forms para criar telas de uso geral. Elas fornecem interfaces do usuário e recursos semelhantes entre as plataformas, como logons, formulários de contato e resultados da pesquisa.  
  
-   Use uma variedade de recursos de personalização no Xamarin.Forms para ajustar a interface do usuário de acordo com cada plataforma. A opção de personalização mais simples envolve a API `OnPlatform`. Você também pode criar exibições personalizadas, estender os renderizadores existentes e criar renderizadores personalizados.  
  
-   Se necessário, use o Xamarin nativo para criar telas que usem recursos de interface do usuário exclusivos de cada plataforma. Um exemplo é uma tela que usa a captura da câmera e a manipulação de imagem nativas.  
  
Em geral, o melhor é começar com uma solução do Xamarin.Forms para configurar o compartilhamento do código da interface do usuário entre as plataformas. Use os recursos de personalização para fazer os ajustes específicos da plataforma. Se e quando precisar de telas totalmente específicas da plataforma, você poderá adicioná-las individualmente usando o Xamarin nativo.  
  
Para saber mais:  
  
1.  O [Xamarin.Forms](/xamarin/xamarin-forms/) fornece uma breve visão geral e os prós e contras do Xamarin.Forms em relação às camadas de interface do usuário nativa (ou seja, o Xamarin.iOS e o Xamarin.Android).  
  
2.  Os primeiros três minutos do vídeo de James Montemagno, [Xamarin.Forms: Native iOS, Android & Windows apps with C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704) (Xamarin.Forms: aplicativos iOS, Android e Windows nativos com C# e XAML), (Channel9 13m3s) fornece outra visão geral e você pode continuar assistindo demonstrações.  
  
3.  (Opcional) [Uma introdução ao Xamarin.Forms](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (Opcional) Veja exemplos de uso de `OnPlatform` para personalização na documentação [Classe de Dispositivo](/xamarin/xamarin-forms/platform/device/)
  
5.  (Opcional) [Multiplataforma – compartilhar código de interface do usuário em plataformas móveis com o Xamarin.Forms](https://msdn.microsoft.com/magazine/dn904669.aspx) de Jason Smith (MSDN Magazine) descreve as diferentes opções de personalização do Xamarin.Forms, cujos detalhes são abordados em [Renderizadores Personalizados](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/).  
  
## <a name="deeper-dive-debugging-with-emulators"></a>Aprofundamento: Depurando com emuladores  

*10 a 15 minutos*  
  
Para depurar seus aplicativos multiplataforma sem precisar usar um dispositivo físico, você precisará usar os emuladores discutidos aqui:  
  
### <a name="microsofts-android-emulator"></a>Android Emulador da Microsoft 

É recomendável que você use o [Emulador do Microsoft Visual Studio para Android](~/cross-platform/visual-studio-emulator-for-android.md), que é instalado com o Visual Studio.  O vídeo [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) (Emulador do Visual Studio para Android) (Channel9, 5m55s) oferece uma visão geral e uma demonstração.  
  
### <a name="apples-ios-simulator"></a>Simulador do iOS da Apple

Para saber mais, leia [Getting Started with the iOS Simulator](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) (Introdução ao Simulador de iOS) (apple.com).  
  
### <a name="microsofts-windows-phone-emulator"></a>Emulator para Windows Phone da Microsoft.

Para saber mais, leia [Testar com o Emulador Microsoft para Windows 10 Mobile](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/).  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Aprofundamento: componentes do Xamarin  

*10 minutos*  
  
Muitas funcionalidades estendidas estão disponíveis para aplicativos Xamarin por meio de componentes Xamarin. Encontre o catálogo completo disponível para download em [http://components.xamarin.com/](http://components.xamarin.com/), que inclui componentes para outros controles adicionais da interface do usuário, autenticação, uma variedade de serviços de nuvem, como o Microsoft Azure, e muito mais.