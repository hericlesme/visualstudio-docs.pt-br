---
title: "Texto de interface do usuário e a Ajuda do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 555fd622f5655a69ba77f3905a39635e01831c76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de interface do usuário e a Ajuda do Visual Studio
##  <a name="BKMK_UITextAndTerminology"></a>Texto de interface do usuário e terminologia  
 Texto abrangente é crucial para a interface de usuário efetivada. Software que os usuários tendem a ler rótulos primeiro, ou seja, aqueles mais relevantes para a conclusão da tarefa em questão. Texto estático é lido com menos frequência. Plano para usuários iniciar suas sessões de trabalho com uma verificação rápida de toda a janela, seguida por uma leitura da interface do usuário nesta ordem aproximado:  
  
1.  Controles interativos no Centro  
  
2.  Confirmar botões  
  
3.  Controles interativos localizados em outro lugar  
  
4.  Instruções principais  
  
5.  Explicações complementares  
  
6.  Título da janela  
  
7.  Outro texto estático no corpo principal  
  
### <a name="usage-patterns-for-ui-text"></a>Padrões de uso para o texto de interface do usuário  
  
#### <a name="title-bar-text"></a>Texto da barra de título  
 Texto da barra de título deve coincidir com o comando que gerou a interface do usuário.  
  
#### <a name="instructional-text-helper-text"></a>Texto de instrução (texto auxiliar)  
 Em algumas caixas de diálogo, é útil fornecer instruções principais proeminentes para explicar o que fazer na janela ou na página. Às vezes, isso é conhecido como "texto auxiliar".  
  
##### <a name="writing-style-rules-for-helper-text"></a>Escrevendo regras de estilo para o texto de ajuda  
  
-   Não explicam o óbvio. A menos que seja absolutamente necessário, não inclua texto de instrução.  
  
-   Texto de instrução sempre é colocado na parte superior da caixa de diálogo e deve se referir à tarefa que está sendo executada.  
  
-   Precisamente explica aos usuários que precisam para realizar. Evite a redundância e comunicação excessiva.  
  
-   Examine cada janela e eliminar instruções e palavras duplicadas.  
  
-   Manter o texto de instrução curto. Se necessário para determinados usuários ou cenários mais informações, forneça um link para o tópico online conceitual detalhado.  
  
-   Escreva o texto para que contém o peso de cada palavra e é necessária.  
  
