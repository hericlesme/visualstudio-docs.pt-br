---
title: Instalar o Visual Studio 2017 | Microsoft Docs
description: Saiba como instalar o Visual Studio, passo a passo.
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords: vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ff51b5910d8b81d8319eddd0fa3be08d2f9553d7
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2017
---
# <a name="install-visual-studio-2017"></a>Instalar o Visual Studio 2017
Bem-vindo a uma nova maneira de instalar o Visual Studio! Em nossa versão mais recente, facilitamos a seleção e instalação apenas dos recursos necessários. Também reduzimos os volumes mínimos do Visual Studio para que ele seja instalado mais rapidamente e com menor impacto ao sistema.

Quer saber mais sobre quais são as outras novidades nesta versão? Consulte nossas [notas de versão](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes).

Pronto para instalar? Guiaremos você no processo, passo a passo.

## <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Etapa 1 - Verificar se o computador está pronto para o Visual Studio

Antes de começar a instalação do Visual Studio:

1. Verifique os [requisitos do sistema](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs). Esses requisitos ajudam você a saber se o computador dá suporte ao Visual Studio 2017.
2. Aplique as atualizações mais recentes do Windows. Essas atualizações garantem que o computador tenha as atualizações de segurança mais recentes e os componentes de sistema obrigatórios para o Visual Studio.
3. Reinicialize. Isso garante que todas as instalações ou atualizações pendentes não atrapalhem a instalação do Visual Studio.
4. Libere espaço. Remova arquivos e aplicativos desnecessários de %SystemDrive%, por exemplo, executando o aplicativo Limpeza de Disco.

