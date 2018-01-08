---
title: Atualizando projetos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 060823a04127480ef8de387200425a34c6ef1178
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="upgrading-projects"></a>Atualizando projetos
Altera o modelo de projeto de uma versão do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para o próximo pode exigir que as soluções e projetos ser atualizado para que eles podem executar a versão mais recente. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece interfaces que podem ser usados para implementar o suporte à atualização em seus próprios projetos.  
  
## <a name="upgrade-strategies"></a>Estratégias de atualização  
 Para dar suporte a uma atualização, a implementação do sistema de projeto deve definir e implementar uma estratégia de atualização. Para determinar sua estratégia, você pode escolher dar suporte a backup lado a lado (SxS), o backup de cópia ou ambos.  
  
-   Backup de SxS significa que um projeto copia somente os arquivos que precisam de atualização in-loco, adicionar um sufixo de nome arquivo adequado, por exemplo, ". old".  
  
-   Backup de cópia significa que um projeto copia todos os itens de projeto para um local de backup fornecida pelo usuário. Os arquivos relevantes no local original do projeto podem ser atualizados.  
  
## <a name="how-upgrade-works"></a>Como atualizar funciona  
 Quando uma solução criada em uma versão anterior do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é aberto em uma versão mais recente, as verificações IDE, a solução de arquivo para determinar se ele precisa ser atualizado. Se a atualização for necessária, o **Assistente de atualização de** é iniciada automaticamente para passar o usuário pelo processo de atualização.  
  
 Quando uma solução precisa de atualização, ele consulta cada fábrica de projeto para sua estratégia de atualização. A estratégia determina se a fábrica de projeto oferece suporte a backup de cópia ou SxS. As informações são enviadas para o **Assistente de atualização de**, que coleta as informações necessárias para o backup e apresenta as opções aplicáveis ao usuário.  
  
### <a name="multi-project-solutions"></a>Soluções multiprojeto  
 Se uma solução contiver vários projetos e as estratégias de atualização forem diferentes, como quando um projeto de C++ que só dá suporte a backup SxS e um projeto Web que só oferecem suporte a backup de cópia, as fábricas de projeto devem negociar a estratégia de atualização.  
  
 A solução de consulta cada fábrica de projeto para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Depois, ele chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para verificar se os arquivos de projeto global necessário atualizar e determinar as estratégias de atualização com suporte. O **Assistente de atualização de** é invocada em seguida.  
  
 Depois que o usuário conclui o assistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> é chamado em cada fábrica de projeto para executar a atualização real. Para facilitar o backup, fornecem métodos de IVsProjectUpgradeViaFactory a <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> serviço para registrar os detalhes do processo de atualização. Este serviço não pode ser armazenado em cache.  
  
 Depois de atualizar todos os arquivos relevantes de global, cada fábrica de projeto pode optar por criar uma instância de um projeto. A implementação do projeto deve oferecer suporte <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado para atualizar todos os itens de projeto relevantes.  
  
> [!NOTE]
>  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método não fornece o serviço SVsUpgradeLogger. Esse serviço pode ser obtido chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Práticas recomendadas  
 Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> serviço para verificar se você editar um arquivo antes de editá-lo e pode salvá-lo antes de salvar. Isso ajudará o backup e implementações de atualização lidar com arquivos de projeto sob controle do código-fonte, arquivos com permissões insuficientes e assim por diante.  
  
 Use o <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas as fases de backup e atualizar para fornecer informações sobre o êxito ou falha do processo de atualização.  
  
 Para obter mais informações sobre como fazer backup e atualizar projetos, consulte os comentários para IVsProjectUpgrade vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a>Atualizando projetos personalizados
