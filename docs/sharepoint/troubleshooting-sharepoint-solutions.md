---
title: Solucionando problemas de soluções do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 12de0ea2e9638c7ab523bbda0e623c84d0182aad
ms.sourcegitcommit: cc88ccc6aacebe497899fab05d243a65053e194c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="troubleshooting-sharepoint-solutions"></a>Solucionando problemas de soluções do SharePoint
  Os seguintes problemas ou alertas que podem ocorrer quando você depura soluções do SharePoint usando o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador. Para obter mais informações, consulte [depuração soluções de fluxo de trabalho do SharePoint 2007](http://msdn.microsoft.com/en-us/3a5392f3-66f3-48be-956e-02de23fa6247).
  
## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>Restrições de token em área restrita do Visual Web Parts  
 Visual web parts em soluções de área restrita não é possível processar tokens padrão, como $SPUrl, que dá suporte ao tempo de execução do SharePoint. Como resultado, a URL não for resolvida, e não é possível visualizar o conteúdo no modo de Design no designer de parte do visual web se você fizer referência a ele diretamente em um elemento de script, como no exemplo a seguir:  
  
```xml  
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>  
```  
  
 Para contornar essa limitação e resolver o token, consulte usando literais:  
  
```xml  
<asp:literal ID="Literal1" runat="server" Text="<script src='" />  
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />  
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />  
```  
  
## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>Restrições de caractere em nomes de projetos e itens de projeto  
 Nomes de projetos e itens de projeto podem conter apenas caracteres válidos em um caminho de implantação do SharePoint 2010. Não há outros caracteres são permitidos.  
  
### <a name="error-message"></a>Mensagem de erro  
 Mensagem de erro "Caracteres inválidos".  
  
### <a name="resolution"></a>Resolução  
 Para nomes de projetos do SharePoint e itens de projeto, use apenas os seguintes caracteres:  
  
-   Caracteres ASCII alfanuméricos  
  
-   Espaço  
  
-   Ponto final (.)  
  
-   Vírgula (,)  
  
-   Caractere de sublinhado (_)  
  
-   Traço (-)  
  
-   Barra invertida (\\)  
  
 Quando um projeto é empacotado, uma regra de validação verifica se a propriedade do caminho de implantação para cada arquivo que você está implantando contém apenas esses caracteres válidos.  
  
## <a name="errors-when-creating-custom-fields"></a>Erros ao criar campos personalizados  
 Em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], campos personalizados são definidos em XML. Podem ocorrer erros se um campo não está definido ou referenciado usando um formato específico.  
  
### <a name="error-message"></a>Mensagem de erro  
 Mensagem de erro "Caracteres inválidos" em vez de empacotamento.  
  
### <a name="resolution"></a>Resolução  
 A ID de uma definição de campo deve ser um GUID entre colchetes, como mostra o exemplo a seguir:  
  
```xml  
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Type="Note"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Group="A Custom Group">  
</Field>.  
```  
  
 Como mostra o exemplo a seguir, uma referência de campo em um tipo de conteúdo deve ser definida usando o formato de elemento vazio (\<FieldRef / >), não por meio de elementos de início/término (\<FieldRef >\</FieldRef >):  
  
```xml  
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"   
    Name="PatientName"   
    DisplayName="Patient Name"   
    Required="TRUE"/>  
```  
  
 Se o XML de origem para o campo está malformado, não é um arquivo XML válido ou exibe algum outro problema, o erro "não é possível analisar o arquivo" ocorre.  
  
## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>Novas definições de Site diferente do inglês não aparecem na página de criação de Site depois da implantação  
 Depois de criar e implantar uma definição de site usando uma versão diferente do inglês do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (ou seja, uma versão com uma localidade [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] diferente 1033), o **SharePoint personalizações** guia não aparece no **Seleção de modelo** caixa e o novo modelo de site não aparecer no **novo Site do SharePoint** página.  
  
### <a name="error-message"></a>Mensagem de erro  
 nenhuma.  
  
### <a name="resolution"></a>Resolução  
 Esse problema ocorre devido a um valor incorreto no **caminho** propriedade para o arquivo de configuração do webtemp site definição, como webtemp_SiteDefinitionProject1.xml. No **caminho** propriedade para o arquivo webtemp, localizado sob o **local de implantação**, altere 1033 para a localidade apropriada [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]. Por exemplo, para usar uma localidade japonês altere o valor para 1041. Para obter mais informações, consulte [IDs de localidade atribuídas pela Microsoft](http://go.microsoft.com/fwlink/?LinkID=165561) no site do MSDN.  
  
## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>Erro aparece quando um projeto de fluxo de trabalho é implantado em um sistema limpo  
 Esse problema ocorre se você implantar um projeto de fluxo de trabalho em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] em um sistema limpo. Um sistema limpo é um computador que tenha uma instalação nova do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e do SharePoint, mas não há projetos de fluxo de trabalho implantado.  
  
