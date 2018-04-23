---
title: Web Essentials projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6918c539409a31dfe5249adb5858ca20c8c2337c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="web-project-essentials"></a>Conceitos básicos de projeto da Web
Projetos da Web criar aplicativos da Web. Você pode usar um projeto da Web para criar um aplicativo Web que tem inteligentes páginas da Web. Uma página da Web inteligente tem código de servidor que processa a página da Web sob demanda.  
  
 Usando linguagens de programação tradicionais, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], você pode criar inteligentes páginas da Web para coletar e processar informações de um usuário, armazene-o em um banco de dados e assim por diante.  
  
-   O modelo de code-behind associa a páginas da Web que têm a extensão de arquivo. aspx ou. asmx de arquivos de código fonte dependentes. Por exemplo, Hello pode ter o hello.aspx.cs de arquivo de código fonte dependentes.  
  
-   O código do lado do servidor associado a uma página da Web inteligente é compilado em um arquivo executável que está localizado na pasta /bin do site.  
  
-   Arquivos de código de origem adicionais, como classes auxiliares que não estão associados uma página da Web específica, estão localizados na pasta /App_Code site da Web.  
  
    -   Um projeto de site da Web (WSP) gera um arquivo executável para cada página da Web inteligente. Arquivos executáveis adicionais são gerados de qualquer arquivo de código fonte na pasta /App_Code.  
  
    -   Um projeto de aplicativo Web (WAP) produz um único arquivo executável que combina o código para todas as páginas da Web inteligentes, bem como todos os arquivos de origem na pasta /App_Code.  
  
-   O arquivo de solução para um projeto da Web está localizado separadamente do site em si. Por padrão, os arquivos de solução estão localizados em \Documents and Settings\\*sua*documentos \My\\*\<Visual Studio # # # >*\Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Se você deseja manter o arquivo de solução com o site da Web, movê-lo lá e reabri-lo.  
  
-   Se você abrir um site que não tem nenhum arquivo de solução no Visual Studio, um novo arquivo de solução é gerado automaticamente para ele.  
  
-   Projetos da Web não tem nenhum arquivo de projeto. Informações do projeto são armazenadas no arquivo de solução, o arquivo Web. config e em outro lugar.  
  
-   Adicionar propriedades globais para um projeto Web automaticamente cria um arquivo de armazenamento na pasta de solução de projeto da Web.  
  
-   Uma página da Web inteligente pode ser associada uma linguagem de programação do lado do servidor usando a diretiva de página ou o \<script runat = "server" > marca.  
  
-   Além disso, a páginas da Web pode ter qualquer número de blocos de script do lado do cliente escrito em qualquer linguagem de script.  
  
-   Um sistema de projeto de site da Web é implementado com a adição de modelos de projeto e item e o registro para o [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeto.  
  
-   Um sistema WAP é implementado como um subtipo de projeto, também chamado de um tipo de projeto. O [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] projeto é versão, o subtipo WAP para criar o sistema WAP. Para obter mais informações sobre os subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
-   Uma página da Web inteligente combina HTML com uma linguagem de programação do lado do servidor. O idioma do servidor é chamado de linguagem independente. Para dar suporte a um idioma independente, o sistema do projeto da Web deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> família de interfaces.  
  
    -   Para dar suporte a linguagem contida em um editor, o serviço de linguagem HTML deve adiar Exibir código independente de idioma para um serviço de linguagem independente.  
  
    -   Marcadores de erro (vermelho squigglies) sempre devem ser criados no buffer principal do editor de códigos.  
  
## <a name="see-also"></a>Consulte também  
 [Projetos Web](../../extensibility/internals/web-projects.md)