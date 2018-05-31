---
title: Soluções e Projetos, caixa de diálogo Opções
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 631b9fc17345d5d0c00d36e42a9d3b1db633c114
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34266335"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Soluções e Projetos, caixa de diálogo Opções
Define o comportamento de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] relacionado a projetos e soluções. Para acessar essas opções, selecione **Ferramentas > Opções**, expanda **Projetos e Soluções** e clique em **Geral**.

Os caminhos padrão para as pastas de projeto e de modelo são definidos por meio da guia **Locais** na mesma caixa de diálogo.

> [!NOTE]
> As opções disponíveis nas caixas de diálogo e os nomes os locais dos comandos de menu que você vê podem diferir do que é descrito na Ajuda, dependendo de suas configurações ativas ou da edição. Esta página de Ajuda foi escrita considerando as **Configurações gerais de desenvolvimento**. Para exibir ou alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).


## <a name="general-tab-options"></a>Opções da guia Geral

**Sempre mostrar a Lista de Erros se houver erros após a conclusão do build**

Abre a janela **Lista de Erros** após a conclusão do build, somente se houve falha de build de um projeto. Os erros que ocorrem durante o processo de build são exibidos. Quando essa opção estiver desmarcada, os erros ainda ocorrerão, mas a janela não será aberta quando o build for concluído. Essa opção é habilitada por padrão.

**Acompanhar item ativo no Gerenciador de Soluções**

Quando essa opção estiver selecionada, o **Gerenciador de Soluções** será aberto automaticamente e o item ativo será selecionado. O item selecionado é alterado conforme você trabalha com arquivos diferentes em um projeto ou uma solução, ou com componentes diferentes em um designer. Quando essa opção estiver desmarcada, a seleção no **Gerenciador de Soluções** não será alterada automaticamente. Essa opção é habilitada por padrão.

**Mostrar configurações de build avançadas**

Quando estiverem marcadas, as opções de configuração de build serão exibidas nas caixas de diálogo **Páginas de Propriedades do Projeto** e **Páginas de Propriedades da Solução**. Quando estiverem desmarcadas, as opções de configuração de build não serão exibidas nas caixas de diálogo **Páginas de Propriedades do Projeto** e **Páginas de Propriedades da Solução** para projetos do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e do [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] que contêm uma configuração ou as duas configurações de depuração e versão. Se um projeto tiver uma configuração definida pelo usuário, as opções de configuração de build serão mostradas.

Quando estiverem desmarcados, os comandos do menu **Build**, como **Compilar Solução**, **Recompilar Solução** e **Limpar Solução** serão executados na configuração de Versão e os comandos do menu **Depurar**, como **Iniciar Depuração** e **Iniciar Sem Depuração**, serão executados na configuração de Depuração.

**Sempre mostrar solução**

Quando essa opção estiver selecionada, a solução e todos os comandos que atuam em soluções sempre serão mostrados no IDE. Quando estiver desmarcada, todos os projetos serão criados como projetos independentes e você não verá a solução no Gerenciador de Soluções nem os comandos que atuam em soluções no IDE se a solução contiver apenas um projeto.

**Salvar novos projetos quando criados**

Quando essa opção estiver selecionada, será possível especificar um local para o projeto na caixa de diálogo **Novo Projeto**. Quando estiver desmarcada, todos os novos projetos serão criados como projetos temporários. Quando você estiver trabalhando com projetos temporários, poderá criar e testar um projeto sem a necessidade de especificar um local de disco.

**Avisar o usuário quando o local do projeto não for confiável**

Se você tentar criar um novo projeto ou abrir um projeto existente em um local que não é totalmente confiável (por exemplo, em um caminho UNC ou um caminho HTTP), uma mensagem será exibida. Use essa opção para especificar se a mensagem será exibida sempre que você tentar criar ou abrir um projeto em um local que não é totalmente confiável.

**Mostrar Janela de Saída no início do build**

Exibe a Janela de Saída automaticamente no IDE no início dos builds da solução. Para obter mais informações, consulte [Como controlar a Janela de Saída](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Solicitar renomeação simbólica ao renomear arquivos**

Quando estiver selecionado, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] exibirá uma caixa de mensagem perguntando se também deverá renomear todas as referências no projeto com o elemento de código ou não.

**Solicitar antes de mover arquivos para um novo local**

Quando selecionado, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] exibe uma caixa de mensagem de confirmação antes que os locais dos arquivos sejam alterados por ações no Gerenciador de Soluções.

**Reabrir documentos no carregamento da solução (Visual Studio 2017 versão 15.8 versão prévia 2 e posterior)**
 
Durante o carregamento da solução, reabra automaticamente documentos que estavam abertos na sessão anterior. Após a seleção, os documentos que estavam abertos na última vez em que esta solução foi fechada são abertos automaticamente quando a solução é carregada.

Reabrir certos tipos de arquivos ou designers pode atrasar o carregamento da solução. Desmarque esta opção para melhorar o desempenho do carregamento de solução, se você não quiser restaurar o contexto anterior da solução.

## <a name="locations-tab-options"></a>Opções da guia Locais

**Local dos projetos**

Especifica o local padrão em que o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cria as pastas de novos projetos e soluções. Várias caixas de diálogo também usam o local definido nessa opção para os pontos iniciais da pasta. Por exemplo, a caixa de diálogo Abrir Projeto usa esse local para o atalho Meus Projetos.

**Local dos modelos de projeto do usuário**

Especifica o local padrão usado pela caixa de diálogo **Novo Projeto** para criar a lista de **Meus Modelos**. Para obter mais informações, consulte [Como localizar e organizar modelos](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

**Local dos modelos de item do usuário**

Especifica o local padrão usado pela caixa de diálogo **Adicionar Novo Item** para criar a lista de **Meus Modelos**. Para obter mais informações, consulte [Como localizar e organizar modelos](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Opções, Projetos e Soluções, Compilar e Executar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Caixa de diálogo Opções, Projetos e Soluções, Projetos Web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
