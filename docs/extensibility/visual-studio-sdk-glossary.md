---
title: Glossário do Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148893"
---
# <a name="visual-studio-sdk-glossary"></a>Glossário do Visual Studio SDK
Este glossário fornece definições de termos que são usados no [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentação.  
  
## <a name="terms"></a>Termos  
 add-in  
 Um aplicativo de utilitário, driver ou outro software adicionadas a um aplicativo principal. No ambiente de desenvolvimento integrado do Visual Studio (IDE), um suplemento é um aplicativo baseado em automação que estende os recursos do IDE.  
  
 modelo de automação  
 O modelo de automação, conhecido em versões anteriores do Visual Studio como o modelo de extensibilidade, é uma interface de programação que oferece acesso às rotinas subjacentes unidade IDE. Os suplementos, assistentes e macros usam objetos no modelo de automação para controlar ou estendem a funcionalidade do IDE.  
  
 contexto de interface do usuário de comando  
 Associação de um GUID com a visibilidade de um elemento, como uma barra de ferramentas ou comando de interface do usuário. Contexto de interface do usuário do comando é diferente de contexto da seleção em que ele não está anexado a uma janela.  
  
 Contexto de interface do usuário do comando pode ser usado para:  
  
-   Atribua um GUID para uma barra de ferramentas é exibida quando uma janela específica está ativada.  
  
-   Atribua um GUID para a disponibilidade de um comando sem a necessidade de carregar ou executar um VSPackage.  
  
-   Atribua um GUID para afetar a associação de chave ativa.  
  
-   Atribua um GUID para ativar a gravação da macro.  
  
-   Atribua um GUID para ativar o modo de depuração ou para alternar entre o design e o modo de execução em um editor.  
  
 componente  
 Parte do software que pode ser feito parte da funcionalidade do aplicativo sem esse aplicativo qualquer pré-existente informações sobre a implementação do software. A comunicação entre um componente e um aplicativo é apenas por meio de interfaces de estilo OLE.  
  
 Gerenciador de componentes  
 Um serviço, `SOleComponentManager`, que fornece serviços de coordenação de interface do usuário não para componentes de nível superior. O `SOleComponentManager` serviço implementa o `IOleComponentManager` interface.  
  
 Gerenciador de componentes de interface do usuário  
 Um serviço, `SOleComponentUIManager`, que fornece serviços de coordenação de interface do usuário. O `SOleComponentUIManager` serviço implementa o `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfaces.  
  
 recipiente de contexto  
 Um `IVsUserContext` COM (objeto) anexado a um componente do ambiente. Esse objeto contém as palavras-chave de pesquisa, F1 palavras-chave e atributos relacionados ao componente. Além disso, pacotes de contexto ponto para quaisquer pacotes subcontexto que estão vinculados a eles.  
  
 provedor de contexto  
 Um componente no IDE que tem um recipiente de contexto associado a ele. Esses componentes incluem uma janela da ferramenta, editor ou hierarquia do projeto.  
  
 designer  
 Uma interface de programação que permite aos usuários manipular os elementos da interface do usuário (formulários, botões e outros controles).  
  
 DocData  
 Um objeto COM que encapsula os dados subjacentes de um documento em um mundo onde há separação de documento/exibição (por exemplo, no caso de editor de texto, isso seria o buffer de texto subjacente todas as exibições do editor de texto). Se o EditorFactory não fornecer esse objeto, o IDE produzirá um em seu nome. É responsabilidade do objeto para gerenciar a persistência de dados e a semântica de compartilhamento para vários modos de exibição sobre isso mesmo `DocData`. Se o `DocData` objeto oferece suporte o `IOleCommandTarget` interface, ele será incluído no roteamento de comando da UIShell.  
  
 DocObject  
 Tecnologia usada para hospedar a interface do usuário em um intervalo fornecido pelo host. Mais especificamente, este termo se refere a qualquer inserção que oferece suporte a `IOleDocument` e interfaces relacionadas à. Essa tecnologia tem muitos aplicativos potenciais, como um detalhe de implementação de documentos COM, janelas de ferramentas no Visual Basic 5.0, os designers do ActiveX no Visual Basic 6.0 e assim por diante.  
  
 documento  
 Usado para se referir genericamente ao documento como um todo, tanto o `DocData` e `DocView`. Por exemplo, um DocumentFrame contém um `DocView`, mas também mantém uma referência para o `DocData` para lidar com a persistência.  
  
 DocView  
 O DocObject/incorporando/WindowPane com a qual o usuário interage para exibir e manipular subjacente `DocData`. Observe que os usuários não tirar proveito da separação de documento/exibição que faz parte do `DocObject` interface de design. Os usuários usar um DocObject inteira para atuar como um modo de exibição em vez de usar uma noção mais abstrata (e menos formalizado) dos dados subjacentes, conhecidos como `DocData`. `DocView` objetos sempre são inseridos com objetos de quadro (windows de filho MDI) do documento do IDE.  
  
 DTE  
 O `DTE` objeto (extensibilidade de ferramentas de desenvolvimento) é o ponto de acesso mais alto no modelo de automação do Visual Studio, que permite automatizar e estender o IDE de forma programática.  
  
 Janela de ajuda dinâmica  
 Janela de ferramenta que é implementada pelo IDE e exibe uma lista de tópicos da Ajuda F1 ou de palavra-chave de pesquisa.  
  
 editor  
 Código (CLSID de classe) que implementa o `DocView`. Ele também implementa `DocData` se a separação de dados de exibição/tem suporte.  
  
 extensão  
 Um recurso que modifica, personaliza ou adiciona um IDE. Você criar extensões usando o modelo de automação ou VSPackages.  
  
 editor externo  
 Um editor que não é específico para o IDE, como o Microsoft Word. Ele foi registrado por meio de seus próprios mecanismos e pode ser usado fora do IDE. Se este editor pode ser inserido, ele será exibido em uma janela no IDE. Se ele não pode ser inserido, uma janela de nível superior é criada.  
  
 hierarquia  
 Árvore de nós, cada nó associado a um conjunto de propriedades.  
  
 componente de nível superior independente  
 Um componente que usa uma janela de nível superior sem janela restrita e pode funcionar efetivamente como uma janela de aplicativo autônomo, mas é implementado como um objeto em processo. Portanto, um componente de nível superior independente deve coordenar modalidade e serviços de loop de mensagem com o IDE. Objetos de processo não tem seu próprio loop de mensagem.  
  
 provedor de informações  
 O provedor de informações é um módulo que pode pesquisar palavras-chave e retornar uma lista de tópicos, na forma de `IVsUserContextItem` objetos. Para fornecer itens de palavra-chave F1 e pesquisa para o provedor de informações, registrar o arquivo de Ajuda compilado (. Nos formatos HxS) com o sistema. Os tópicos da Ajuda nesses arquivos são usados para fornecer a lista de tópicos exibidos na janela de ajuda dinâmica e mostra se o usuário pressionar F1.  
  
 componente no local  
 Um objeto VSPackage que implementa o `IOleInPlaceComponent` interface para gerenciar uma janela visualmente contido dentro de uma janela de documento do IDE de propriedade. Componentes no local não participam padrão OLE-mesclagem de menus; em vez disso, eles integram seus elementos de interface de usuário do IDE.  
  
 Há dois tipos de componentes no local: conectada in-loco componentes e controles de componente.  
  
 Conectada in-loco componentes têm menus, barras de ferramentas e comandos que estão bem integrados na interface de usuário do IDE, que aparecem como se eles foram criados diretamente no IDE.  
  
 Controles de componente não tem seus próprios elementos de interface do usuário integrados ao IDE; em vez disso, use as barras de ferramentas, comandos e menus do IDE. Por exemplo, o comando negrito pode ser usado como negrito uma palavra selecionada em um controle rich text inserido em um formulário. No entanto, controles de componente podem solicitar que os elementos de interface do usuário específico do componente instalados dinamicamente seja exibido.  
  
 serviço de linguagem  
 Um conjunto de objetos que permite aos desenvolvedores VSPackage implementar recursos de editores de códigos de idioma do computador, como marcação e a coloração de texto.  
  
 Projeto arquivos diversos  
 Projeto usado para hospedar arquivos abertos que não estão em nenhum projeto. A lista de itens neste projeto não é persistente.  
  
 projeto  
 Projetos são compostos de objetos da hierarquia, ou COM os objetos que implementam o `IVsHierarchy` interface.  
  
 designer de projeto específicas ou editor  
 Um designer não pode ser usado independentemente do tipo de projeto. Todos os designers específicos do projeto devem inserir suas informações de fábrica do Editor do registro. O IDE, em seguida, pode instanciar o designer sempre que um determinado tipo de arquivo é aberto em um projeto específico.  
  
 janela de tipo de projeto  
 Uma janela que monitora constantemente a hierarquia do projeto ativo no momento e o item do contexto global de seleção. O tipo de projeto windows usa o `SVsTrackSelectionEx` serviço para o IDE das alterações de alerta e exibir comentários para o usuário. Gerenciador de soluções é um exemplo de uma janela de tipo de projeto.  
  
 Janela de Propriedades  
 Navegador de propriedade anteriormente.  
  
 referência com base em projetos  
 Projeto que não exigem que os arquivos do projeto a ser no mesmo diretório. Em vez disso, referências aos arquivos de outros diretórios não relacionados são armazenadas e mantidas pelo próprio projeto.  
  
 tabela de documento em execução  
 Estrutura interna pelo qual o IDE mantém a lista de todos os documentos abertos no momento. Essa lista inclui todos os documentos abertos na memória, independentemente se os documentos estão sendo editados atualmente. Um documento é qualquer item que é salvo, incluindo procedimentos armazenados abertos em um editor, arquivos em um projeto ou o projeto principal arquivo (por exemplo, *. vcproj).  
  
 Contexto de seleção  
 Dados que faz parte dos detalhes de cada janela no IDE e são usados para rastrear as seleções ativas. Contexto de seleção consiste em:  
  
-   Ponteiro para o `IVsHierarchy` interface da hierarquia de projeto  
  
-   Identificador do item do item de projeto.  
  
-   Ponteiro para o `ISelectionContainer` interface fornecendo acesso às propriedades de objetos ativos.  
  
-   Matriz de valores de elemento.  
  
 serviço  
 Um contrato para um conjunto de interfaces que residem em um único objeto COM. Quando você cria um serviço, que é identificado por um GUID, você pode definir o conjunto de interfaces que executa o serviço. Objetos COM usam serviços para se comunicar uns com os outros.  
  
 Solução  
 Grupo de projetos relacionados com o qual o usuário trabalha.  
  
 designer de padrão  
 Um designer pode ser usado independentemente do tipo de projeto. Todos os designers padrão devem inserir suas informações de fábrica do Editor do registro. O IDE, em seguida, pode instanciar o designer sempre que um arquivo com uma extensão específica é aberto. Os dados devem persistir para um arquivo.  
  
 editor padrão  
 Editor que pode ser usada independentemente de qualquer tipo de projeto específico. Esses editores tem EditorFactories registrado no registro. Isso permite que o IDE localizar e invocar o editor.  
  
 editor padrão do sistema operacional  
 Uma inserção não for Visual Studio específico. Está registrado usando as teclas de Win32 conhecidas (por exemplo, o Gerenciador de Win32 sabe como chamar). Se tal um editor pode ser inserido, o editor ainda aparecerá em seu lugar no IDE. Caso contrário, uma janela de nível superior é criada para esses editores.  
  
 recipiente subcontexto  
 Um `IVsUserContext` objeto vinculado a um recipiente de contexto. Esse objeto contém palavras-chave de pesquisa, as palavras-chave de F1 e atributos de uma seleção em um componente do IDE. Exemplos de subcontexto incluem um comando em uma janela de ferramenta ou uma palavra-chave em um editor.  
  
 Lista de tarefas  
 Janela de ferramenta que é implementada pelo IDE e exibe uma lista de tarefas ativas.  
  
 Buffer de texto  
 Nome comum para o objeto `VSTextBuffer`.  
  
 Exibição de texto  
 Nome comum para o objeto `VSTextView`.  
  
 componente de nível superior da ferramenta  
 Um componente que funciona como uma janela pop-up sem janela restrita, coordenando intimamente com a interface de usuário do IDE. Como componentes de nível superior independentes, componentes de nível superior da ferramenta também devem coordenar modalidade e serviços de loop de mensagem com o IDE.  
  
 componente de nível superior  
 Um objeto de VSPackage que gerencia uma janela de nível superior sem janela restrita em vez da área cliente de uma janela do IDE. Componentes de nível superior é implementam o `IOleComponent` interface para tirar proveito dos serviços de loop de mensagem, como acesso de tempo ocioso.  
  
 Interface do usuário ativa  
 Um objeto VSPackage que está visível e atualmente não tem foco.  
  
 Hierarquia de interface do usuário  
 Um objeto COM que implementa o `IVsUIHierarchy` interface para permitir a exibição de uma hierarquia. A janela de hierarquia de interface do usuário implementa o `ISelectionContainer` interface para atualizar a janela de propriedades; outras janelas de tipo de projeto podem usar essa implementação, se desejado.  
  
 VSCT  
 Tabela de comando do Visual Studio. O arquivo. VSCT contém informações sobre o posicionamento e comportamentos de menus, barras de ferramentas e comandos no formato XML.  
  
 VSPackage  
 Um componente instalável de software que estende o Visual Studio IDE informando um ou mais dos seguintes: interface do usuário, serviços, tipos de projeto ou designer do editor. Um VSPackage consiste em um objeto COM que implementa o `IVsPackage` interface e um ou mais outros objetos que implementam as interfaces para dar suporte a seleção e outros recursos. Além disso, um VSPackage tem requisitos de registro específico.