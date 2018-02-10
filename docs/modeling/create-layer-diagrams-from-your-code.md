---
title: "Criar diagramas de dependência do seu código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 18477479255ff7af8216d093830c6c0d60fa50dc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="create-dependency-diagrams-from-your-code"></a>Criar diagramas de dependência do seu código

Para visualizar a arquitetura de alto nível, a lógica do seu sistema de software, criar um *diagrama de dependência* no Visual Studio. Para certificar-se de que seu código permaneça consistente com esse design, valide seu código com um diagrama de dependência. Você pode criar diagramas de dependência para projetos do Visual c# e Visual Basic. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

![Criar um diagrama de dependência](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

Um diagrama de dependência permite organizar os itens de solução do Visual Studio em grupos lógicos, abstract chamados *camadas*. É possível usar camadas para descrever as tarefas principais realizadas por esses artefatos ou os componentes principais do sistema. Cada camada pode conter outras camadas que descrevem tarefas mais detalhadas. Você também pode especificar se destina ou existente *dependências* entre camadas. Essas dependências, representadas como setas, mostram quais camadas podem usar ou atualmente usam a funcionalidade representada por outras camadas. Para manter controle arquitetônico do código, mostre as dependências desejadas no diagrama e, em seguida, valide o código no diagrama.

[Vídeo: Validar suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4) 

##  <a name="CreateDiagram"></a>Criar um diagrama de dependência

Antes de criar um diagrama de dependência, certifique-se de que sua solução tem um projeto de modelagem.

> [!IMPORTANT]
> Não adicione, arrastar ou copiar um diagrama de dependência existente de um projeto de modelagem para outro projeto de modelagem ou para outro lugar na solução. Isso preserva as referências do diagrama original, mesmo que você altere o diagrama. Isso também impede que a validação da camada funcione corretamente e talvez cause outros problemas como, por exemplo, elementos não encontrados ou outros erros quando você tenta abrir o diagrama.
>
> Em vez disso, adicione um novo diagrama de dependência para o projeto de modelagem. Copie os elementos do diagrama de origem para o novo diagrama. Salve o projeto de modelagem e o novo diagrama de dependência.

#### <a name="to-add-a-new-dependency-diagram-to-a-modeling-project"></a>Para adicionar um novo diagrama de dependência a um projeto de modelagem  
  
1.  Sobre o **arquitetura** menu, escolha **novo diagrama de dependência**.  
  
2.  Em **modelos**, escolha **diagrama de dependência**.  
  
3.  Nomeie o diagrama.  
  
4.  Em **adicionar ao projeto de modelagem**, navegue até e selecione um projeto de modelagem existente em sua solução.  
  
     -ou-  
  
     Escolha **criar um novo projeto de modelagem** para adicionar um novo projeto de modelagem para a solução.  
  
    > [!NOTE]
    >  O diagrama de dependência deve existir dentro de um projeto de modelagem. Porém, é possível vinculá-lo a itens em qualquer lugar na solução.  
  
5.  Certifique-se de salvar o projeto de modelagem e o diagrama de dependência.  

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Arrastar e soltar, ou copiar e colar, de um mapa de código

1. Gerar um mapa de código para a solução usando o **arquitetura** menu. 

2. Considere a aplicação de um filtro de mapa de código para remover pastas de solução e "Teste ativos", se você quiser impor dependências no código de produto.

3. No mapa de código gerado, remova o nó "Externo", ou expanda para mostrar assemblies externos, dependendo se você deseja impor dependências de namespace e excluir assemblies não obrigatórios do mapa de código. 

4. Criar um novo diagrama de dependência para a solução usando o **arquitetura** menu

5. Selecione todos os nós do mapa de código (usar _Ctrl_ + _um_, ou usar a seleção elástica pressionando o _Shift_ antes de clicar, arraste e solte da chave.

6. Arrastar e soltar, ou uma cópia e colagem, os elementos selecionados para o novo diagrama de validação de dependência. 

7. Isso mostra a arquitetura do aplicativo atual. Decidir o que você deseja que a arquitetura seja e modificar o diagrama de dependência adequadamente.

![Diagrama de dependência gerado a partir de um mapa de código](media/dependency-validation-01.png)
  
##  <a name="CreateLayers"></a>Criar camadas de artefatos  
 É possível criar camadas dos itens de solução do Visual Studio como, por exemplo, projetos, arquivos de código, namespaces, classes e métodos. Isso cria automaticamente links entre camadas e itens, incluindo-os no processo de validação da camada.  
  
 Também é possível vincular camadas a itens que não dão suporte à validação como, por exemplo, documentos do Word ou apresentações do Powerpoint, de forma que você pode associar uma camada a especificações ou planos. Também é possível vincular camadas a arquivos em projetos compartilhados entre vários aplicativos, mas o processo de validação não incluirá essas camadas, exibidas com nomes genéricos como, por exemplo, "Camada 1" e "Camada 2".  
  
 Para ver se um item vinculado oferece suporte à validação, abra **Explorer camada** e examine o **dá suporte à validação** propriedade do item. Consulte [gerenciar links para artefatos](#Managing).  
  
|**To**|**Siga estas etapas**|  
|------------|----------------------------|  
|Criar uma camada para um único artefato|<ol><li>Arraste o item para o diagrama de dependência destas origens:<br /><br /> <ul><li>**Gerenciador de Soluções**<br /><br />         Por exemplo, é possível arrastar arquivos ou projetos.</li><li>Mapas de código<br /><br />         Consulte [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md) e [mapas de código de uso para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Exibição de classe** ou **Pesquisador de objetos**</li></ul><br />     Uma camada é exibida no diagrama e está vinculada ao artefato.</li><li>Renomeie a camada para refletir as responsabilidades do código ou dos artefatos associados.</li></ol> **Importante:** arrastando arquivos binários para o diagrama de dependência não adiciona automaticamente as referências ao projeto de modelagem. Você deve adicionar manualmente os arquivos binários que você deseja validar ao projeto de modelagem. **Para adicionar arquivos binários para o projeto de modelagem** <ol><li>Em **Solution Explorer**, abra o menu de atalho para o projeto de modelagem e, em seguida, escolha **Add Existing Item**.</li><li>No **Add Existing Item** caixa de diálogo, navegue até os arquivos binários, selecioná-los e, em seguida, escolha **Okey**.     Os arquivos binários são exibidos no projeto de modelagem.</li><li>Em **Solution Explorer**, escolha um arquivo binário que você adicionou e, em seguida, pressione **F4** para abrir o **propriedades** janela.</li><li>Em cada arquivo binário, defina o **ação de compilação** propriedade **validar**.</li></ol>|  
|Criar uma única camada para todos os artefatos selecionados|Arraste todos os artefatos para o diagrama de dependência ao mesmo tempo.<br /><br /> Uma camada é exibida no diagrama e está vinculada a todos os artefatos.|  
|Criar uma camada para cada artefato selecionado|Pressione e segure o **SHIFT** pressionada enquanto você arrasta todos os artefatos para o diagrama de dependência ao mesmo tempo. **Observação:** se você usar o **SHIFT** chave para selecionar um intervalo de itens, solte a tecla depois de selecionar os artefatos. Mantenha-o pressionado novamente ao arrastar os artefatos para o diagrama. <br /><br /> Uma camada para cada artefato é exibida no diagrama e está vinculada a cada artefato.|  
|Adicionar um artefato a uma camada|Arraste o artefato à camada.|  
|Criar uma nova camada desvinculada|No **caixa de ferramentas**, expanda o **diagrama de dependência** seção e, em seguida, arraste um **camada** ao diagrama de dependência.<br /><br /> Para adicionar várias camadas, clique duas vezes na ferramenta. Quando você terminar, escolha o **ponteiro** ferramenta ou pressione a **ESC** chave.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para o diagrama de dependência, escolha **adicionar**e, em seguida, escolha **camada**.|  
|Criar camadas aninhadas|Arraste uma camada existente para outra camada.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para uma camada, escolha **adicionar**e, em seguida, escolha **camada**.|  
|Criar uma nova camada que contém duas ou mais camadas existentes|Selecione as camadas, abra o menu de atalho de sua seleção e, em seguida, escolha **grupo**.|  
|Alterar a cor de uma camada|Definir seu **cor** propriedade para a cor que você deseja.|  
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na camada de **proibido Namespaces** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na camada de **dependências de Namespace proibido** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na camada de **Namespaces necessários** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
  
 O número em uma camada indica o número de artefatos que estão associados à camada. No entanto, ao ler esse número, lembre-se do seguinte:  
  
-   Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.  
  
     Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.  
  
-   Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.  
  
##  <a name="Managing"></a>Gerenciar links entre camadas e artefatos  
  
1.  No diagrama de dependência, abra o menu de atalho para a camada e escolha **Exibir Links**.  
  
     **Pesquisador de objetos da camada** mostra os links de artefato para a camada selecionada.  
  
2.  Use as seguintes tarefas para gerenciar esses links:  
  
|**To**|**No Gerenciador de camada**|  
|------------|---------------------------|  
|Excluir o links entre a camada e um artefato|Abra o menu de atalho para o link de artefato e, em seguida, escolha **excluir**.|  
|Mover o link de uma camada para outra|Arraste o link de artefato para uma camada existente no diagrama.<br /><br /> - ou -<br /><br /> 1.  Abra o menu de atalho para o link de artefato e, em seguida, escolha **Recortar**.<br />2.  No diagrama de dependência, abra o menu de atalho para a camada e escolha **colar**.|  
|Copiar o link de uma camada para outra|1.  Abra o menu de atalho para o link de artefato e, em seguida, escolha **cópia**.<br />2.  No diagrama de dependência, abra o menu de atalho para a camada e escolha **colar**.|  
|Criar uma nova camada com base em um link de artefato existente|Arraste o link de artefato para uma área em branco no diagrama.|  
|Verifique se um artefato vinculado oferece suporte à validação contra o diagrama de dependência.|Examine o **dá suporte à validação** coluna para o link de artefato.|  
  
##  <a name="Discovering"></a>Dependências de engenharia reversa existentes  
 Existirá uma dependência sempre que um artefato associado a uma camada tiver uma referência a um artefato associado a outra camada. Por exemplo, uma classe em uma camada declara uma variável que tem uma classe em outra camada. É possível fazer engenharia reversa em dependências existentes para artefatos vinculados a camadas no diagrama.  
  
> [!NOTE]
>  As dependências não podem sofrer engenharia reversa para determinados tipos de artefatos. Por exemplo, nenhuma dependência sofrerá engenharia reversa de ou para uma camada vinculada a um arquivo de texto. Para ver quais artefatos têm dependências que você pode fazer engenharia reversa, abra o menu de atalho para uma ou várias camadas e, em seguida, escolha **Exibir Links**. Em **Explorer camada**, examine o **dá suporte à validação** coluna. Dependências não será revertido para artefatos para a qual esta coluna mostra **False**.  
  
-   Selecione uma ou várias camadas, abra o menu de atalho para uma camada selecionada e, em seguida, escolha **dependências gerar**.  
  
 Normalmente, você verá algumas dependências que não devem existir. É possível editar essas dependências para alinhá-las com o design desejado.  
  
##  <a name="EditDependencies"></a>Editar camadas e as dependências para mostrar o design desejado  
 Para descrever as alterações que você planeja fazer em seu sistema, ou a arquitetura pretendida, edite o diagrama de dependência:  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Alterar ou restringir a direção de uma dependência|Definir seu **direção** propriedade.|  
|Criar novas dependências|Use o **dependência** e **dependência bidirecional** ferramentas.<br /><br /> Para desenhar várias dependências, clique duas vezes na ferramenta. Quando você terminar, escolha o **ponteiro** ferramenta ou pressione a **ESC** chave.|  
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na camada de **dependências de Namespace proibido** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na camada de **proibido Namespaces** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na camada de **Namespaces necessários** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
  
##  <a name="EditLayout"></a>Alterar a aparecem dos elementos no diagrama  
 É possível alterar o tamanho, a forma, a cor e a posição das camadas ou a cor das dependências editando-se suas propriedades.  
  
##  <a name="Codemaps"></a>Descobrir padrões e as dependências de um mapa de código  
 Ao criar diagramas de dependência, você também pode criar **mapas de código**. Esses diagramas podem ajudá-lo a descobrir padrões e as dependências, enquanto você explorar o código. Use o Gerenciador de soluções, o modo de exibição de classe ou o Pesquisador de objetos para explorar os assemblies, namespaces e classes - que geralmente correspondem para as camadas existentes. Para obter mais informações sobre mapas de códigos, consulte:  
  
-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)  
  
-   [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Encontrar possíveis problemas usando analisadores de mapa de códigos](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Consulte também  
 [Vídeo: Validar suas dependências de arquitetura em tempo real](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)   
 [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)   
 [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)   
 [Validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualizar código](../modeling/visualize-code.md)