### <a name="error-message"></a>Mensagem de erro  
 Não é possível localizar a lista do SharePoint: histórico de fluxo de trabalho.  
  
### <a name="resolution"></a>Resolução  
 Esse erro ocorre devido a uma lista de histórico de fluxo de trabalho ausente. Como o ambiente de desenvolvimento é um sistema limpo, não há fluxos de trabalho são implantados e a lista de histórico de fluxo de trabalho ainda não existir. Para resolver esse problema, abra novamente o Assistente de fluxo de trabalho, o que faz com que a lista de histórico de fluxo de trabalho a ser criado.  
  
##### <a name="to-reenter-the-workflow-wizard"></a>Insira novamente o Assistente de fluxo de trabalho  
  
1.  Em **Solution Explorer**, escolha o nó de fluxo de trabalho.  
  
2.  No **propriedades** janela, escolha o botão de reticências (...) em qualquer propriedade que tem um botão de reticências.  
  
## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>Usuário deve atualizar a página de aplicativo no navegador enquanto a depuração para exibir a imagem atualizada  
 Se você estiver depurando uma solução do SharePoint que contém uma página de aplicativo com um controle que exibe uma imagem, como um [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] controle de imagem, você deve atualizar a página no navegador para exibir as alterações feitas na imagem.  
  
## <a name="error-the-site-location-is-not-valid"></a>Erro: O local do Site não é válido  
 Esse problema pode ocorrer se [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] não está instalado. Ele também pode ocorrer se você não tiver acesso de administrador para o site do SharePoint que é especificado no **Assistente de personalização do SharePoint**.  
  
### <a name="error-message"></a>Mensagem de erro  
  
-   Local do site do SharePoint não é válido.  
  
### <a name="resolution"></a>Resolução  
  
