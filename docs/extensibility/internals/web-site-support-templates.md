---
title: Modelos de suporte do Site da Web | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4e3d64f77064c04e131853786495c921711f2d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="web-site-support-templates"></a>Modelos de suporte do Site da Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Modelos de projeto e item do site da Web fornecem stubs de projeto e item site reutilizáveis e personalizáveis acelerar o processo de desenvolvimento, removendo a necessidade de criar novos projetos de site da Web e itens do zero. Para obter mais informações sobre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelos, consulte [criando modelos de projeto e Item](../../ide/creating-project-and-item-templates.md).  
  
## <a name="project-template-folder"></a>Pasta de modelos de projeto  
 Modelos de modelo de projeto da Web geralmente são instalados em [*caminho de instalação do Visual Studio*] \Common7\IDE\ProjectTemplates\Web\\, cada um em uma subpasta chamada após a linguagem de programação da web.  
  
## <a name="project-file"></a>Arquivo de Projeto  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) requer uma extensão de arquivo de projeto como uma maneira de mapear um modelo para o tipo de projeto correto. Como projetos da Web não tem um arquivo de projeto, o webproj de extensão de arquivo de projeto fictício está registrado para dar suporte a isso.  
  
 Opcionalmente, uma cadeia de caracteres de nome de idioma pode ser adicionada ao modelo para ativar o sistema de projeto da Web definir o idioma padrão **Adicionar Novo Item** caixa de diálogo de itens com base no modelo. A cadeia de caracteres deve ser a primeira linha do arquivo e deve corresponder ao nome registrado em AddItemLanguageName no registro do mecanismo Intellisense e o nome registrado em Subtype(VsTemplate) do projeto. Para obter mais informações, consulte [atributos de suporte do Site da Web](../../extensibility/internals/web-site-support-attributes.md).  
  
 Se a cadeia de caracteres não estiver presente, o sistema do projeto Web tentará determinar o idioma padrão com base nas extensões de atributo e o arquivo de idioma das páginas adicionadas ao projeto Web pelo modelo do modelo de projeto.  
  
## <a name="project-templates"></a>Modelos de projeto  
 Modelos de projeto de site são usados para criar novos sites da Web em resposta ao **novo Site** comando o **arquivo** menu. Atualmente há suporte para três tipos de projeto de site da Web:  
  
-   Projetos de site da Web vazio  
  
-   Projetos de site  
  
-   Projetos de serviço da Web  
  
### <a name="empty-web-site-projects"></a>Projetos de Site da Web vazio  
 Esses arquivos criam um novo site vazio em resposta ao **Site vazio** comando, que está disponível após apontar para **novo Site** no **arquivo** menu:  
  
-   EmptyWeb.vstemplate  
  
     O arquivo de modelo que orienta a criação do novo site da Web vazio.  
  
-   EmptyWeb.webproj  
  
     Esse arquivo é um artefato do sistema de modelo de projeto. Esteja de acordo com a referência do arquivo de projeto no arquivo EmptyWeb.vstemplate.  
  
### <a name="web-site-projects"></a>Projetos de Site  
 Esses arquivos criam um novo site em resposta ao **Site da Web ASP.NET** comando, que está disponível após apontar para **novo Site** no **arquivo** menu:  
  
-   Default.aspx  
  
     A página inicial padrão para o novo site. O atributo de idioma especifica o idioma de code-behind e o atributo CodeFile Especifica o arquivo dependente que contém o código de code-behind associado a esta página.  
  
-   Default. aspx. *extensão*  
  
     O arquivo dependente que contém o código de code-behind para a página inicial padrão. O idioma de code-behind determina o *extensão* deste arquivo.  
  
-   web.config  
  
     O arquivo de configuração de web.site raiz.  
  
-   WebApplication.vstemplate  
  
     O arquivo de modelo que determina o conteúdo da solução de site da Web e força a criação da pasta App_Data.  
  
-   WebApplication.webproj  
  
     Esse arquivo é um artefato do sistema de modelo de projeto. Esteja de acordo com a referência do arquivo de projeto no arquivo WebApplication.vstemplate.  
  
### <a name="web-service-projects"></a>Projetos de serviço da Web  
 Esses arquivos criam um novo site em resposta ao **serviço Web ASP.NET** comando que está disponível após apontar para **novo Site** no **arquivo** menu:  
  
-   Asmx  
  
     A página HTML para o novo serviço da Web. O atributo de idioma especifica o idioma de code-behind e o atributo CodeBehind Especifica o arquivo dependente que contém o código de code-behind associado a esse serviço.  
  
-   Serviço. *extensão*  
  
     O arquivo dependente que implementa a classe de serviço. O idioma de code-behind determina o *extensão* deste arquivo.  
  
-   web.config  
  
-   O arquivo de configuração de web.site raiz.  
  
