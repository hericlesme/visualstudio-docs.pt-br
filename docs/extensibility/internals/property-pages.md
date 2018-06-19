---
title: Páginas de propriedade | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b08e210a57388d77859600c02c0e6a30a404884
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133254"
---
# <a name="property-pages"></a>Páginas de propriedade
Usuários podem exibir e alterar propriedades de configuração dependente e - independentes de projeto usando as páginas de propriedade. Um **páginas de propriedade** botão é habilitado no **propriedades** janela ou na barra de ferramentas do Gerenciador de soluções para objetos que fornecem um modo de exibição de página de propriedade do objeto selecionado. Páginas de propriedade são criadas pelo ambiente e estão disponíveis para projetos e soluções. Mas, no entanto, também é possível tornar disponíveis para itens de projeto que tornam o usam de propriedades dependentes de configuração. Esse recurso pode ser usado quando os arquivos dentro de um projeto exigem configurações de comutador de compilador diferentes ser compilado corretamente.  
  
## <a name="using-property-pages"></a>Usando as páginas de propriedade  
 Se uma página de propriedades já exibida e a seleção é alterada (por exemplo, de uma solução para um projeto), as informações exibidas nas páginas de alterações para exibir as propriedades para a nova seleção. Se não houver nenhuma propriedade no objeto que dão suporte a páginas de propriedade, a página de propriedades está vazia.  
  
 Se forem selecionados vários objetos, a página de propriedades exibe a interseção de propriedades para todos os itens selecionados. Se o item selecionado não tem propriedades dependentes de configuração e o **páginas de propriedade** na barra de ferramentas do Gerenciador de soluções é clicada, o foco muda para a janela de propriedades. Para obter mais informações relacionadas à janela de propriedades e seleção, consulte [estendendo propriedades](../../extensibility/internals/extending-properties.md).  
  
 Se propriedades são exibidas para vários objetos e você alterar um valor em uma página de propriedade, todos os valores para os objetos são definidos para o novo valor, mesmo se eles foram inicialmente diferentes e a página foi em branco quando as propriedades de um objeto foram exibidas.  
  
 Há dois tipos gerais de **ProjectProperty páginas** disponíveis em caixas de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. No primeiro, para projetos do Visual Basic, por exemplo, as páginas de propriedade são exibidas usando um formato de campo, conforme mostrado na seguinte captura de tela. No segundo, mostrado posteriormente nesta seção, a propriedade hosts página uma grade de propriedades semelhante àquele encontrado na janela Propriedades.  
  
 ![Páginas de propriedades do Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Caixa de diálogo páginas de propriedades de projeto com estrutura de árvore e de formato de campo  
  
 A estrutura de árvore na caixa de diálogo páginas de propriedade não é criada usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. O ambiente, com base no nível nome passado pelo <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfaces, compila-lo.  
  
 Apenas duas categorias de nível superior estão disponíveis no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] páginas de propriedades:  
  
-   Propriedades em comum, que exibe informações de configuração independente para o objeto ou objetos selecionados. Como resultado, quando uma das subcategorias de propriedades comuns é selecionada, as opções de configuração, plataforma e Configuration Manager na parte superior da caixa de diálogo não estão disponíveis.  
  