-   Instalar [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
-   Certifique-se de que você tem acesso de administrador para o site do SharePoint. Para obter mais informações, consulte o [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] artigo Online [atribuir ou remover administradores de aplicativos de serviço no SharePoint Server](https://docs.microsoft.com/en-us/sharepoint/administration/assign-or-remove-administrators-of-service-applications).  
  
## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>Evento de Web de exclusão de site não ocorre no projeto do receptor de evento  
 Quando você cria um projeto de receptor de evento e selecione determinados eventos da Web, como "um site está sendo excluído", ocorre o evento nunca.  
  
### <a name="error-message"></a>Mensagem de erro  
 nenhuma.  
  
### <a name="resolution"></a>Resolução  
 Esse problema ocorre porque o escopo do recurso deve ser "Site" para tratar eventos de nível de site, mas o escopo do recurso padrão para projetos de receptor de evento é "Web". Os eventos da Web afetados são:  
  
-   Um site está sendo excluído (WebDeleting)  
  
-   Um site foi excluído (WebDeleted)  
  
-   Um site está sendo movido (WebMoving)  
  
-   Um site foi movido (WebMoved)  
  
 Para corrigir o problema, altere o escopo do recurso do receptor do evento, da seguinte maneira.  
  
##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>Para alterar o escopo do recurso do receptor do evento  
  
1.  Em **Solution Explorer**, abrir o arquivo de .feature do receptor de evento no **recurso Designer** por duas vezes no arquivo ou abrir o menu de atalho e escolhendo **abrir**.  
  
2.  Clique na seta ao lado de **escopo**e, em seguida, escolha **Site** que aparece na lista.  
  
## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>Erro de implantação é exibida depois que o nome de um identificador em um projeto de modelo de conectividade de dados de negócios é alterado  
 Esse problema ocorre se você alterar o nome do identificador de uma entidade em um modelo de conectividade de dados de negócios (BDC) e, em seguida, tente implantar a solução.  
  
### <a name="error-messages"></a>Mensagens de erro  
  
-   \<*nome do modelo*> tem os seguintes erros de ativação de tipo de conteúdo externo...  
  
-   IMetadataObject com nome '\<*nome do modelo*>' tem um valor no campo 'nome' duplicado...  
  
### <a name="resolution"></a>Resolução  
 Para resolver esse problema, exclua manualmente o modelo e, em seguida, implante a solução novamente.  Você pode excluir o modelo usando uma das ferramentas a seguir:  
  
-   Administração de Central do SharePoint 2010. Para obter mais informações, consulte [gerenciamento de modelo BDC](http://go.microsoft.com/fwlink/?LinkID=181472) no site da Web do Microsoft TechNet.  
  
-   Windows PowerShell. Você pode excluir o modelo digitando o seguinte comando no prompt de comando: **SPBusinessDataCatalogModel remover**. Para obter mais informações, consulte [geral cmdlets (SharePoint Server 2010)](http://go.microsoft.com/fwlink/?LinkID=182375) no site da Web do Microsoft TechNet.  
  
## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>Um erro será exibido quando você tenta exibir uma Web Part Visual do SharePoint  
 Esse problema ocorre quando o **caminho** propriedade do controle de usuário não começa com a cadeia de caracteres "CONTROLTEMPLATES\\".  
  
### <a name="error-messages"></a>Mensagens de erro  
  
-   O arquivo ' /_CONTROLTEMPLATES/*\<nome do projeto >*/*\<nome da Web Part >*/*\<controle de usuário nome >*. ascx ' não existe.  
  
-   Erro de servidor no aplicativo '/'.  
  
### <a name="resolution"></a>Resolução  
  
##### <a name="to-resolve-this-issue"></a>Para resolver esse problema  
  
1.  Em **Solution Explorer**, escolha o arquivo de controle de usuário, cuja extensão de nome de arquivo é. ascx.  
  
2.  Na barra de menus, escolha **exibição**, **janela propriedades**.  
  
3.  No **propriedades** janela, expanda o **local de implantação** nó.  
  
4.  Certifique-se de que o valor de **caminho** propriedade começa com a cadeia de caracteres "CONTROLTEMPLATES\\".  
  
## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>Erro aparece quando um fluxo de trabalho reutilizável importado que contém um campo de formulário de tarefa é executado  
 Esse problema ocorre se você importa um fluxo de trabalho que contém um formulário de tarefa que tem um campo e, em seguida, executa o novo fluxo de trabalho no mesmo sistema do qual você importou.  
  
### <a name="error-message"></a>Mensagem de erro  
 Ocorreu um erro na etapa de implantação 'Ativar recursos': O campo com a Id [*Guid*] definida no recurso [*Guid*] foi encontrado no conjunto de sites atual ou em um subsite.  
  
### <a name="resolution"></a>Resolução  
 Esse erro é o resultado de colisões de ID de campo que ocorrem porque o fluxo de trabalho reutilizável de importação de projeto em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] não altera o campo de formulário de tarefa IDs. Se você implantar um fluxo de trabalho importado no mesmo servidor que contém o fluxo de trabalho original, ocorrerem conflitos de ID de campo.  
  
 Para resolver esse problema, use o recurso Localizar e substituir para alterar o valor do atributo ID do campo em todos os arquivos de fluxo de trabalho importados.  
  
## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>Erro aparece quando renomeado importado é executada a instância de lista  
 Esse problema ocorre se você renomear uma instância de lista importada e, em seguida, executá-lo no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
### <a name="error-message"></a>Mensagem de erro  
 Erro de compilação: erro na etapa de implantação 'Ativar recursos': O arquivo Template\Features\\[*Importar projeto**recurso**nome*]\Files\Lists\\[*antigo**nome da lista*]\Schema.xml não existe.  
  
### <a name="resolution"></a>Resolução  
 Quando você importar uma instância de lista, um atributo chamado CustomSchema é adicionado ao arquivo Elements da instância de lista. Elements inclui o caminho de um Schema. XML personalizado para a instância de lista. Quando você renomear a instância de lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], o caminho de implantação para o Schema. XML personalizado for alterado, mas o valor do caminho do atributo CustomSchema não é atualizado. Como resultado, a instância da lista não é possível localizar o arquivo Schema no caminho antigo que é especificado pelo atributo CustomSchema quando o recurso está ativado.  
  
 Para resolver esse problema, atualize o caminho do local do arquivo schema.xml no atributo CustomSchema de implantação.  
  
## <a name="sharepoint-debugging-session-terminated-by-iis"></a>SharePoint encerrado pelo IIS de sessão de depuração  
 Esse problema ocorre se você definir um ponto de interrupção em um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solução do SharePoint, escolha a tecla F5 para executá-lo e, em seguida, permanecem em um ponto de interrupção mais de 90 segundos.  
  
### <a name="error-message"></a>Mensagem de erro  
 O processo do servidor Web que estava sendo depurado foi encerrado pelo Internet Information Services (IIS). Você pode evitar esse problema, definindo configurações de ping do Pool de aplicativos no IIS. Consulte a Ajuda para obter mais detalhes.  
  
### <a name="resolution"></a>Resolução  
 Por padrão, o pool de aplicativos IIS aguardará 90 segundos para um aplicativo responder antes que ele fecha o aplicativo. Esse processo é conhecido como "ping" o aplicativo. Para resolver esse problema, você pode aumentar o tempo de espera ou desabilitar ping totalmente o aplicativo.  
  
##### <a name="to-access-the-iis-app-pool-settings"></a>Para acessar as configurações de pool de aplicativos do IIS  
  
1.  Abra o Gerenciador do IIS.  
  
2.  No **conexões** painel, expanda o nó do servidor do SharePoint e, em seguida, escolha o **Pools de aplicativos** nó.  
  
3.  No **Pools de aplicativos** página, escolha o pool de aplicativos do SharePoint (normalmente "SharePoint - 80") e, em seguida, no **ações** painel, escolha o **configurações avançadas** link.  
  
4.  Para aumentar o tempo de espera antes do tempo limite do IIS, altere o valor de **tempo máximo de resposta do Ping (segundos)** para um valor maior que 90 segundos.  
  
5.  Para desabilitar a execução de ping do IIS, defina **Ping habilitado** para **False**.  
  
## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>Cancele automaticamente deixa órfãos lista instância no SharePoint  
 Esse problema ocorre se você executar as etapas a seguir.  
  
1.  Criar uma definição de lista que tem uma instância de lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Pressione a tecla F5 para executar a solução.  
  
3.  Parar a depuração, ou feche o site do SharePoint.  
  
4.  Abra o site do SharePoint e abra a instância da lista.  
  
### <a name="error-message"></a>Mensagem de erro  
 Erro de servidor no aplicativo '/'.  
  
### <a name="resolution"></a>Resolução  
 Isso acontece porque, após você fechar uma sessão de depuração de uma solução do SharePoint, a retirada automaticamente recurso retira a solução. O cancelamento exclui a definição de lista do SharePoint, mas não exclui a instância da lista. A definição da lista subjacente é necessário para a instância da lista.  
  
 Para resolver esse problema, implante a solução, na barra de menus, escolhendo **criar**, **implantar**. (Não depurar a solução, escolha a tecla F5.) Em seguida, exclua a instância de lista do SharePoint.  
  
## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>Solução do SharePoint original é substituída por uma versão exportada  
 Se você exportar uma solução do SharePoint, importar a solução em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]e, em seguida, implantar a solução de volta para o mesmo local do qual ele foi exportado, a solução do SharePoint original será substituída. Esse problema não ocorre se você implantar a solução em um servidor que não tem a solução original ativada.  
  
### <a name="error-message"></a>Mensagem de erro  
 nenhuma.  
  
### <a name="resolution"></a>Resolução  
 Para evitar a substituição de uma solução no site do qual ele foi exportado, alterar os GUIDs da ID da solução e as IDs de recurso de todos os recursos importados no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projeto.  
  
## <a name="error-appears-when-debugging-starts"></a>Erro aparece quando a depuração iniciar  
 Quando você depura uma solução do SharePoint no Visual Studio, um erro indica que o Visual Studio não pôde carregar o arquivo Web. config porque a chave fornecida não estava no dicionário.  
  
### <a name="error-message"></a>Mensagem de erro  
 Não foi possível carregar o arquivo de configuração Web. config. Verifique o arquivo para todos os elementos XML malformados e tente novamente. Ocorreu o seguinte erro: A chave fornecida não estava presente no dicionário.  
  
### <a name="resolution"></a>Resolução  
 Para resolver esse problema, certifique-se de que o valor da propriedade URL do Site do projeto do SharePoint no Visual Studio corresponde à URL que é atribuída para a zona padrão para os mapeamentos alternativos de acesso do aplicativo web. Você não pode resolver o erro usando outra zona, como a Intranet, para a URL. O site de URL para o projeto e a URL na zona padrão devem corresponder. Para acessar os mapeamentos alternativos de acesso, abra o utilitário de Administração Central do SharePoint 2010, escolha o **gerenciamento de aplicativos** link e, em seguida, em **aplicativos Web**, escolha o  **Configurar mapeamentos alternativos de acesso** link. Para obter mais informações, consulte [criar zonas para aplicativos Web](http://go.microsoft.com/fwlink/?LinkId=192274).  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas do SharePoint empacotamento e implantação](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)   
 [Compilando e depurando soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
  
  
