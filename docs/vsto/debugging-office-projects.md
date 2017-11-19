---
title: Depurando projetos do Office | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
ms.assetid: e360b9e9-9f36-48f0-a0c5-a6980fb47a87
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 110d6231da40ab59c3979b97441b3ac0ad458b3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-office-projects"></a>Depurando projetos do Office
  Você pode depurar projetos do Office usando o mesmo Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ferramentas usadas para outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]recursos do depurador, como a capacidade de inserir pontos de interrupção e exibir as variáveis no **locais** janela, também estão disponíveis quando você depurar projetos do Office. Para obter mais informações sobre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ferramentas de depuração, consulte [depuração no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Para simplificar a depuração, feche todas as instâncias do aplicativo do Office antes de compilar e depurá-lo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="starting-and-stopping-the-debugger"></a>Iniciando e parando o depurador  
 Você pode iniciar a depuração de um projeto do Office como iniciar a depuração outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos; por exemplo, você pode pressionar a tecla F5. Quando você inicia a depuração de um projeto de suplemento do VSTO, um novo processo para o aplicativo do Office de destino é iniciado e o suplemento do VSTO é carregado.  
  
 Quando você inicia a depuração de um projeto no nível do documento, o documento ou a pasta de trabalho é aberto em um novo processo do Word ou Excel.  
  
 Quando você interrompe o depurador, o depurador encerra o processo do aplicativo abruptamente ou desconecta-se você tiver o depurador definido para desanexar. Todos os outros documentos que são abertos no processo do aplicativo Office encerrado também são fechados sem aviso, e as alterações não salvas serão perdidas. Isso pode incluir todos os documentos ou pastas de trabalho que são abertas enquanto o depurador está em execução.  
  
 Normalmente, é melhor desanexar do processo antes de parar o depurador, para que você pode encerrar o aplicativo do Office da maneira normal. Você também pode desanexar do processo primeiro se desejar trabalhar com uma planilha ou documento aberto depois de parar o depurador.  
  
 Se você estiver depurando uma personalização de nível de documento para Word, repetidamente parando o depurador e fazendo com que o Word fechar repentinamente podem levar a modelo Normal se tornar corrompido. Se isso acontecer, você pode excluir o modelo Normal corrompido e ele será recriado automaticamente na próxima vez que abrir o Word. No entanto, todas as macros que foram armazenadas no modelo Normal não são recriadas.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Depurar o Office 2013 VSTO Add-ins usando o Office 2013 ou Office 2016  
 Se você estiver usando o Visual Studio 2015 e você tem as duas versões do Office instalado lado a lado, o Visual Studio inicia o Office 2016. Se você estiver usando o Visual Studio 2013, Visual Studio inicia o Office 2013.  
  
 Se você deseja depurar o suplemento do VSTO por meio de uma versão diferente do Office (2013 ou 2016), abra o **Project Designer**e no **depurar** guia, escolha o **Iniciar programa externo**botão de opção. Em seguida, navegue até o local do aplicativo do Office apropriado executável.  
  
## <a name="f10-and-f11-behavior"></a>F10 e o comportamento de F11  
 Quando você inicia a depuração de um projeto do Office, F10 e F11 não têm o mesmo comportamento ao iniciar a depuração de outros projetos do Visual Basic ou c#. Em projetos do Visual Basic ou c#, o depurador interrompe na função principal; em projetos do Office, o Visual Studio não tem controle sobre a função principal do aplicativo do Office. No entanto, durante a depuração, F10 e F11 têm as mesmas funções de projetos do Visual Basic e c#.  
  
## <a name="displaying-exceptions"></a>Exibindo exceções  
 Por causa da forma que o código gerenciado interage com código não gerenciado, o Visual Studio não exibe erros que são gerados pelos aplicativos do Microsoft Office. Por exemplo, se um VSTO suplemento criado usando ferramentas de desenvolvimento do Office no Visual Studio gera uma exceção, o aplicativo do Microsoft Office continua sem exibir um erro. Para ver esses erros, defina o depurador para interromper as exceções do common language runtime. Para obter mais informações, consulte [Gerenciando exceções com o depurador](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Se você definir o depurador para interromper as exceções do common language runtime, todas as exceções agora interromperá o depurador, incluindo aqueles que você manuseou e algumas exceções de primeira chance do tempo de execução, que podem não ser relevante para seu projeto. Erros referindo-se a msosec não foi encontrada aparecem em todos os projetos, mas são seguros ignorar. Essas exceções msosec não afetará sua solução.  
  
 Você também pode usar **tente... Catch** instruções em torno de seus métodos para capturar exceções.  
  
 Por padrão, o Visual Studio também não exibição Just-In-Time erros de depuração para projetos do Office; No entanto, você pode habilitar esse recurso para que você possa ver os erros que são gerados. Para obter mais informações, consulte [depuração Just-in-no Visual Studio](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argumentos de linha de comando  
 Se o **iniciar ação** no **depurar** página de propriedade é definida como **Iniciar projeto**, Visual Studio não usa argumentos de linha de comando ao depurar o projeto, mesmo se você tiver especificados argumentos de linha de comando, como opções de início. Se você quiser usar argumentos de linha de comando ao iniciar a depuração, você deve selecionar um **iniciar ação** diferente de **Iniciar projeto**.  
  
## <a name="source-control"></a>Controle do código-Fonte  
 Depurar propriedades não são compartilhadas entre vários usuários sob controle de origem. Projetos Visual Basic e c# armazenam propriedades de depuração em um arquivo específico do usuário (*ProjectName*. vbproj.user ou *ProjectName*. csproj.user), e esse arquivo não está sob controle de origem. Se a depuração de mais de uma pessoa, cada pessoa deve inserir propriedades de depuração manualmente.  
  
## <a name="debugging-cached-datasets-in-a-document-level-project"></a>Depuração de conjuntos de dados armazenados em cache em um projeto no nível de documento  
 Sempre que você criar um projeto, o conjunto de dados é esvaziado e recriado. Se você quiser depurar um conjunto de dados armazenados em cache, você deve abrir o documento fora do Visual Studio e, em seguida, anexar o depurador.  
  
## <a name="debugging-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Depurando projetos de documento do Word com base no documento do Word 97-2003 (*. doc) formato  
 Para depurar um projeto de documento do Word com base no documento do Word 97-2003 (*. doc) formato, você deve adicionar a pasta do projeto para a lista de pastas confiáveis. Para obter mais informações sobre como fazer isso, consulte [concedendo confiança a documentos](../vsto/granting-trust-to-documents.md)...  
  
## <a name="debugging-disabled-add-ins"></a>Depuração de suplementos desabilitados  
 Aplicativos do Microsoft Office podem desabilitar suplementos do VSTO que se comportam de forma inesperada. Um aplicativo do Microsoft Office desabilita o suplemento do VSTO para impedir que o código problemática carregar toda vez que o aplicativo for iniciado. No entanto, também é fácil causar um comportamento inesperado durante a depuração típico. Para obter informações sobre como habilitar novamente os suplementos do VSTO, consulte [como: habilitar novamente um VSTO suplemento que tem sido desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Há dois tipos de desabilitar a que os aplicativos do Microsoft Office usam para suplementos do VSTO: desabilitar o disco rígido e desabilitando flexível.  
  
### <a name="hard-disabling"></a>Desativar disco rígido  
 Desabilitar o disco rígido pode ocorrer quando um suplemento do VSTO faz com que o aplicativo seja encerrado inesperadamente. Também pode ocorrer no computador de desenvolvimento se você parar o depurador enquanto o <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos no seu suplemento do VSTO está em execução. Quando um suplemento do VSTO é rígida desabilitada, ela aparece no **itens desabilitados** lista no aplicativo.  
  
 Se um aplicativo do Office rígido desabilita um VSTO suplemento criado usando ferramentas de desenvolvimento do Office no Visual Studio, o aplicativo desabilita apenas o VSTO Add-in que causou a falha. Outros suplementos do VSTO criados usando ferramentas de desenvolvimento do Office no Visual Studio para o aplicativo Office continuará a ser carregado.  
  
### <a name="soft-disabling"></a>Desabilitando flexível  
 Desabilitar o software pode ocorrer quando um suplemento do VSTO produz um erro que não faz com que o aplicativo fechar inesperadamente. Por exemplo, um aplicativo flexível pode desabilitar um suplemento do VSTO se ele lança uma exceção não tratada durante a <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos está em execução. Quando um suplemento do VSTO é desabilitado flexível, ela aparece no **suplementos de aplicativo inativos** lista no aplicativo e o aplicativo altera o valor da **LoadBehavior** entrada do registro para o VSTO Suplemento para indicar que ela é descarregada. Para obter mais informações sobre o **LoadBehavior** entrada do registro, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshooting-installation-errors-by-using-the-event-viewer"></a>Solucionando problemas de erros de instalação usando o Visualizador de eventos  
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] grava mensagens para o Visualizador de eventos do Windows para todas as exceções que são geradas quando você instala ou desinstala soluções do Office. Você pode usar essas mensagens para solucionar problemas de implantação e instalação.  
  
## <a name="troubleshooting-startup-errors-by-using-a-log-file-and-error-messages"></a>Solucionando problemas de erros de inicialização usando um arquivo de Log e mensagens de erro  
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pode gravar todos os erros que ocorrem durante a inicialização do log de um arquivo ou exibem cada erro em uma caixa de mensagem. Por padrão, essas opções estão desativadas. Você pode ativar as opções com a criação de variáveis de ambiente.  
  
 Para exibir cada erro em uma caixa de mensagem, crie uma variável de ambiente denominada `VSTO_SUPPRESSDISPLAYALERTS` e defina-o como 0 (zero). Você pode suprimir as mensagens excluindo a variável de ambiente ou definir o valor como 1 (um).  
  
 Para gravar os erros em um arquivo de log, crie uma variável de ambiente denominada `VSTO_LOGALERTS` e defina-a como 1 (um). O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria o arquivo de log na pasta que contém o manifesto de implantação para o suplemento do VSTO ou na pasta que contém o documento ou a pasta de trabalho que está associada com a personalização. Se isso falhar, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria o arquivo de log na pasta local % TEMP %. Nível de aplicativo suplementos do VSTO, o nome padrão é *suplemento nome*. vsto.log. Para projetos no nível de documento, o nome do arquivo de log é *nome do documento*. *extensão*. log, como ExcelWorkbook1.xlsx.log. Para interromper o log de erros, excluir a variável de ambiente ou defina-o como 0 (zero).  
  
## <a name="see-also"></a>Consulte também  
 [Criando soluções do Office](../vsto/building-office-solutions.md)   
 [Como: habilitar novamente um suplemento do VSTO que tenha sido desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Programando suplementos do VSTO](../vsto/programming-vsto-add-ins.md)  
  
  