-   Propriedades de configuração, que contém informações de configuração dependente relacionadas a compilação de depuração e otimização parâmetros para a solução ou projeto.  
  
 Você não pode criar qualquer outras categorias de nível superior, mas você pode optar por não exibir um ou outro na implementação de `IVsPropertyPage`. Se, por exemplo, você não tiver quaisquer propriedades de configuração independente para exibir um objeto, você pode optar por não exibir a categoria de propriedades comuns. Exibir propriedades comuns se `ISpecifyPropertyPages` é implementado de objeto de procura do item e propriedades de configuração quando você implementa `ISpecifyPropertyPages` no objeto de configuração (o objeto que implementa `IVsCfg`, `IVsProjectCfg`e relacionados interfaces).  
  
 Cada categoria exibida em uma categoria de nível superior representa uma página de propriedades separadas. Entradas de categoria e subcategoria disponíveis na caixa de diálogo são determinadas pela sua implementação de `ISpecifyPropertyPages` e `IVsPropertyPage`.  
  
 `IDispatch` objetos para itens no contêiner de seleção que têm propriedades a serem exibidas na implementação de páginas de propriedade `ISpecifyPropertyPages` para enumerar uma lista de IDs de classe. As IDs de classe são passadas como variáveis `ISpecifyPropertyPages` e são usados para instanciar as páginas de propriedades. A lista de IDs de classe também é passada para `IVsPropertyPage` para criar a estrutura de árvore à esquerda da caixa de diálogo. As páginas de propriedades, em seguida, passe informações de volta para o `IDispatch` objeto que implementa `ISpecifyPropertyPages` e preencha as informações para cada página.  
  
 As propriedades do objeto procurar são recuperadas usando `IDispatch` para cada objeto no contêiner de seleção.  
  
 Implementando `Help::DisplayTopicFromF1Keyword` no seu VSPackage fornece a funcionalidade para o botão Ajuda.  
  
 Para obter mais informações, consulte `IDispatch` e `ISpecifyPropertyPages`na biblioteca MSDN.  
  
 O segundo tipo de páginas de propriedades exibidas nos hosts de exemplos um formulário da grade de propriedades, conforme mostrado na seguinte captura de tela.  
  
 ![Páginas de propriedade do VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Caixa de diálogo páginas de propriedades com a grade de propriedades  
  
 As interfaces `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` (declarado em vsmanaged.h) são usados para criar e popular a grade de propriedades dentro de uma caixa de diálogo ou janela.  
  
 A arquitetura de projetos mudou significativamente das versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Em particular, a ideia de qual projeto está ativa foi alterado. Em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], não há nenhum conceito de um projeto ativo. Em ambientes de desenvolvimento anterior, o projeto ativo foi padrão para o projeto que criar e implantar comandos independentemente do contexto. Agora, a solução controla e arbitra que criar e implantar comandos se aplicam a quais projetos.  
  
 O que era anteriormente um projeto ativo agora é capturado em uma das três maneiras diferentes:  
  
-   O projeto de inicialização  
  
     Você pode especificar um projeto ou projetos da solução página de propriedades que será iniciado quando o usuário pressiona F5 ou seleciona executar no menu Build. Isso funciona de maneira semelhante para o antigo projeto ativo no sentido de que seu nome é exibido no Gerenciador de soluções com fonte em negrito.  
  
     Você pode recuperar o projeto de inicialização como uma propriedade no modelo de automação chamando `DTE.Solution.SolutionBuild.StartupProjects`. Em um VSPackage, você deve chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> métodos. `IVsSolutionBuildManager` está disponível como um serviço por `QueryService` em SID_SVsSolutionBuildManager. Para obter mais informações, consulte [objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md) e [configuração de solução](../../extensibility/internals/solution-configuration.md).  
  
-   Configuração de build de solução ativa  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tem uma configuração de solução ativa, disponível no modelo de automação com a implementação de `DTE.Solution.SolutionBuild.ActiveConfiguration`. Uma configuração de solução é uma coleção que contém uma configuração de projeto para cada projeto na solução (cada projeto pode ter várias configurações, em várias plataformas, com nomes diferentes). Para obter mais informações relacionadas a páginas de propriedades da solução, consulte [configuração de solução](../../extensibility/internals/solution-configuration.md).  
  
-   Projeto selecionado no momento  
  
     Implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> método para recuperar a hierarquia de projeto e item de projeto ou itens selecionados. De DTE, você usaria o `SelectedItems.SelectedItem.Project` e `SelectedItems.SelectedItem.ProjectItem` métodos. Não há código de exemplo com os títulos no núcleo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] documentos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)   
 [Configuração da solução](../../extensibility/internals/solution-configuration.md)