Se você alterar as informações mantidas no arquivo de projeto entre diferentes versões do Visual Studio do produto, você precisará dar suporte ao atualizar o arquivo de projeto do antigo para a nova versão. Para dar suporte a atualização que permite que você participe de **Assistente de conversão do Visual Studio**, implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Essa interface contém o único mecanismo disponível para a atualização da cópia. A atualização do projeto ocorre como uma parte da solução é aberta. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é implementada pela fábrica de projeto ou pelo menos deve ser obtido da fábrica de projeto.  
  
 O mecanismo antigo que usa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface também é suportada, mas conceitualmente atualiza o sistema de projeto como parte do projeto aberto. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface, portanto, é chamada pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente mesmo se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface chamada ou implementada. Essa abordagem permite que você use <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar a cópia e somente as partes da atualização de projeto e delegar o resto do trabalho a ser realizado no local (possivelmente no novo local), o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface.  
  
 Para um exemplo da implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [VSSDK exemplos](http://aka.ms/vs2015sdksamples).  
  
 Os cenários a seguir ocorrem com as atualizações do projeto:  
  
-   Se o arquivo for de um formato mais novo que o projeto pode suportar, ele deve retornar um erro informando isso. Isso pressupõe que a versão mais antiga do seu produto inclui código para verificar a versão.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> especificado no sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização será a ser implementada como uma atualização in-loco antes da abertura do projeto.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> sinalizador é especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização é implementado como uma atualização de cópia.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador é especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamar, em seguida, o usuário foi solicitado pelo ambiente de atualizar o arquivo de projeto como uma atualização in-loco, depois que o projeto é aberto. Por exemplo, o ambiente solicita ao usuário a atualização, quando o usuário abre uma versão mais antiga da solução.  
  
-   Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não for especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamar, em seguida, você deve solicitar ao usuário para atualizar o arquivo de projeto.  
  
     Uma mensagem de aviso de atualização exemplo é o seguinte:  
  
     "O projeto '%1' foi criado com uma versão mais antiga do Visual Studio. Se você abri-lo com esta versão do Visual Studio, você não poderá abri-lo com versões anteriores do Visual Studio. Deseja continuar e abrir este projeto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar IVsProjectUpgradeViaFactory  
  
1.  Implementar o método do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, especificamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método em sua implementação de fábrica de projeto, ou verifique as implementações chamado de sua implementação de fábrica de projeto.  
  
2.  Se você deseja fazer uma atualização no local como parte da solução de abertura, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
3.  Se você deseja fazer uma atualização no local como parte da solução de abertura, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
4.  Para ambas as as etapas 2 e 3, o arquivo real atualizar etapas usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, podem ser implementados conforme descrito no "Implementando `IVsProjectUpgade`" seção abaixo, ou você pode delegar a atualização real do arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Use os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> pós-atualização relacionados mensagens para o usuário usando o Assistente de migração do Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interface é usada para implementar qualquer tipo de atualização de arquivo que deve acontecer como parte da atualização do projeto. Esta interface não é chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, mas é fornecida como um mecanismo para atualizar os arquivos que fazem parte do sistema de projeto, mas o sistema de projeto principal pode não estar ciente diretamente. Por exemplo, essa situação pode ocorrer se o compilador relacionadas a arquivos e as propriedades não são tratadas pela equipe de desenvolvimento mesmo que lida com o restante do sistema de projeto.  
  
### <a name="ivsprojectupgrade-implementation"></a>Implementação de IVsProjectUpgrade  
 Se o sistema de projeto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> somente, ele não pode participar de **Assistente de conversão do Visual Studio**. No entanto, mesmo se você implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, você ainda pode delegar a atualização de arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar IVsProjectUpgrade  
  
1.  Quando um usuário tenta abrir um projeto, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado pelo ambiente depois que o projeto é aberto e antes de qualquer outro usuário ação possa ser executada no projeto. Se o usuário já tinha sido solicitado a atualizar a solução, o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador é passado a `grfUpgradeFlags` parâmetro. Se o usuário abre um projeto diretamente, tal como usando o **Adicionar projeto existente** comando, em seguida, o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não for passado e o projeto precisa solicitar ao usuário para atualizar.  
  
2.  Em resposta ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamada, o projeto deve avaliar se o arquivo de projeto será atualizado. Se o projeto não precisa atualizar o tipo de projeto para uma nova versão, ele pode simplesmente retornar a <xref:Microsoft.VisualStudio.VSConstants.S_OK> sinalizador.  
  
3.  Se o projeto precisa atualizar o tipo de projeto para uma nova versão, ele deve determinar se o arquivo de projeto pode ser modificado por meio da chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método e passando um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro. O projeto precisa fazer o seguinte:  
  
    -   Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, em seguida, a atualização pode continuar porque o arquivo de projeto pode ser gravado.  
  
    -   Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o `VSQueryEditResult` valor tem o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit definido, em seguida, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deve retornar a falha, porque os usuários devem resolver as permissões execute próprios. O projeto deve, em seguida, faça o seguinte:  
  
         Relatar o erro para o usuário chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> e retornar o <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> código de erro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Se o `VSQueryEditResult` valor é <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e `VSQueryEditResultFlags` valor tem o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> o conjunto de bits, em seguida, o arquivo de projeto deve fazer check-out chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Se o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chamada no arquivo de projeto faz com que o arquivo de check-out e a versão mais recente a ser recuperado, o projeto é descarregado e recarregado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado novamente depois que a outra instância do projeto é criada. Essa segunda chamada, o arquivo de projeto pode ser gravado em disco; Recomenda-se que o projeto de salvar uma cópia do arquivo do projeto no formato anterior com um. Extensão antigo, faça suas alterações de atualização necessárias e salve o arquivo de projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, o método deve indicar falha, retornando <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Isso faz com que o projeto para ser descarregado no Gerenciador de soluções.  
  
     É importante entender o processo de conclusão que ocorre no ambiente para o caso em que a chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método (especificando um valor de ReportOnly) retorna o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> sinalizadores.  
  
5.  O usuário tenta abrir o arquivo de projeto.  
  
6.  O ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
7.  Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retorna `true`, em seguida, o ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
8.  O ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementação para abrir o arquivo e inicializar o objeto de projeto, por exemplo, Project1.  
  
9. O ambiente chama seu `IVsProjectUpgrade::UpgradeProject` implementação para determinar se o arquivo de projeto precisa ser atualizado.  
  
10. Você chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passar um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
11. Retorna o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit é definido em `VSQueryEditResultFlags`.  
  
12. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> chamadas de implementação `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 Essa chamada pode causar uma nova cópia do arquivo do projeto para fazer check-out e recuperar a versão mais recente, bem como a necessidade de recarregar o arquivo de projeto. Neste ponto, uma das seguintes ações ocorrerá:  
  
-   Se você tratar recarregar seu próprio projeto, em seguida, o ambiente chama seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementação (VSITEMID_ROOT). Quando você receber essa chamada, recarregue a primeira instância do seu projeto (Project1) e continuar a atualizar o arquivo de projeto. O ambiente sabe que você manipule recarregar seu próprio projeto se você retornar `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Se você não tratar recarregar seu próprio projeto, você retornar `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). Nesse caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) retorna, o ambiente cria outra nova instância do seu projeto, por exemplo, Project2, da seguinte maneira:  
  
    1.  O ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> em seu primeiro objeto de projeto Project1, colocando esse objeto no estado inativo.  
  
    2.  O ambiente chama seu `IVsProjectFactory::CreateProject` implementação para criar uma segunda instância do seu projeto, Project2.  
  
    3.  O ambiente chama seu `IPersistFileFormat::Load` implementação para abrir o arquivo e inicializar o segundo objeto de projeto, Project2.  
  
    4.  O ambiente chama `IVsProjectUpgrade::UpgradeProject` pela segunda vez determinar se o objeto de projeto deve ser atualizado. No entanto, essa chamada é feita em um novo em segundo lugar, a instância do projeto, Project2. Este é o projeto é aberto na solução.  
  
        > [!NOTE]
        >  Na instância que seu primeiro projeto, Project1, é colocado no estado inativo, em seguida, você deve retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> da primeira chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementação.  
  
    5.  Você chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passar um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
    6.  Retorna o ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e a atualização pode continuar porque o arquivo de projeto pode ser gravado.  
  
 Se você não atualizar, retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> de `IVsProjectUpgrade::UpgradeProject`. Se nenhuma atualização é necessária ou se você optar por não atualizar, tratar o `IVsProjectUpgrade::UpgradeProject` chamar como não operacional. Se você retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, um nó de espaço reservado é adicionado à solução para seu projeto.  
  
## <a name="upgrading-project-items"></a>Atualizando itens de projeto
  
Se você adicionar ou gerenciar itens em sistemas de projeto, você não implemente, convém participar do processo de atualização de projeto. Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema de projeto.  
  
 Normalmente, os implementadores de item de projeto desejam aproveitar um projeto já totalmente instanciado e atualizado porque eles precisam saber que o projeto são referências e o que outras propriedades do projeto existem para tomar uma decisão de atualização.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Para obter a notificação de atualização de projeto  
  
1.  Definir o <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> sinalizador (definido em vsshell80.idl) em sua implementação de item de projeto. Isso faz com que o item de projeto VSPackage automaticamente carregar quando o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell determina que um sistema de projeto está em processo de atualização.  
  
2.  Informe o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> por meio da interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> método.  
  
3.  O <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionada depois que a implementação do sistema de projeto completar suas operações de atualização e o novo projeto atualizado é criado. Dependendo do cenário, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionada após o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, ou o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> métodos.  
  
### <a name="to-upgrade-the-project-item-files"></a>Para atualizar os arquivos de item de projeto  
  
1.  Você deve gerenciar cuidadosamente o processo de backup do arquivo em sua implementação de item de projeto. Isso se aplica especificamente para um backup de lado a lado, onde o `fUpgradeFlag` parâmetro o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método está definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, onde os arquivos de backup são colocados ao longo de arquivos lado que são designados como "old". Os arquivos de backup mais antigos do que a hora do sistema quando o projeto foi atualizado podem ser designados como obsoleto. Além disso, eles podem ser substituídos, a menos que você seguir etapas específicas para evitar isso.  
  
2.  No momento em que o item de projeto recebe uma notificação de atualização de projeto, o **Assistente de conversão do Visual Studio** ainda será exibido. Portanto, você deve usar os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interface para fornecer mensagens de atualização para o Assistente de interface do usuário.  
  
## <a name="see-also"></a>Consulte também  
 [Projetos](../../extensibility/internals/projects.md)   