-   Siga as diretrizes da Microsoft existente para [texto de Interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [estilo e o tom](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="supplemental-instructions"></a>Instruções complementares  
 Instruções complementares fornecem informações adicionais que ajudam o usuário a entender os controles ou agrupamentos de controle. Isso também pode incluir texto de dica necessário entender o formato que o controle de entrada está esperando. Use instruções complementares com moderação. Reservá-los para casos em que é provável que o usuário não compreenda plenamente as consequências da opção que eles estão fazendo.  
  
 ![Texto complementar no Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "b_SupplementalText1 0601")  
  
 **Texto complementar no Visual Studio**  
  
 ![Texto complementar no Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "c_SupplementalText2 0601")  
  
 **Texto complementar no Visual Studio**  
  
#### <a name="infotips"></a>InfoTips  
 Normalmente, o texto de instrução pode ser muito demorado para posicionar o local na interface de usuário ou pode ser útil somente novos usuários, pareçam resíduos para usuários experientes. Nesse caso, o texto das instruções informativas deve ser colocado como uma dica de ferramenta em uma InfoDica.  
  
 InfoTips deve ser colocada próximo os controles que eles estão relacionados e devem usar o ícone de InfoDica específico, que é discreto ainda notável.  
  
 ![InfoDica no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Exemplo de uma InfoDica no Visual Studio**  
  
##### <a name="writing-style-rules-for-infotips"></a>Regras de estilo de escrita para InfoTips  
  
-   Grave InfoTips como frases. Eles exigem verbos específicos, caso oração e pontuação final.  
  
-   Use InfoTips para completar sua instrução principal ou informações. Se estiver usando apenas palavras diferentes para reformular a ideia principal, não é necessário uma InfoDica.  
  
-   Manter InfoTips diretos. Use palavras pequenas e simples, linguagem cotidiana que oferece suporte e incentivo o usuário.  
  
-   Siga as diretrizes da Microsoft existente para [texto de Interface do usuário](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx) e [estilo e o tom](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx).  
  
#### <a name="control-labels"></a>Rótulos de controle  
 Rótulos de controle devem ser curto, concisa e siga o [orientação de área de trabalho do Windows para controles](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx).  
  
 Para obter mais informações sobre o formato do rótulo de controle e posicionamento dentro da interface do usuário, consulte [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
#### <a name="help-links"></a>Links de ajuda  
 Links de Ajuda pode ser posicionado dentro do texto de instrução ou no corpo da interface do usuário. Eles podem ser links para Ajuda ou iniciar caixas de diálogo internas.  
  
##### <a name="visual-style-rules-for-help-links"></a>Regras de estilo visual para links de ajuda  
  
-   Use as cores do ambiente correto de hiperlinks. Um hiperlink corretamente com estilo não pisca brevemente vermelho quando clicado. Se você vir isso, é uma indicação de que as cores de ambiente não estão sendo usadas.  
  
-   Sublinhados só devem ser usados em foco ou quando o link é inserido em um parágrafo.  
  
-   Para obter mais informações sobre estilos visuais e interação de hiperlinks, ver botões e hiperlinks.  
  
##### <a name="writing-style-rules-for-help-links"></a>Regras de estilo de escrita para links de ajuda  
  
-   Ao iniciar as caixas de diálogo, manter os padrões elipses: nenhum botão de reticências para navegação, elipses se a tarefa requer adicional da interface do usuário.  
  
     ![Link de Ajuda no Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "e_HelpLink 0601")  
  
     **Reticências (...) em um link de ajuda indicam que a tarefa exigirá adicional da interface do usuário.**  
  
-   Links não deve começar com "Saiba", já que não é a intenção do usuário. O usuário deseja responder a uma pergunta específica, não receberá um treinamento geral.  
  
-   Links de ajuda de frase para que eles fazer a pergunta que o tópico responderá.  
  
     Incorreto:  
     "Saiba mais sobre preços de serviços móveis do Windows Azure"  
  
     Corrigi:  
     "Quais opções de preços estão disponíveis para serviços móveis do Windows Azure?"  
  
-   Nunca use *clique em...*  para o texto do link.  
  
-   Nunca link apenas a palavra "aqui". Isso é problemático para alguns leitores de tela, que serão apenas a palavra hiperlink de voz.  
  
     Incorreto:  
     "Para obter informações sobre serviços móveis do Windows Azure **aqui**"  
  
     Corrigi:  
     "Quais opções de preços estão disponíveis para serviços móveis do Windows Azure?"  
  
-   Para obter mais informações sobre o estilo de texto correto para links de Ajuda, consulte o [orientação de área de trabalho do Windows para obter ajuda](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx).  
  
#### <a name="hint-text"></a>Texto de dica  
 Texto de dica aparece como uma marca d'água em um controle ou abaixo do controle. A formatação correta será aplicada usando o token VSColors apropriado, `Environment.GrayText`.  
  
 Ele pode aparecer em um número de formulários.  
  
-   Em vez do rótulo de controle:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "f_HintText1 0601")  
  
-   Com um verbo, fornecendo instruções:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "g_HintText2 0601")  
  
-   Com texto indicando uma entrada necessária:  
  
     ![Dica de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "h_HintText3 0601")  
  
#### <a name="watermark-text"></a>Texto de marca d'água  
 Em uma superfície de design vazio, o texto deve indicar o que fazer, bem como fornecer links para abrir outras janelas relacionadas, se apropriado:  
  
 ![Marca d'água de texto no Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "i_WatermarkText 0601")  
  
 **Exemplo de texto de marca d'água no Visual Studio**  
  
### <a name="common-terminology"></a>Terminologia comum  
  
|Termo|Explicação|Comentário|  
|----------|-----------------|-------------|  
|Entrar / sair|Verbos usados como sinônimo de web para a representação de autenticação em uma propriedade de web. Os clientes, usamos isso vez como uma noção de nível superior para entrar e sair da conexão de usuário do IDE, que representa uma identidade de nível superior que fornece recursos de nível superior como roaming e licenciamento que não estão disponíveis com todas as outras conexões.|O usuário de IDE é o único recurso que deve representar uma página de entrada / sair verbo, que representa o usuário IDE de nível superior.|  
|Conectar / desconectar|Use em locais em que um recurso mantém uma única conexão a um serviço online.|Gerenciador de servidores, onde você pode ter apenas uma conexão do Azure ativa por vez, é um exemplo de conectar/desconectar.|  
|Adicionar / remover|Não destrutiva. Use quando estiver adicionando ou removendo algo em uma lista.|A caixa de diálogo de lista de servidor do Gerenciador de Conexão do TFS é um exemplo de como adicionar ou remover.|  
|Excluir|Destrutiva. Use somente quando o elemento que está sendo removido será permanentemente descartado ou excluído do disco.|"Delete" geralmente requer um prompt, se o resultado é excluindo um arquivo de disco.|  
  
## <a name="error-messages"></a>Mensagens de erro  
  
### <a name="overview"></a>Visão geral  
 Erros de acontecem. Definir limitações em que o usuário pode fazer é uma primeira etapa a sensata evitar mensagens de erro evitáveis. No entanto, quando ocorre um erro, uma mensagem de erro bem escrito pode ir um longo caminho para atenuar o problema. Mensagens de erro são possivelmente um dos tipos mais importantes de notificação de que o usuário vê, porque eles são síncronos e indicam um problema que precisa ser resolvido. Mensagens de erro de escrita inadequadamente deixam os usuários em seus próprios para decidir a causa dos erros e todas as soluções possíveis.  
  
 Os usuários podem parar prestar atenção ao uso excessivo ou confuso mensagens de erro, portanto experimentar mensagens somente necessário de gravação que agregam valor ao usuário. Se a mensagem é simplesmente uma notificação, use uma apresentação alternativa.  
  
### <a name="rules-for-creating-an-error-message"></a>Regras para criar uma mensagem de erro  
  
-   Ao construir mensagens de erro, escolha o nível de erro apropriado para o público. Visar resumos simples que fornecem uma ação que o usuário pode tomar, se aplicável. Estado não tudo o que o usuário não precisa saber.  
  
-   Fornece assistência construtivas. É mais fácil de ler e agir em uma mensagem de erro que contém a instrução.  
  
-   Não use negativas duplas.  
  
-   Executar ambos um automatizada e uma ortografia e gramática manual verificar qualquer mensagem de erro que você escrever.  
  
-   Para mensagens de erro complexo, evite comunicações sequenciais. Nunca use uma conexão de F1 para a mensagem de erro. A própria mensagem deve ser suficiente.  
  
-   Use o ícone correto.  
  
-   Faça perguntas fáceis de entender e usar os botões que tem opções claras, como "Excluir" e "Cancelar".  
  
-   Para avisos, estar claro sobre a consequência de continuar. Os botões devem indicar a consequência.  
  
-   Para erros, descreva o que o usuário pode fazer para corrigir o problema. Botões devem ser ações ou dizer "Fechar". Não use um botão "Okey" para uma mensagem de erro.  
  
-   Algumas perguntas para perguntar ao construir uma mensagem de erro:  
  
    -   O usuário pode descobrir como resolver o problema com este erro sozinho?  
  
    -   O usuário usa o mesmo vocabulário como esse erro?  
  
    -   É esse erro ambigious ou compartilhados em várias situações? Nesse caso, como você orientar os usuários para a solução que precisam?  
  
#### <a name="build-errors"></a>Erros de compilação  
 Como o Visual Studio é uma ferramenta de desenvolvimento de software, muitos de seus componentes têm uma compilação, converter ou codificação etapa para converter o trabalho do desenvolvedor em um formato binário. Essas conversões podem causar erros quando o compilador não pode processar arquivos criados incorretamente ou quando as opções de compilador não foram definidas corretamente.  
  
 Usuários do Visual Studio podem passar um enorme número de horas de desenvolvimento, Resolvendo erros de compilação. Esse tempo de resolução aumenta quando erros têm dependências ou quando as mensagens de erro estão mal gravadas, que pode dificultar descobrir a origem do erro.  
  
 Os erros de compilação recomendados são aquelas que não ocorrem em primeiro lugar, o que faz com que o Visual Studio fornece preenchimento automático e a linha ondulante do IntelliSense. Validador de esquema e ferramentas semelhantes fornecem o mesmo tipo de comentários. Esses mecanismos proativamente orientam o usuário para construir códigos bem formado, reduzindo a chance de erros de compilação.  
  
 O Visual Studio fornece uma janela de ferramenta em que os usuários podem ler e percorrer os erros que ocorreram na janela do documento. Atalhos de teclado são fornecidos para que o usuário possa rapidamente navegue grandes quantidades de código e ir diretamente para o local do problema. O Visual Studio também permite que cada erro de compilação a ser vinculado a uma ID de contexto/palavra-chave de ajuda específica, para que o usuário possa ir diretamente para um tópico da Ajuda que fornece informações mais detalhadas sobre o erro.  
  
 Erros de compilação claras e concisas de gravação:  
  
-   **Usar linguagem simples** que explica o problema com pouca ou nenhuma jargão do compilador. O texto de um erro de compilação não deve ser excessivamente técnico.  
  
-   **Descrever as possíveis causas.** Por exemplo, "faltando um vírgula entre a propriedade e o valor de ' (propriedade): (valor)' declaração."  
  
-   Fornecer detalhes sobre possíveis correções. Se não houver espaço suficiente, detalhes adicionais podem ser colocados em um tópico da Ajuda correspondente.  
  
### <a name="components-of-a-well-written-error-message"></a>Componentes de uma mensagem de erro bem escrito  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Use o serviço de caixa de diálogo do shell para mensagens de erro.  
 Usar o serviço de shell diálogo lhe permite controlar a aparência da mensagem, fontes em particular, sem alterações importantes para elementos individuais. Use o **IErrorInfo** mecanismos e relatá-los usando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Escolha uma apresentação efetivo e apropriado a notificação.  
 Use uma caixa de diálogo modal com um aviso crítico se uma ação imediata é necessária para evitar perda de dados (notificação síncrona). Ícones críticas são reservados para situações em que a mensagem sem leitura fechando pode levar a consequências negativas. Perda de dados é uma situação crítica que exige uma resposta de nível de alarme. Uso excessivo do ícone crítico desensitizes usuários em sua importância. Se a mensagem de erro é informativa por natureza, considere as alternativas para uma caixa de diálogo modal (notificação assíncrona).  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornece uma explicação sucinta, limpa de por que o problema ocorreu em vez de uma explicação técnica.  
 Sobrecarregar os usuários com detalhes técnicos na explicação tornará mais provável ignorar as mensagens de erro. Exemplos de mensagens bom:  
  
-   "Não é possível abrir o arquivo solicitado."  
  
-   "Não é possível conectar à Internet."  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>Fornecem informações sobre como corrigir o problema.  
 Oferece as sugestões de usuário de como corrigir o problema. Ser verdade com o usuário se não houver nenhuma sugestão. Forneça links diretos para fontes online alternativas, como o suporte técnico ou o suporte da comunidade. Tente direcionar os usuários para informações pertinentes ao problema de online específicas. Para uma ID de erro, considere a vinculação de usuários a um segmento de discussão sobre esse erro específico. Exemplos de mensagens bom:  
  
-   "Certifique-se de que você está conectado à Internet e tente a operação novamente."  
  
-   "Certifique-se de que o arquivo existe e se você tem permissão para abri-lo."  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Grave uma mensagem curta e para o ponto.  
 Uma mensagem de erro pode notificar, explicar e oferecem uma solução mas ser ignorada se for muito prolixo. Uma solução é usar divulgação progressiva com um botão de detalhes. Por exemplo, forneça uma descrição curta/solução e, em seguida, colocar mais detalhes em um botão de detalhes. Se os usuários optarem ler mais informações sobre o erro, eles podem fazer isso.  
  
 O idioma da mensagem deve ser:  
  
-   **Domínio apropriado.** Use linguagem que entenda o usuário. Mesmo que os clientes são desenvolvedores, geralmente não têm o contexto e terminologia que temos.  
  
-   **Específico.** Evite palavras vagas e dar nomes específicos e localizações de objetos envolvidos. Por exemplo, uma mensagem de erro como "o caractere é inválido" não é útil. O caractere? "Arquivo não encontrado". Qual arquivo?  
  
-   **Cortês.** Não culpam o usuário ou os fazem sentir tolos. Evite linguagem hostil ou ofensiva (kill, execução, encerrar, fatal, inválido). Evite texto em maiusculas, que geralmente é visto como shouting e não é mais legíveis. Não use humor.  
  
-   **Corrigi.** Use corrigir a ortografia e gramática (mesmo em alfabeto). Erros de digitação são não profissional e inconveniente.  
  
-   **Contextualmente apropriadas.** Use o texto do botão apropriado. Evite o botão "Okey" e em vez disso, use "Continue" ou "Sim/não".  
  
### <a name="error-message-examples"></a>Exemplos de mensagem de erro  
  
|Bom|Incorreta|  
|----------|---------|  
|"O número discado não está mais no serviço. Verifique o número e disque novamente ou discar 0 para o operador."|-"(449) de erro: número inválido"<br />-"Esta exceção sem tratamento de erro indica que a operação foi concluída com êxito."<br /><br /> ![Mensagem de erro inválido no Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>Acessando a Ajuda  
  
### <a name="overview"></a>Visão geral  
 Além de documentação no MSDN, um usuário do Visual Studio tem vários pontos de acesso para ajudar o usuário enquanto na interface de usuário. Para garantir que esses pontos de acesso estejam consistentemente disponíveis, é necessário tirar proveito do sistema de ajuda oferecido pelo ambiente de equipes de recursos. Esses pontos de acesso são:  
  
-   **Texto de instrução e complementar em caixas de diálogo.** Texto estático que dá a direção ou explicação, na interface do usuário superfície ou passe o mouse sobre um ícone de InfoDica está disponível.  
  
-   **Ajuda de F1** (somente no editor). No editor do Visual Studio, o usuário pode confiar que a qualquer momento, pressionando F1 abrirá um tópico de ajuda específico à seleção atual. Verifique se os tópicos associados F1 são apropriadas e informativos.  
  
-   **Hiperlinks para tópicos de Ajuda.** Um hiperlink em uma caixa de diálogo, a janela da ferramenta ou a superfície de design que inicia um tópico para ajudar o usuário em saber mais sobre uma tecnologia, recurso ou obter informações sobre como realizar uma tarefa.  
  
-   **Mecanismos de interface do usuário de auxiliar, como marcas inteligentes e caixas de diálogo de criação.** Esses mecanismos ajudar o usuário Noções básicas sobre um elemento de interface do usuário ou facilitam uma tarefa, como marcas inteligentes ou caixas de diálogo do construtor.  
  
-   **Botões de Ajuda da IU da** (preterido). Um indicador visível na barra de título que fornece acesso para o tópico da Ajuda de F1 relacionado.  
  
### <a name="text"></a>Texto  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto de instrução e complementar em caixas de diálogo  
 Nas caixas de diálogo que oferecem suporte a tarefas complexas, pode haver a necessidade de fornecer texto de instrução na interface do usuário, geralmente na parte superior da caixa de diálogo ou próximo controles complexos. Consulte [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obter detalhes sobre o estilo de texto.  
  
#### <a name="infotips"></a>InfoTips  
 Normalmente, texto de instrução pode ser muito demorado para posicionar o local na interface do usuário ou pode ser útil somente novos usuários, pareçam resíduos para usuários experientes. Nesse caso, o texto das instruções informativas deve ser colocado como uma dica de ferramenta em uma InfoDica.  
  
 InfoTips deve ser colocada próximo os controles que eles estão relacionados e devem usar o ícone de InfoDica específico, que é discreto ainda notável.  
  
 ![InfoDica no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "d_InfoTip 0601")  
  
 **Exemplo de uma InfoDica no Visual Studio**  
  
### <a name="interactive-help-mechanisms"></a>Mecanismos de ajuda interativos  
  
#### <a name="f1-help"></a>F1 Ajuda  
 Ajuda F1 é necessária em um editor ou a superfície de design, mas não em outro lugar no ambiente do Visual Studio.  
  
#### <a name="hyperlinks-to-help-topics"></a>Hiperlinks para tópicos de ajuda  
 Hiperlinks podem ser usados para executar uma ação, navegue no IDE ou iniciar a Ajuda em um navegador. Consulte [UI texto e terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obter detalhes sobre o idioma e 07.10.01 botões e hiperlinks para diretrizes visual e layout.  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Ajuda [?] botões em barras de título da caixa de diálogo (preteridas)  
 A maior parte do tempo, os botões de Ajuda [?] na barra de título de caixas de diálogo são preteridos. Tópicos de interface do usuário não fazem parte de nosso modelo de documento e, portanto, talvez não haja um tópico relevante para vincular a. Essencialmente, o botão da barra de título era a mesma coisa que ajuda F1, e que não é mais necessário em caixas de diálogo. Em alguns casos, isso pode ainda ser usado como um indicador de que há mais informações conceituais ou procedimentos disponíveis, embora os hiperlinks são mais comumente usados na interface do usuário mais recente.  
  
##### <a name="dialogs-created-through-the-environment"></a>Caixas de diálogo criadas através do ambiente  
 Muitas caixas de diálogo do shell são criadas por meio de **VBDialogBoxParam** função. Essa função compartilhada foi atualizada para auxiliar na movimentação de **ajuda** botão da caixa de diálogo para o **?** botão mantendo uma arquitetura com versões anteriores compatível e extensível.  
  
 Especificamente, o **VBDialogBoxParam** função examina o modelo de caixa de diálogo para um botão cuja ID é **IDHELP** (9) ou rótulo é **ajuda** ou **& Ajuda**. Se um botão de ajuda for encontrado, ele é oculto e o **WS_EX_CONTEXTHELP** estilo é adicionado à caixa de diálogo, o que coloca o **?** botão na barra de título da caixa de diálogo.  
  
 Quando a caixa de diálogo é criada, ele envia proc a caixa de diálogo para uma pilha e invoca a caixa de diálogo com um processo de caixa de diálogo pré-processando denominado **DialogPreProc**. Quando o **?** botão é clicado, ele envia um **WM_SYSCOMMAND** de **SC_CONTEXTHELP** à caixa de diálogo. O **DialogPreProc** captura este comando e o altera para um **WM_HELP** mensagem, que é passada para o procedimento original. a caixa de diálogo  
  
 A maioria das caixas de diálogo Criar ambiente têm um botão de ajuda na caixa de diálogo. Quando a caixa de diálogo é exibida, o botão Ajuda estiver oculto automática e somente o **?** botão funciona. Se o **?** botão nunca é removido ou alterado no Windows, essa solução permite que você voltar rapidamente para os botões de ajuda originais.  
  
 Esta solução pressupõe quatro que poderiam causar erros:  
  
-   Botão de Ajuda da caixa de diálogo é **IDHELP** (9).  
  
-   A caixa de diálogo parece correta quando o botão Ajuda é oculto.  
  
-   A caixa de diálogo não substitua seu winproc.  
  
-   A caixa de diálogo não será inserida dentro de outra caixa de diálogo.  
  
 Se a caixa de diálogo reside no msenv e não usa **VBDialogBoxParam**, investigue aproveitando **VBDialogBoxParam** antes de implementar seu próprio manipulador.  
  
##### <a name="dialogs-created-through-other-packages"></a>Caixas de diálogo criadas por meio de outros pacotes  
 Você pode implementar sua própria solução para caixas de diálogo que residem fora msenv. Para uma classe de caixa de diálogo compartilhadas no seu VSPackage, considere mover o botão de barra de título ou implementar um manipulador em cada caixa de diálogo. O código a seguir é um esqueleto de uma implementação para ajudá-lo a começar:  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>Botões de Ajuda no código gerenciado  
 Substituindo o comportamento de padrão do botão da barra de ajuda janela título é fácil em código gerenciado. Abaixo está um aplicativo de demonstração completo que demonstra esse comportamento. Em essência, você precisa substituir o formulário **WndProc** método e, em seguida, incêndio desativar a Ajuda de F1 solicitações quando uma **SC_CONTEXTHELP** mensagem é interceptada.  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Fontes e formatação para o Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Layout para o Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Notificações e progresso do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)