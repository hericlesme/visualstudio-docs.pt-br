---
title: Visual Studio Isolated Shell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6f4056e778e7d8f6aa62e84b03897c810160fa41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Isolated Shell
Shell do Visual Studio isolado permite que você crie aplicativos autônomos que podem ser executados lado a lado com outras versões do Visual Studio. É usado principalmente para hospedar ferramentas especializadas que podem usar os serviços do Visual Studio, mas também tem uma aparência personalizada e identidade visual. Recursos do Visual Studio e grupos de comando de menu podem facilmente ser ativados e desativado. Títulos de aplicativos, os ícones de aplicativo e telas são totalmente personalizáveis. Para obter uma lista de recursos personalizados, consulte [Personalizando o Shell isolado](customizing-the-isolated-shell.md).  
  
 Para trabalhar com um projeto do shell isolado, você deve instalar o SDK do Visual Studio. A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../installing-the-visual-studio-sdk.md).  
  
 Para criar um aplicativo de shell isolado, comece com um projeto do Visual Studio Shell isolado. Este projeto contém tudo o que você precisa para desenvolver e testar seu próprio aplicativo de shell isolado. Quando estiver pronto para escrever o programa de instalação que implanta seu aplicativo, você deve obter o pacote redistribuível do shell isolado do [pacote redistribuível do Microsoft Visual Studio Shell (isolado)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Antes de poder acessar o pacote redistribuível do shell isolado, você será solicitado para preencher uma pesquisa de clientes breve.  Depois de preencher a pesquisa, você será direcionado para uma página de conexão do Visual Studio com links de download do pacote redistribuível.  Você pode encontrar os links de download em visitas subsequentes para o site no Visual Studio se conectar a **programas &#124; VISUAL STUDIO 2015 integrado e SHELL ISOLADO** guia.  
  
> [!NOTE]
>  Para obter mais informações sobre como implantar um aplicativo shell isolado, consulte [passo a passo: Criando um aplicativo de Shell isolado básico](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabalhando com o shell isolado  
 Um aplicativo de shell do Visual Studio isolada tem acesso completo aos serviços do Visual Studio e dá suporte a identidade visual e personalização especial. Há várias maneiras que você pode personalizar um aplicativo de shell isolado:  
  
-   Você pode usar componentes VSPackages e Managed Extensibility Framework (MEF) para estender um aplicativo de shell isolado, assim como você usaria em qualquer outra extensão do Visual Studio. Para obter mais informações, consulte [estendendo o Shell isolado](extending-the-isolated-shell.md).  
  
-   Para tornar os recursos do Visual Studio e grupos de comando de menu disponíveis ou não está disponível, atualize o arquivo. VSCT do projeto de interface do usuário do usuário do aplicativo.  
  
-   Para remover **opções** páginas ou outros componentes do shell do Visual Studio do aplicativo, atualize o arquivo de .pkgundef do aplicativo.  
  
-   Para modificar o comportamento do shell ou outros aspectos da aparência, atualize o arquivo de .pkgdef do aplicativo.  
  
-   Alguns aspectos do shell também podem ser especificados quando o aplicativo é iniciado. Para fazer isso, atualize os parâmetros na chamada para o ponto de entrada inicial do appenvstub.dll.  
  
 Para obter mais informações sobre os diferentes elementos que você pode personalizar, consulte [elementos do Shell isolado](elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Recursos padrão do Shell isolado  
 Os seguintes recursos são padrão para todas as edições do Visual Studio.  
  
|Categoria de Recurso|Recurso|  
|----------------------|-------------|  
|Recursos IDE|Configurações de importação/exportação<br /><br /> Instalador do controle de caixa de ferramentas<br /><br /> Lista de tarefas & lista de erros<br /><br /> Janela Saída<br /><br /> Start Page<br /><br /> Janela Propriedades<br /><br /> Caixa de Ferramentas<br /><br /> Gerenciador de Soluções<br /><br /> Janela indicadores<br /><br /> Exibição de Classe<br /><br /> Pesquisador de Objetos<br /><br /> Janela Comando<br /><br /> Estrutura de Tópicos do Documento<br /><br /> Modo de exibição de recursos<br /><br /> Ferramenta externa<br /><br /> O Windows Communication Foundation (WCF) adicionar referência de serviço<br /><br /> Linguagem integrado suporte LINQ (consulta)|  
|Designer do Editor|Ferramentas (localização unificada, definição de fonte, herança) de navegação de código<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Gerenciador de Trechos de Código<br /><br /> Trechos de código<br /><br /> Refatoração<br /><br /> Listagem bonita<br /><br /> Filtragem do IntelliSense<br /><br /> Janela de definição de código<br /><br /> Designer de aplicativos<br /><br /> Designer de Formulários do Windows<br /><br /> Designer do Windows Presentation Foundation (WPF)|  
|Depuração|Avaliador de expressão c#<br /><br /> Depuração local<br /><br /> Depuração gerenciada<br /><br /> Editar e continuar<br /><br /> Depuração entre threads<br /><br /> Visualizações<br /><br /> DataTips<br /><br /> Depuração nativa<br /><br /> Depuração de script<br /><br /> Depuração de interoperabilidade<br /><br /> A depuração Just-in-time (JIT)<br /><br /> Depuração multiprocesso<br /><br /> Depuração de XSLT<br /><br /> Anexar ao processo de local<br /><br /> Pontos de rastreamento<br /><br /> Restrições de ponto de interrupção|  
|Dados|Gerenciador de servidores (simplificado - somente dados)<br /><br /> Ligar dados a dados local (. MDF ou. MDB)<br /><br /> Associar dados ao objeto<br /><br /> Associar dados ao serviço Web<br /><br /> Conjunto completo de controles de dados<br /><br /> Editor de XML<br /><br /> Associar dados ao servidor de banco de dados local<br /><br /> janela Fontes de Dados|  
|Web|Editor de HTML<br /><br /> Navegador da Web<br /><br /> O Web Forms designer<br /><br /> Projeto de Site<br /><br /> Projeto de aplicativo Web|  
|Extensibilidade|Consome componentes VSPackages e MEF|  
  
## <a name="see-also"></a>Consulte também  
 [Shell (isolado ou integrado)](shell-isolated-or-integrated.md)