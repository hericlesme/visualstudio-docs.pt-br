---
title: "Noções básicas do Windows Installer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1a9f895db0d202dd573e7c665b1185f6e3f4b751
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-installer-basics"></a>Noções básicas do Windows Installer
O Windows Installer instala e desinstala os aplicativos ou produtos de software no computador do usuário, realizar essas tarefas em unidades chamadas de componentes do Windows Installer (às vezes chamados de WICs ou apenas componentes). Um GUID que identifica cada WIC, que é a unidade básica de instalação e de configurações usando o Windows Installer de contagem de referência.  
  
 Para obter a documentação completa do Windows Installer, consulte o tópico do SDK da plataforma, [do Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Criar um VSPackage  
 O Windows Installer usa pacotes de instalação, que contêm informações que o Windows Installer precisa para instalar, desinstalar ou reparar um produto e para executar a interface de usuário (UI) de configuração. Cada pacote de instalação inclui um arquivo. msi, que contém um banco de dados de instalação, um fluxo de informações de resumo e fluxos de dados de várias partes da instalação. Para usar o instalador, você deve criar uma instalação. Porque o instalador organiza instalações em torno do conceito de componentes e armazena informações sobre a instalação em um banco de dados relacional, o processo de criação de um pacote de instalação em larga escala envolve as seguintes etapas:  
  
1.  Planeje sua configuração de criação para dar suporte a controle de versão e estratégias de lado a lado.  
  
2.  Identificar os recursos a serem apresentados aos usuários.  
  
3.  Organize o VSPackage e as dependências em componentes.  
  
4.  Preencha o banco de dados com informações de instalação.  
  
5.  Valide o pacote de instalação.  
  
 Esta documentação trata-se principalmente com as primeira e terceira etapas do processo. Durante essas etapas você organize seus recursos VSPackage WICs para que você possa forme o controle de versão e a estratégia para versões subsequentes da conta de serviço [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. As três etapas restantes são abordadas em detalhes na documentação do Windows Installer no SDK da plataforma.  
  
## <a name="key-terms"></a>Principais termos  
 A seguir é definições de chave termos relacionados a tecnologia Windows Installer.  
  
 Recurso  
 Arquivos, chaves do registro, atalhos, ou e assim por diante que pode ser instalado em um computador. Esses recursos são agrupados logicamente em componentes do Windows Installer.  
  
 Componente do Windows Installer (WIC)  
 A unidade básica de instalação que representa um agrupamento lógico de recursos relacionados que são instalados e desinstalados como uma unidade. Componentes do Windows Installer são identificados por uma ID exclusiva do componente, ou um GUID. Além disso, o Windows Installer mantém seu nível o WIC de contagem de referência. Para obter flexibilidade máxima do controle de versão, inclua não mais do que um recurso primário, como uma DLL, em um determinado WIC. Observe que, depois de identificar e popular um WIC, dê a ele um GUID e implantá-lo, você não pode alterar sua composição. Para obter mais informações, consulte [organizar aplicativos em componentes](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Pacote (Redist)  
 Uma unidade de implantação que consiste em um arquivo. msi e arquivos de origem externa ao qual este arquivo pode apontar. Um pacote contém todas as informações que o Windows Installer precisa para executar a interface do usuário e para instalar ou desinstalar o aplicativo.  
  
 arquivo. msi  
 Um arquivo de armazenamento estruturado em COM que contém as instruções e os dados necessários para instalar um aplicativo. Cada pacote contém pelo menos um arquivo. msi. O arquivo. msi contém o banco de dados do instalador, um fluxo de informações de resumo e possivelmente uma ou mais transformações e os arquivos de origem interna. Arquivos a serem instalados podem ser compactados em um gabinete e armazenados em um fluxo no arquivo. msi ou armazenados, compactados ou descompactados, fora do arquivo. msi na mídia de origem. Para obter mais informações, consulte [extensões de arquivo do Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Imposição de regras do Windows Installer  
 Dois conjuntos de regras determinam a implantação de recursos por meio de componentes da instalação. Um conjunto de regras é mantido pelo Windows Installer, enquanto você deve aplicar o segundo conjunto como autor de instalação.  
  
> [!NOTE]
>  A imposição de regras do Windows Installer ocorre somente se você executar uma validação de seu arquivo. msi. No entanto, são evitaram para tratar essas regras como as práticas recomendadas. Para obter mais informações, consulte [validação de um banco de dados de instalação](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) e [validação do pacote](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Regras aplicadas pelo instalador  
  
-   Todos os arquivos em um determinado componente devem ser instalados no mesmo diretório. Por outro lado, instalados para separar as pastas de arquivos devem pertencer para separar componentes.  
  
-   Pode haver apenas um caminho de chave por componente. O caminho da chave é simplesmente um arquivo ou chave do registro que representa o componente inteiro.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilidades do provedor de componente  
  
-   Quaisquer dois recursos que podem enviar separadamente em versões subsequentes devem existir em componentes separados. Recursos devem ser agrupados no mesmo componente somente quando você tiver certeza de que esses recursos nunca serão fornecido separadamente. Na verdade, é recomendável que todos os recursos principais (DLLs, por exemplo) sempre existem no WICs separados. Para obter mais informações, consulte [definindo instalador componentes](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Nenhum recurso com versão nunca deve enviar em mais de um WIC.  
  
## <a name="see-also"></a>Consulte também  
 [O que acontece se as regras de componente são desfeitas?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)