-   WebService.vstemplate  
  
     O arquivo de modelo que determina o conteúdo da solução de site da Web e força a criação da pasta App_Data e App_Code. O serviço. *extensão* arquivo é copiado para a pasta App_Code.  
  
-   WebService.webproj  
  
     Esse arquivo é um artefato do sistema de modelo de projeto. Esteja de acordo com a referência do arquivo de projeto no arquivo WebService.vstemplate.  
  
## <a name="project-item-template-folder"></a>Pasta de modelos de Item de projeto  
 Modelos de modelo de item de projeto da Web geralmente são instalados em [*caminho de instalação do Visual Studio*] \Common7\IDE\ItemTemplates\Web\\, cada um em uma subpasta chamada após sua linguagem de programação da web.  
  
## <a name="project-item-templates"></a>Modelos de Item de projeto  
 Modelos de item de projeto de site da Web são usados para adicionar novas páginas da Web para um site da Web em resposta ao **Add Existing Item** comando. Esses tipos de páginas da Web são atualmente suportados:  
  
-   Nova classe  
  
-   Nova página HTML  
  
-   Novo formulário da Web  
  
-   Nova página mestra  
  
### <a name="new-class"></a>Nova classe  
 Este modelo cria um novo arquivo de origem que define uma classe vazia em resposta ao **Add New Class** comando.  
  
-   Classe. *extensão*  
  
     O arquivo de origem que implementa a classe vazia. O idioma de code-behind determina o *extensão* deste arquivo.  
  
-   Class.vstemplate  
  
     O arquivo de modelo que cria o arquivo de origem e determina o seu conteúdo.  
  
### <a name="new-html-page"></a>Nova página HTML  
 Este modelo cria uma nova página da Web em resposta ao **adicionar nova página HTML** comando.  
  
-   HtmlPage  
  
     O conteúdo inicial da página da Web. Esta página da Web geralmente não tem nenhum arquivo de code-behind associado dependentes. Para criar uma página inteligente com um arquivo de code-behind associado, use o modelo de formulário da Web.  
  
-   HTMLPage.vstemplate  
  
     O arquivo de modelo que cria a página da Web e determina o seu conteúdo.  
  
### <a name="new-webform"></a>Novo formulário da Web  
 Este modelo cria uma nova página da Web inteligente em resposta ao **adicionar novo Web Form** comando.  
  
 Para criar um arquivo de origem do code-behind dependentes, selecione **colocar código em arquivo separado**. Caso contrário, uma única página da Web é criada com um bloco de script vazio e não \<% Page % > diretivas para ligar um arquivo dependente.  
  
 Para criar uma página de conteúdo para uma página mestra selecionada, selecione **página mestra selecione**.  
  
-   WebForm.aspx  
  
     O conteúdo inicial da página da Web. Esta página da Web não tem nenhum arquivo de code-behind associado dependentes.  
  
-   WebForm_cb.aspx  
  
     O conteúdo inicial da página da Web. Esta página da Web tem um arquivo dependente de code-behind associado.  
  
-   Code-behind. *extensão*  
  
     O arquivo dependente que implementa a classe de formulário da Web. O idioma de code-behind determina o *extensão* deste arquivo.  
  
-   ContentPage.aspx  
  
     O conteúdo inicial da página da Web como uma página de conteúdo. Esta página da Web não tem nenhum arquivo de code-behind associado dependentes.  
  
-   ContentPage_cb.aspx  
  
     O conteúdo inicial da página da Web como uma página de conteúdo. Esta página da Web tem um arquivo dependente de code-behind associado.  
  
-   WebForm.vstemplate  
  
     O arquivo de modelo que determina o conteúdo da nova página da web e seus arquivos dependentes, se houver.  
  
### <a name="new-master-page"></a>Nova página mestra  
 Este modelo cria uma nova página mestra em resposta ao **adicionar nova página mestra** comando.  
  
 Para criar um arquivo de origem do code-behind dependentes, selecione **colocar código em arquivo separado**. Caso contrário, uma única página da Web é criada com um bloco de script vazio e não \<% Page % > diretivas para ligar um arquivo dependente.  
  
-   MasterPage  
  
     O conteúdo inicial da página mestra. Esta página mestre não contém nenhum arquivo de code-behind associado dependentes.  
  
-   MasterPage_cb.master  
  
     O conteúdo inicial da página mestra. Essa página mestra tem um arquivo dependente de code-behind associado.  
  
-   Code-behind. *extensão*  
  
     O arquivo dependente que implementa a classe de página mestra. O idioma de code-behind determina o *extensão* deste arquivo.  
  
-   MasterPage.vstemplate  
  
     O arquivo de modelo que determina o conteúdo da nova página mestra e seus arquivos dependentes, se houver.  
  
## <a name="see-also"></a>Consulte também  
 [Suporte ao site](../../extensibility/internals/web-site-support.md)