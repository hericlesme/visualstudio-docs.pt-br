---
title: "Diagramas de dependência: Diretrizes | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: "55"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.workload: multiple
ms.openlocfilehash: 4590652f37c3f1a1bdaf6bd601aee8d01d1a1c98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependência: diretrizes
Descreve a arquitetura do aplicativo em um nível alto criando *diagramas de dependência* no Visual Studio. Certifique-se de que seu código permaneça consistente com esse design, validando seu código com um diagrama de dependência. Você também pode incluir validação de camada no processo de compilação. Consulte [vídeo do Channel 9: Design e validar sua arquitetura usando diagramas de dependência](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-dependency-diagram"></a>O que é um diagrama de dependência?  
 Como um diagrama de arquitetura tradicional, um diagrama de dependência identifica os principais componentes ou unidades funcionais de design e suas interdependências. Cada nó no diagrama, chamado um *camada*, representa um grupo lógico de namespaces, projetos ou outros artefatos. Você pode emitir as dependências que devem existir em seu design. Ao contrário de um diagrama de arquitetura tradicional, você pode verificar se as dependências reais no código-fonte está de acordo com as dependências pretendidas que você especificou. Fazendo parte de validação de uma compilação regular na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], você pode garantir que o código do programa continua a atender à arquitetura do sistema por meio de alterações futuras. Consulte [diagramas de dependência: referência](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a>Como criar ou atualizar seu aplicativo com diagramas de dependência  
 As etapas a seguir fornecem uma visão geral de como usar diagramas de dependência dentro do processo de desenvolvimento. As seções posteriores neste tópico descrevem mais detalhes sobre cada etapa. Se você estiver desenvolvendo um novo design, omita as etapas que se referem ao código existente.  
  
> [!NOTE]
>  Essas etapas aparecem na ordem aproximada. Você provavelmente deseja sobrepor as tarefas, reordená-las de acordo com sua situação e revisá-las no início de cada iteração em seu projeto.  
  
1.  [Criar um diagrama de dependência](#Create) para o aplicativo inteiro ou para uma camada dentro dele.  
  
2.  [Definir camadas para representar as principais áreas funcionais ou componentes](#CreateLayers) do seu aplicativo. Nome essas camadas de acordo com sua função, por exemplo, "Apresentação" ou "Serviços". Se você tiver um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução, você pode associar cada camada com uma coleção de *artefatos*, como projetos, namespaces, arquivos e assim por diante.  
  
3.  [Descobrir as dependências existentes](#Generate) entre camadas.  
  
4.  [Editar as camadas e dependências](#EditArchitecture) para mostrar a atualização que você deseja que o código para refletir de design.  
  
5.  [Criar novas áreas do seu aplicativo](#NewAreas) criando camadas para representar os blocos arquitetônicos principais ou componentes e definir dependências para mostrar como cada camada usa os outros.  
  
6.  [Editar o layout e a aparência do diagrama](#EditLayout) para ajudá-lo a discuti-lo com colegas.  
  
7.  [Validar o código com o diagrama de dependência](#Validate) para realçar os conflitos entre o código e a arquitetura que você precisa.  
  
8.  [Atualize o código de acordo com sua nova arquitetura](#UpdateCode). Iterativamente desenvolver e refatorar o código até que a validação não mostra nenhum conflito.  
  
9. [Incluir validação de camada no processo de compilação](#BuildValidation) para garantir que o código continue aderir ao seu design.  
  
##  <a name="Create"></a>Criar um diagrama de dependência  
 Um diagrama de dependência deve ser criado dentro de um projeto de modelagem. Você pode adicionar um novo diagrama de dependência a um projeto de modelagem existente, crie um novo projeto de modelagem para o diagrama de dependência ou copiar um diagrama de dependência existente dentro do mesmo projeto de modelagem.  
  
> [!IMPORTANT]
>  Não adicionar, arrastar ou copiar um diagrama de dependência existente de um projeto de modelagem para outro projeto de modelagem ou para outro local na solução. Um diagrama de dependência que é copiado dessa maneira terá as mesmas referências como o diagrama original, mesmo se você modificar o diagrama. Isso impedirá a validação da camada de funcionar corretamente e pode causar outros problemas, como elementos ausentes ou outros erros ao tentar abrir o diagrama.  
  
 Consulte [criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a>Definir camadas para representar as áreas funcionais ou componentes  
 Camadas representam grupos lógicos de *artefatos*, como projetos, arquivos de código, namespaces, classes e métodos. Você pode criar camadas de artefatos de projetos do Visual c# .NET e Visual Basic .NET ou anexar especificações ou planos para uma camada por meio da vinculação de documentos, como arquivos do Word ou apresentações do PowerPoint. Cada camada aparece como um retângulo no diagrama e mostra o número de artefatos que estão vinculados a ele. Uma camada pode conter camadas aninhadas que descrevem as tarefas mais específicas.  
  
 Como diretriz geral, camadas de nome de acordo com a sua função, por exemplo, "Apresentação" ou "Serviços". Se os artefatos estão estreitamente interdependentes, coloque-os na mesma camada. Se os artefatos podem ser atualizados separadamente ou usados em aplicativos separados, coloquem-os em diferentes camadas. Para saber mais sobre os padrões de camadas, visite o site de padrões e práticas em [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Determinados tipos de artefatos que você pode vincular a camadas, mas que não oferece suporte à validação contra o diagrama de dependência. Para ver se o artefato oferece suporte à validação, abra **Explorer camada** para examinar o **dá suporte à validação** propriedades do link de artefato. Consulte [descobrir dependências existentes entre as camadas](#Generate).  
  
 Ao atualizar um aplicativo desconhecido, você também pode criar mapas de código. Esses diagramas podem ajudá-lo a descobrir padrões e as dependências, enquanto você explorar o código. Use o Gerenciador de soluções para explorar os namespaces e classes, que geralmente correspondem para as camadas existentes. Atribua esses artefatos de código para camadas arrastando-os no Gerenciador de soluções para diagramas de dependência. Você pode usar diagramas de dependência para ajudá-lo a atualizar o código e mantê-los consistentes com o design.  
  
 Consulte:  
  
-   [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a>Descobrir dependências existentes entre camadas  
 Existirá uma dependência sempre que um artefato associado a uma camada tiver uma referência a um artefato associado a outra camada. Por exemplo, uma classe em uma camada declara uma variável que tem uma classe em outra camada. Você pode descobrir dependências existentes com a engenharia reversa-los.  
  
> [!NOTE]
>  As dependências não podem sofrer engenharia reversa para determinados tipos de artefatos. Por exemplo, nenhuma dependência sofrerá engenharia reversa de ou para uma camada vinculada a um arquivo de texto. Para ver quais artefatos têm dependências que você pode fazer engenharia reversa, clique uma ou várias camadas e, em seguida, clique em **Exibir Links**. Em **Explorer camada**, examine o **dá suporte à validação** coluna. Dependências não será revertido para artefatos para a qual esta coluna mostra **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>A engenharia reversa de dependências existentes entre camadas  
  
-   Selecione uma camada ou várias camadas, com o botão direito uma camada selecionada e, em seguida, clique em **dependências gerar**.  
  
 Normalmente, você verá algumas dependências que não devem existir. É possível editar essas dependências para alinhá-las com o design desejado.  
  
##  <a name="EditArchitecture"></a>Editar camadas e as dependências para mostrar o design desejado  
 Para descrever as alterações que você planeja fazer em seu sistema, ou a arquitetura pretendida, use as etapas a seguir para editar o diagrama de dependência. Você também pode considerar fazer algumas alterações de refatoração para melhorar a estrutura do código antes de estendê-lo. Consulte [melhorando a estrutura do código](#Improving).  
  
|**To**|**Execute estas etapas**|  
|------------|-----------------------------|  
|Excluir uma dependência que não deve existir|Clique na dependência e, em seguida, pressione **excluir**.|  
|Alterar ou restringir a direção de uma dependência|Definir seu **direção** propriedade.|  
|Criar novas dependências|Use o **dependência** e **dependência bidirecional** ferramentas.<br /><br /> Para desenhar várias dependências, clique duas vezes na ferramenta. Quando tiver terminado, clique no **ponteiro** ferramenta ou pressione a **ESC** chave.|  
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na camada de **dependências de Namespace proibido** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na camada de **proibido Namespaces** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na camada de **Namespaces necessários** propriedade. Use um ponto e vírgula (**;**) para separar os namespaces.|  
  
###  <a name="Improving"></a>Melhorando a estrutura do código  
 As alterações de refatoração são aprimoramentos que não afetam o comportamento do aplicativo, mas ajuda a facilitar o código alterar e estender no futuro. Código bem estruturado tem um design que seja fácil de abstrair a um diagrama de dependência.  
  
 Por exemplo, se você criar uma camada para cada namespace no código e, em seguida, fazer engenharia reversa as dependências, deve haver um conjunto mínimo de dependências unidirecionais entre as camadas. Se você criar um diagrama mais detalhado usando classes ou métodos de como as camadas, o resultado também deve ter as mesmas características.  
  
 Se isso não for o caso, o código será mais difícil alterar ao longo do tempo e menos adequado para a validação usando diagramas de dependência.  
  
##  <a name="NewAreas"></a>Criar novas áreas do seu aplicativo  
 Quando você iniciar o desenvolvimento de um novo projeto ou uma nova área em um novo projeto, você pode desenhar camadas e as dependências para ajudar a identificar os principais componentes antes de começar a desenvolver o código.  
  
-   **Mostrar os padrões de arquitetura identificação** nos diagramas de dependência, se possível. Por exemplo, um diagrama de dependência que descreve um aplicativo de área de trabalho pode incluir camadas como apresentação, a lógica do domínio e o repositório de dados. Um diagrama de dependência que abrange um único recurso em um aplicativo pode ter camadas como modelo, exibição e controlador. Para obter mais informações sobre esses padrões, consulte [padrões e práticas: arquitetura de aplicativo](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
-   **Criar um artefato de código para cada camada** como um namespace, classe ou componente. Isso facilita a seguir o código e vincular os artefatos de código em camadas. Assim que você cria cada artefato, vincule-o à camada apropriada.  
  
-   **Você não precisa vincular a maioria das classes e outros artefatos em camadas** porque eles se encaixam dentro de artefatos maiores, como namespaces que você já tiver vinculado a camadas.  
  
-   **Criar um novo diagrama para um novo recurso**. Normalmente, haverá um ou mais diagramas de dependência que descreve o aplicativo inteiro. Se você estiver criando um novo recurso do aplicativo, não adicionar ou alterar os diagramas existentes. Em vez disso, crie seu próprio diagrama que reflete as novas partes do código. As camadas no novo diagrama podem incluir apresentação, lógica de domínio e as camadas de banco de dados para o novo recurso.  
  
     Quando você cria o aplicativo, seu código será validado tanto no diagrama como um todo e seu diagrama mais detalhado do recurso.  
  
##  <a name="EditLayout"></a>Editar o layout de apresentação e discussão  
 Para ajudá-lo a identificar camadas e as dependências ou discuti-los com membros da equipe, edite a aparência e o layout do diagrama das seguintes maneiras:  
  
-   Altere os tamanhos, formas e posições das camadas.  
  
-   Altere as cores de camadas e as dependências.  
  
    -   Selecione uma ou mais camadas ou dependências, com o botão direito e clique **propriedades**. No **propriedades** janela, edite o **cor** propriedade.  
  
##  <a name="Validate"></a>Validar o código com o diagrama  
 Quando você tiver editado o diagrama, você pode validá-lo com o código manualmente a qualquer momento ou automaticamente toda vez que você executar uma compilação local ou [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].  
  
 Consulte:  
  
-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Incluir validação de camada no processo de compilação](#BuildValidation)  
  
##  <a name="UpdateCode"></a>O código de acordo com a nova arquitetura de atualização  
 Normalmente, aparecerão erros na primeira vez que você valide o código em um diagrama de dependência atualizado. Esses erros podem ter várias causas:  
  
-   Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.  
  
-   Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.  
  
 Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. Isso geralmente é um processo iterativo. Para obter mais informações sobre esses erros, consulte [validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Ao desenvolver ou refatorar o código, você pode ter novos artefatos para vincular ao diagrama de dependência. No entanto, isso pode não ser necessário, por exemplo, quando você tem camadas que representam a namespaces existentes e o novo código apenas adiciona mais material para esses namespaces.  
  
 Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Quando você suprime um erro, é uma prática recomendada registrar em log um item de trabalho em [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para executar essa tarefa, consulte [validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a>Incluir validação de camada no processo de compilação  
 Para garantir que as alterações futuras no código em conformidade com os diagramas de dependência, inclua validação de camada para o processo de compilação padrão da solução. Sempre que outros membros da equipe Compile a solução, todas as diferenças entre as dependências no código e o diagrama de dependência serão relatadas como erros de compilação. Para obter mais informações sobre como incluir validação de camada no processo de compilação, consulte [validar o código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Consulte também  
 [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)   
 [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)
