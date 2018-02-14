---
title: Perguntas frequentes sobre as Ferramentas do R para Visual Studio | Microsoft Docs
description: Perguntas frequentes sobre R no Visual Studio.
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 5d6ede092549a3f055c15b1f7deafe0421797c44
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="frequently-asked-questions"></a>Perguntas frequentes

## <a name="visual-studio-support"></a>Suporte a Visual Studio

**P. As RTVS funciona no OS X ou no Linux?**

R. Atualmente, as RTVS se baseiam no Visual Studio, que é uma implementação somente do Windows. A Microsoft está analisando o suporte no Visual Studio Code e no Visual Studio para Mac. Consulte a [edição nº 1295 do RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**P. As RTVS funcionam com edições do Visual Studio Express?**

R. Nº

**P. Posso usar extensões do Visual Studio com as RTVS?**

R. Com certeza. Na verdade, aqui estão algumas opções que são comuns para pessoas que trabalham com o R.

- [VsVim para associações de chave vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Editor de markdown com visualização em tempo real](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Veja o [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para saber mais.

**P. Como as RTVS estão no Visual Studio, isso significa que o R pode ser facilmente usado com o C#, C++ e outras linguagens da Microsoft?**

R. Nº As RTVS são uma ferramenta para desenvolver código R e usa os intérpretes nativos de R padrão. Atualmente, não há suporte para interoperabilidade entre o R e outras linguagens.

**P. O RTVS funciona com uma localidade diferente do inglês?**

R. A versão 1.0 do RTVS será somente em inglês. A versão 1.1 será localizado para o mesmo conjunto de idiomas do Visual Studio. Enquanto isso, use o [Pacote do idioma inglês para o Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou, no Visual Studio 2017, execute o instalador e selecione inglês na guia **Pacotes de idiomas**.

![Configurações internacionais do Visual Studio 2017](media/FAQ-international-settings.png)

**P. Eu gosto muito das minhas configurações atuais do Visual Studio, mas desejo testar as novas configurações de Ciência de Dados. O que devo fazer?**

R. Salve suas configurações atuais do Visual Studio usando **Ferramentas > Importar e Exportar Configurações...** e, em seguida, mude para as configurações de Ciência de Dados. Para restaurar as configurações salvas, use o comando **Importar e Exportar Configurações...** novamente.

**P. Posso armazenar meu projeto do Visual Studio em um compartilhamento de rede?**

R. Não, o Visual Studio não dá suporte ao carregamento de projetos de um compartilhamento de rede.

## <a name="r-interpretersintegration"></a>Interpretadores/integração do R

**P. Com quais intérpretes do R as RTVS funcionam?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client e Microsoft Machine Learning Server](/machine-learning-server/)

**P. Onde posso baixar esses intérpretes?**

R. Veja [Instalação](installing-r-tools-for-visual-studio.md).

P. **O que é o Microsoft R Server?**

R. R Server é o antigo nome do [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**P. As RTVS funcionarão com as edições de 32 bits do R?**

R. Não, as RTVS só dão suporte às edições de 64 bits do R em execução em edições de 64 bits do Windows.

**P. As RTVS funcionam com meu sistema de controle do código-fonte?**

R. Sim, você pode usar qualquer sistema de controle do código-fonte que esteja integrado ao Visual Studio.

**P. Quais são as configurações `.gitignore` recomendadas para um projeto das RTVS?**

R. O Github mantém um repositório de arquivos `.gitignore` recomendados. Você pode vê-lo aqui: [.gitignore do R](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Serviços remotos

P. **O que são os Serviços Remotos no Visual Studio?**

R. Os Serviços Remotos do R para Visual Studio permitem configurar um computador Windows ou Linux e, em seguida, conectar-se a ele por meio do RTVS. Consulte [Configurando espaços de trabalho remotos](setting-up-remote-r-workspaces.md).

P. **O RTVS pode se conectar ao Microsoft R Server?**

R. Não, porque o Microsoft R Server é uma tecnologia diferente e não fornece o mesmo mecanismo de conectividade, como exigido pelo RTVS.

P. **O RTVS pode se conectar a uma VM criada usando a imagem de VM de ciência de dados no Azure?**

R. Sim, a imagem [VM de ciência de dados – Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) vem pré-instalada com os Serviços R Remotos para Visual Studio.

P. **O RTVS pode se conectar a um computador remoto com R instalado?**

Para executar código R em um computador remoto, deve haver algum serviço de escuta para as solicitações, recebendo o código e enviando os resultados de volta para o computador cliente. É isto que os Serviços Remotos do R para Visual Studio fazem. Consulte [Configurando espaços de trabalho remotos](setting-up-remote-r-workspaces.md).

P. **O que é a sessão remota?**

R. Consulte o artigo [Executar no servidor remoto](/machine-learning-server/r/how-to-execute-code-remotely) na documentação do Machine Learning Server.

## <a name="rtvs-development-and-features"></a>Recursos e desenvolvimento do RTVS

**P. O recurso X está ausente, mas o RStudio o tem!**

R. O RStudio é um IDE fantástico e maduro para R que vem sendo desenvolvido há vários anos. As RTVS procuram ter todos os recursos mais importantes que você precisa para ser bem-sucedido. Ajude a priorizar futuros trabalhos participando da [Pesquisa de RTVS](https://www.surveymonkey.com/r/RTVS1) e problemas de arquivo no [GitHub](https://github.com/Microsoft/RTVS/issues/).

**P. Posso contribuir para RTVS?**

R. Claro! O código-fonte reside no [Github](https://github.com/microsoft/RTVS). Use o rastreador de problemas para enviar bugs e comentar sobre aqueles já arquivados.

Você também pode contribuir com esta documentação &mdash; basta selecionar o comando **Editar** no canto superior direito de qualquer página. Os comentários sobre os documentos também são bem-vindos, os quais você pode adicionar à parte inferior de qualquer página.