Para solucionar dúvidas sobre a execução de versões anteriores do Visual Studio lado a lado com o Visual Studio de 2017, consulte [os detalhes de compatibilidade do Visual Studio](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs#compatibility-with-previous-releases).

## <a name="step-2---download-visual-studio"></a>Etapa 2 - Baixar o Visual Studio

Em seguida, baixe o arquivo bootstrapper do Visual Studio. Para fazer isso, clique no botão a seguir, selecione a edição desejada do Visual Studio 2017, clique em **Salvar** e, em seguida, clique em **Abrir pasta**.

 > [!div class="button"]
 > [Baixe o Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
<br/>

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Download-the-Visual-Studio-Installer-GgrESHD6D_3311787171) sobre como baixar o arquivo bootstrapper do Visual Studio e selecione a edição do Visual Studio que é ideal para você. |

## <a name="step-3---install-the-visual-studio-installer"></a>Etapa 3 - Instalar o instalador do Visual Studio

Em seguida, execute o arquivo bootstrapper para instalar o Instalador do Visual Studio. Esse novo instalador leve inclui tudo o que você precisa para instalar e personalizar o Visual Studio 2017.

1.  Da sua pasta **Downloads**, clique duas vezes no inicializador que corresponde ou é semelhante a um dos seguintes arquivos:

  * **vs_enterprise.exe** para Visual Studio Enterprise
  * **vs_professional.exe** para Visual Studio Professional
  * **vs_community.exe** para Visual Studio Community  <br><br>

  Se você receber um aviso de Controle de Conta de Usuário, clique em **Sim**.

2.  Solicitaremos sua confirmação dos [Termos de Licença](https://www.visualstudio.com/license-terms/) da Microsoft e da [Política de Privacidade](https://go.microsoft.com/fwlink/?LinkID=824704) da Microsoft. Clique em **Continue**.  

   ![Termos de Licença e Política de Privacidade](media/vs2017-privacy-and-license-terms.PNG "Termos de Licença e Política de Privacidade da Microsoft")

## <a name="step-4---select-workloads"></a>Etapa 4 - Selecionar cargas de trabalho

Após a instalação do instalador, use-o para personalizar sua instalação selecionando os conjuntos de recursos ou cargas de trabalho desejados. Veja como.

1.  Encontre a carga de trabalho desejada na tela **Instalando o Visual Studio**.

  ![Caixa de diálogo de instalação do Visual Studio 2017](media/vs2017-workloads.PNG "Instalar cargas de trabalho do Visual Studio")

     Por exemplo, escolha a carga de trabalho de desenvolvimento de área de trabalho do .NET. Ela vem com o editor de núcleo padrão, que inclui o suporte à edição de código básico para mais de 20 linguagens, a capacidade de abrir e editar o código de qualquer pasta sem precisar de um projeto e o controle do código-fonte integrado.  

2.  Depois de selecionar as cargas desejadas, clique em **Instalar**.

    Em seguida, serão exibidas telas de status que mostram o progresso da instalação do Visual Studio.

3.  Depois que as novas cargas de trabalho e os componentes forem instalados, clique em **Inicializar**.  

> [!TIP]
>  A qualquer momento após a instalação, você pode instalar as cargas de trabalho ou os componentes não instalados inicialmente. Caso o Visual Studio esteja aberto, acesse **Ferramentas**, **Obter Ferramentas e Funcionalidades...**, que abre o Instalador do Visual Studio. Outra opção é abrir o **Instalador do Visual Studio** no menu Iniciar. Assim, é possível selecionar as cargas de trabalho ou os componentes que você deseja instalar e, em seguida, clicar e **Modificar**.  

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Workloads-in-Visual-Studio-2017-jHE19HD6D_1611787171) sobre como instalar o Instalador do Visual Studio e, em seguida, instalar uma carga de trabalho. |

## <a name="step-5---select-individual-components-optional"></a>Etapa 5 - Selecionar componentes individuais (opcional)

Se não quiser usar o recurso Cargas de Trabalho para personalizar a instalação do Visual Studio, você pode fazê-lo instalando componentes individuais como alternativa. Para selecionar componentes individuais, clique na opção **Componentes individuais** no Instalador do Visual Studio, selecione o que deseja e, em seguida, siga os avisos.

  ![Visual Studio 2017 — Instalar componentes individuais](media/vs2017-components.PNG "Instalar componentes individuais do Visual Studio")

  |         |         |
  |---------|---------|
  |  ![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo")  |   [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Components-in-Visual-Studio-2017-ZMfaVID6D_7411787171) sobre como instalar um componente individual usando o Instalador do Visual Studio. |

## <a name="step-6---install-language-packs-optional"></a>Etapa 6 - Instalar pacotes de idiomas (opcional)

Por padrão, o programa do instalador tenta encontrar a correspondência do idioma do sistema operacional quando ele é executado pela primeira vez. Para instalar o Visual Studio 2017 em um idioma de sua escolha, clique na opção **Pacotes de idioma** do Instalador do Visual Studio e siga os prompts.

  ![Visual Studio 2017 — Instalar pacotes de idiomas](media/vs2017-languages.PNG "Instalar pacotes de idiomas do Visual Studio")

  |         |         |
  |---------|---------|
  |  ![ícone de câmera para vídeo](media/video-icon.png "Assistir a um vídeo")  |   [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Install-Language-Packs-in-Visual-Studio-2017-ByT7yID6D_9011787171) sobre como instalar um pacote de idiomas usando o Instalador do Visual Studio. |

### <a name="change-the-installer-language-from-the-command-line"></a>Alterar o idioma de instalação da linha de comando

Outra maneira de alterar o idioma padrão é executar o instalador a partir da linha de comando. Por exemplo, é possível forçar o instalador a ser executado em inglês usando o seguinte comando: `vs_installer.exe --locale en-US`. O instalador memorizará essa configuração quando for executado na próxima vez. O instalador dá suporte aos seguintes tokens de idioma: zh-cn, zh-tw, cs-cz, en-us, es-es, fr-fr, de-de, it-it, ja-jp, ko-kr, pl-pl, pt-br, ru-ru e tr-tr.


## <a name="step-7---start-developing"></a>Etapa 7 – Começar a desenvolver
1. Após a conclusão da instalação do Visual Studio, clique no botão **Iniciar** para ver a [Introdução ao desenvolvimento com o Visual Studio](../ide/get-started-developing-with-visual-studio.md).

2. Clique em **Arquivo** e, em seguida, clique em **Novo Projeto**.

3. Selecione um tipo de projeto. <br><br>
   Por exemplo, para [compilar um aplicativo em C++](../ide/getting-started-with-cpp-in-visual-studio.md), clique em **Instalado**, expanda **Visual C++** e, em seguida, selecione o tipo de projeto C++ que deseja compilar. <br><br>
   Para [compilar um aplicativo em C#](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md), clique em **Instalado**, expanda **Visual C#** e, em seguida, selecione o tipo de projeto C# que deseja compilar.

## <a name="get-support"></a>Obter suporte
Às vezes, as coisas podem dar errado. Caso a instalação do Visual Studio falhe, confira a página [Solução de problemas de instalação e atualização do Visual Studio 2017](troubleshooting-installation-issues.md). Se nenhuma das etapas de solução de problemas ajudar, entre em contato conosco por meio de um chat ao vivo para obter ajuda com a instalação (somente em inglês). Para saber mais detalhes, confira a [página de suporte do Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aqui estão algumas outras opções de suporte:
* Você pode nos relatar problemas do produto por meio da ferramenta [Relatar um Problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md), exibida no Instalador do Visual Studio e no IDE do Visual Studio.
* Você pode compartilhar uma sugestão de produto conosco no [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* É possível acompanhar os problemas do produto na [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/), além de fazer perguntas e encontrar respostas.
* Você pode também interagir conosco e com outros desenvolvedores do Visual Studio por meio das [conversas sobre o Visual Studio na comunidade do Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opção requer uma conta do [GitHub](https://github.com/).)

## <a name="see-also"></a>Consulte também
* [Atualizar o Visual Studio 2017](update-visual-studio.md)
* [Modificar o Visual Studio 2017](modify-visual-studio.md)
* [Desinstalar o Visual Studio 2017](uninstall-visual-studio.md)
* [Criar uma instalação offline do Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Guia do administrador do Visual Studio 2017](visual-studio-administrator-guide.md)
  * [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Instalar ferramentas de build em um contêiner](build-tools-container.md)
