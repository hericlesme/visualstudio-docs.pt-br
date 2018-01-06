---
title: "Implantando uma solução do Office usando o ClickOnce | Microsoft Docs"
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
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
ms.assetid: feb516b3-5e4d-449a-9fd2-347d08d90252
caps.latest.revision: "59"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0076eea1fa8866ad90bf4125583ed8359916de4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-office-solution-by-using-clickonce"></a>Implantando uma solução do Office usando o ClickOnce
  Se você usar o ClickOnce, você pode implantar sua solução do Office em menos etapas. Se você publicar atualizações, sua solução vai detectá-las e instalá-las automaticamente. No entanto, o ClickOnce exige que sua solução seja instalada separadamente para cada usuário de um computador. Portanto, é preciso considerar o uso do Windows Installer (.msi) se mais de um usuário for executar a solução no mesmo computador.  
  
## <a name="in-this-topic"></a>Neste tópico  
  
-   [Publicar a solução](#Publish)  
  
-   [Decida como você deseja conceder confiança para a solução](#Trust)  
  
-   [Ajudar os usuários a instalar a solução](#Helping)  
  
-   [Coloque o documento de uma solução para o computador do usuário final (somente no nível do documento personalizações)](#Put)  
  
-   [Coloque o documento de uma solução em um servidor que está executando o SharePoint (somente no nível do documento personalizações)](#SharePoint)  
  
-   [Criar um instalador personalizado](#Custom)  
  
-   [Publicar uma atualização](#Update)  
  
-   [Alterar o local de instalação de uma solução](#Location)  
  
-   [Reverter uma solução para uma versão anterior](#Roll)  
  
 Para obter mais informações sobre como implantar uma solução do Office, criando um arquivo do Windows Installer, consulte [Implantando uma solução do Office usando o Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Publish"></a>Publicar a solução  
 Você pode publicar sua solução usando o **Assistente de publicação** ou **Project Designer**. Neste procedimento, você usará o **Project Designer** porque ele fornece o conjunto completo de opções de publicação. Consulte [publicar Assistente &#40; desenvolvimento do Office no Visual Studio &#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).  
  
#### <a name="to-publish-the-solution"></a>Para publicar a solução  
  
1.  Em **Solution Explorer**, escolha o nó que é nomeado para seu projeto.  
  
2.  Na barra de menus, escolha **projeto**, *ProjectName* **propriedades**.  
  
3.  No **Project Designer**, escolha o **publicar** guia, que mostra a ilustração a seguir.  
  
     ![A guia de publicação no Designer de projeto](../vsto/media/vsto-publishtab.png "guia Publicar no Designer de projeto")  
  
4.  No **local da pasta de publicação (servidor ftp ou caminho do arquivo)** caixa, digite o caminho da pasta onde você deseja que o **Project Designer** para copiar os arquivos de solução.  
  
     Você pode inserir qualquer um destes tipos de caminho.  
  
    -   Um caminho local (por exemplo, *C:\FolderName\FolderName*).  
  
    -   Um caminho de convenção de nomenclatura uniforme (UNC) para uma pasta da rede (por exemplo,  *\\\ServerName\FolderName*).  
  
    -   Um caminho relativo (por exemplo, *PublishFolder\\*, que é a pasta na qual o projeto é publicado por padrão).  
  
5.  No **URL da pasta de instalação** , digite o caminho totalmente qualificado do local onde os usuários finais encontrará sua solução.  
  
     Se você não souber o local, não insira nesse campo. Por padrão, o ClickOnce procura atualizações na pasta da qual seus usuários instalam a solução.  
  
6.  Escolha o botão **Pré-requisitos**.  
  
7.  No **pré-requisitos** caixa de diálogo caixa, certifique-se de que o **criar o programa de instalação para instalar os componentes de pré-requisito** caixa de seleção é marcada.  
  
8.  No **escolha quais pré-requisitos para instalar** , selecione as caixas de seleção **Windows Installer 4.5** e o pacote apropriado do .NET Framework.  
  
     Por exemplo, se seus destinos de solução de [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], marque as caixas de seleção para **Windows Installer 4.5** e **Microsoft .NET Framework 4.5 Full**.  
  
9. Se sua solução tem como alvo o .NET Framework 4.5, selecione também a **Visual Studio 2010 Tools for Office Runtime** caixa de seleção.  
  
    > [!NOTE]  
    >  Por padrão, essa caixa de seleção não aparecerá. Para mostrá-la, é preciso criar um pacote Bootstrapper. Consulte [criando um pacote de Bootstrapper para um Office 2013 VSTO suplemento com o Visual Studio 2012](http://blogs.msdn.com/b/vsto/archive/2012/12/21/creating-a-bootstrapper-package-for-an-office-2013-vsto-add-in-with-visual-studio-2012.aspx).  
  
10. Em **especificar o local de instalação de pré-requisitos**, escolha uma das opções que aparecem e, em seguida, escolha o **Okey** botão.  
  
     A tabela a seguir descreve cada opção.  
  
    |Opção|Descrição|  
    |------------|-----------------|  
    |**Baixar os pré-requisitos no site do fornecedor do componente**|É solicitado que o usuário baixe e instale esses pré-requisitos do fornecedor.|  
    |**Baixar os pré-requisitos no mesmo local do meu aplicativo**|O software de pré-requisito é instalado com a solução. Se você escolher essa opção, o Visual Studio copiará todos os pacotes do pré-requisito no local de publicação. Para que essa opção funcione, os pacotes do pré-requisito devem estar no computador de desenvolvimento.|  
    |**Baixar os pré-requisitos no seguinte local**|O Visual Studio copia todos os pacotes do pré-requisito no local que você especifica e os instala com a solução.|  
  
     Consulte [caixa de diálogo pré-requisitos](/visualstudio/ide/reference/prerequisites-dialog-box).  
  
11. Escolha o **atualizações** botão, especifique a frequência desejada para do cada usuário final suplemento do VSTO ou personalização para verificar se há atualizações e, em seguida, escolha o **Okey** botão.  
  
    > [!NOTE]  
    >  Se você estiver implantando usando um CD ou uma unidade removível, escolha o **nunca verificar se há atualizações** botão de opção.  
  
     Para obter informações sobre como publicar uma atualização, consulte [publicar uma atualização](#Update).  
  
12. Escolha o **opções** botão, examine as opções no **opções** caixa de diálogo caixa e, em seguida, escolha o **Okey** botão.  
  
13. Escolha o **publicar agora** botão.  
  
     O Visual Studio adiciona as pastas e os arquivos a seguir à pasta de publicação que você especificou anteriormente neste procedimento.  
  
    -   O **arquivos de aplicativo** pasta.  
  
    -   O programa de instalação.  
  
    -   Um manifesto de implantação que aponta para o manifesto de implantação da versão mais recente.  
  
     O **arquivos de aplicativo** pasta contém uma subpasta para cada versão que você publicar. Cada subpasta específica da versão contém os arquivos a seguir.  
  
    -   Um manifesto de aplicativo.  
  
    -   Um manifesto de implantação.  
  
    -   Assemblies de personalização.  
  
     A ilustração a seguir mostra a estrutura da pasta de publicação para um suplemento do VSTO do Outlook.  
  
     ![Publicar a estrutura de pasta](../vsto/media/publishfolderstructure.png "publicar estrutura de pastas")  
  
    > [!NOTE]  
    >  ClickOnce acrescenta a extensão. Deploy para assemblies de modo que uma instalação segura do Internet Information Services (IIS) não bloqueia os arquivos devido a uma extensão não segura. Quando o usuário instala a solução, o ClickOnce remove a extensão .deploy.  
  
14. Copie os arquivos da solução no local de instalação que você especificou anteriormente neste procedimento.  
  
##  <a name="Trust"></a>Decida como você deseja conceder confiança para a solução  
 Para que uma solução possa ser executada nos computadores dos usuários, você deve conceder confiança ou os usuários devem responder a uma solicitação de confiança quando instalam a solução. Para conceder confiança à solução, assine o manifesto usando um certificado que identifique um fornecedor conhecido e confiável. Consulte [confiantes a solução ao assinar o aplicativo e implantação manifestos](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
 Se você estiver implantando uma personalização no nível do documento e você deseja colocar o documento em uma pasta no computador do usuário ou disponibilizar o documento em um site do SharePoint, certifique-se de que o Office confie o local do documento. Consulte [concedendo confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
##  <a name="Helping"></a>Ajudar os usuários a instalar a solução  
 Os usuários podem instalar a solução executando o programa de instalação, abrindo o manifesto de implantação ou, no caso de uma personalização no nível de documento, abrindo o documento diretamente. Como uma prática recomendada, os usuários devem instalar a solução usando o programa de instalação. As duas abordagens não Certifique-se de que o software de pré-requisito está instalado. Se os usuários desejarem abrir o documento do local de instalação, eles deverão adicioná-lo à lista de locais confiáveis na Central de Confiabilidade do aplicativo do Office.  
  
### <a name="opening-the-document-of-a-document-level-customization"></a>Abrindo o documento de uma personalização no nível de documento  
 Os usuários podem abrir o documento de uma personalização no nível de documento diretamente do local de instalação ou copiando o documento no computador local e, em seguida, abrindo a cópia.  
  
 Como uma prática recomendada, os usuários devem abrir uma cópia do documento nos respectivos computadores para que vários usuários não tentem abrir a mesma cópia ao mesmo tempo. Para impor essa prática, você pode configurar o programa de instalação para copiar o documento nos computadores dos usuários. Consulte [colocar o documento de uma solução para o computador do usuário final (somente no nível do documento personalizações)](#Put).  
  
### <a name="installing-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instalando a solução abrindo o manifesto de implantação de um site do IIS  
 Os usuários podem instalar uma solução do Office abrindo o manifesto de implantação na Web. No entanto, uma instalação protegida do IIS (Serviços de Informações da Internet) bloqueará arquivos que tenham a extensão .vsto. O tipo de MIME deve ser definido no IIS para que você possa implantar uma solução do Office usando o IIS.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Para adicionar o tipo de MIME .vsto ao IIS 6.0  
  
1.  No servidor que está executando o IIS 6.0, escolha **iniciar**, **todos os programas**, **ferramentas administrativas**, **doGerenciadordeserviçosdeinformaçõesdaInternet(IIS)**.  
  
2.  Escolha o nome do computador, o **Sites da Web** pasta ou site da web que você está configurando.  
  
3.  Na barra de menus, escolha **ação**, **propriedades**.  
  
4.  Sobre o **cabeçalhos HTTP** guia, escolha o **tipos MIME** botão.  
  
5.  No **tipos MIME** janela, escolha o **novo** botão.  
  
6.  No **tipo MIME** janela, digite **.vsto** como a extensão, digite **application/x-ms-vsto** como MIME de tipo e, em seguida, aplicar as novas configurações.  
  
    > [!NOTE]  
    >  Para que as alterações entrem em vigor, você deve reiniciar o Serviço de Publicação na World Wide Web ou aguardar até que o processo de trabalho seja reciclado. Você deve liberar o cache de disco do navegador e tentar abrir o arquivo .vsto novamente.  
  
##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Para adicionar o tipo MIME .vsto para o IIS 7.0  
  
1.  No servidor que está executando o IIS 7.0, escolha **iniciar**, **todos os programas**, **Acessórios**.  
  
2.  Abra o menu de atalho para **Prompt de comando**e, em seguida, escolha **executar como administrador.**  
  
3.  No **abrir** caixa, digite o seguinte caminho e, em seguida, escolha o **Okey** botão.  
  
    ```  
    %windir%\system32\inetsrv   
    ```  
  
4.  Insira o comando a seguir e aplique as novas configurações.  
  
    ```  
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  
  
    > [!NOTE]  
    >  Para que as alterações entrem em vigor, você deve reiniciar o Serviço de Publicação na World Wide Web ou deve aguardar até que o processo de trabalho seja reciclado. Você deve liberar o cache de disco do navegador e tentar abrir o arquivo .vsto novamente.  
  
##  <a name="Put"></a>Coloque o documento de uma solução para o computador do usuário final (somente no nível do documento personalizações)  
 Você pode copiar o documento de sua solução no computador do usuário final para eles, criando uma ação de pós-implantação. Dessa forma, o usuário não precisa copiar manualmente o documento do local de instalação para o computador depois de instalar a solução. Você precisará criar uma classe que define a ação de pós-implantação, criar e publicar a solução, modifique o manifesto do aplicativo e assinar novamente o manifesto de aplicativo e implantação.  
  
 Os procedimentos a seguir pressupõem que o nome do projeto é **ExcelWorkbook** e publique-a solução para o **C:\publish** diretório em seu computador.  
  
### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Criar uma classe que defina a ação de pós-implantação  
  
1.  Na barra de menus, escolha **arquivo**, **adicionar**, **novo projeto**.  
  
2.  No **adicionar novo projeto** na caixa de **modelos instalados** painel, escolha o **Windows** pasta.  
  
3.  No **modelos** painel, escolha o **biblioteca de classes** modelo.  
  
4.  No **nome** , digite **FileCopyPDA**e, em seguida, escolha o **Okey** botão.  
  
5.  Em **Solution Explorer**, escolha o **FileCopyPDA** projeto.  
  
6.  Na barra de menus, escolha **Projeto**, **Adicionar Referência**.  
  
7.  Sobre o **.NET** guia, adicione referências a Microsoft.VisualStudio.Tools.Applications.Runtime e Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
8.  Renomeie a classe para `FileCopyPDA` e substitua o conteúdo do arquivo pelo código. Esse código executa as seguintes tarefas:  
  
    -   Copia o documento na área de trabalho do usuário  
  
    -   Altera a propriedade assemblylocation de um caminho relativo para um caminho totalmente qualificado para o manifesto de implantação.  
  
    -   Exclui o arquivo se o usuário desinstalar a solução.  
  
     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  
  
### <a name="build-and-publish-the-solution"></a>Compilar e publicar a solução  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **FileCopyPDA** do projeto e, em seguida, escolha **criar**.  
  
2.  Abra o menu de atalho para o **ExcelWorkbook** do projeto e, em seguida, escolha **criar**.  
  
3.  Abra o menu de atalho para o **ExcelWorkbook** do projeto e, em seguida, escolha **adicionar referência**.  
  
4.  No **adicionar referência** caixa de diálogo caixa, escolha o **projetos** guia, escolha **FileCopyPDA**e, em seguida, escolha o **Okey** botão.  
  
5.  Em **Solution Explorer**, escolha o **ExcelWorkbook** projeto.  
  
6.  Na barra de menus, escolha **projeto**, **nova pasta**.  
  
7.  Insira **dados**e, em seguida, escolha a tecla Enter.  
  
8.  Em **Solution Explorer**, escolha o **dados** pasta.  
  
9. Na barra de menus, escolha **projeto**, **Add Existing Item**.  
  
10. No **Add Existing Item** caixa de diálogo, navegue até o diretório de saída para o **ExcelWorkbook** de projeto, escolha o **ExcelWorkbook.xlsx** de arquivo e, em seguida, escolha o  **Adicionar** botão.  
  
11. Em **Solution Explorer** escolha o **ExcelWorkbook.xlsx** arquivo.  
  
12. No **propriedades** janela, altere o **ação de compilação** propriedade **conteúdo** e o **copiar para diretório de saída** propriedade  **Copiar se mais recente**.  
  
     Quando você concluir essas etapas, seu projeto será semelhante a ilustração a seguir.  
  
     ![Estrutura do projeto da ação de implantação de postagem. ] (../vsto/media/vsto-postdeployment.png "Estrutura da ação de implantação de postagem do projeto.")  
  
13. Publicar o **ExcelWorkbook** projeto.  
  
### <a name="modify-the-application-manifest"></a>Modificar o manifesto de aplicativo  
  
1.  Abra o **c:\publish** diretório usando **Explorador de arquivos**.  
  
2.  Abra o **arquivos de aplicativo** pasta e, em seguida, abra a pasta que corresponde a mais recente publicada versão da solução.  
  
3.  Abra o **ExcelWorkbook.dll.manifest** em um editor de texto como bloco de notas.  
  
4.  Depois do elemento `</vstav3:update>`, adicione o código a seguir. Para o atributo de classe do `<vstav3:entryPoint>` elemento, use a seguinte sintaxe: *NamespaceName.ClassName*. No exemplo a seguir, os nomes de classe e o namespace são iguais, de modo que o nome do ponto de entrada resultante é `FileCopyPDA.FileCopyPDA`.  
  
    ```  
    <vstav3:postActions>  
      <vstav3:postAction>  
        <vstav3:entryPoint  
          class="FileCopyPDA.FileCopyPDA">  
          <assemblyIdentity  
            name="FileCopyPDA"  
            version="1.0.0.0"  
            language="neutral"  
            processorArchitecture="msil" />  
        </vstav3:entryPoint>  
        <vstav3:postActionData>  
        </vstav3:postActionData>  
      </vstav3:postAction>  
    </vstav3:postActions>  
    ```  
  
### <a name="re-sign-the-application-and-deployment-manifests"></a>Assinar novamente os manifestos de aplicativo e implantação  
  
1.  No **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook** pasta, copie o **ExcelWorkbook_TemporaryKey.pfx** arquivo de certificado e, em seguida, cole-o  *PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ pasta.
  
2.  Abra o prompt de comando do Visual Studio e, em seguida, altere os diretórios para o **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ pasta (por exemplo, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).  
  
3.  Assine o manifesto de aplicativo modificado executando o seguinte comando:  
  
    ```  
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  
  
     A mensagem "ExcelWorkbook.dll.manifest assinado com êxito" é exibida.  
  
4.  Altere para o **c:\publish** pasta e, em seguida, atualização e a implantação de entrada de manifesto, executando o seguinte comando:  
  
    ```  
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  
  
    > [!NOTE]  
    >  No exemplo anterior, substitua MostRecentVersionNumber com o número de versão da versão mais recente publicada da sua solução (por exemplo, **1_0_0_4**).  
  
     A mensagem "ExcelWorkbook.vsto assinado com êxito" é exibida.  
  
5.  Copie o arquivo ExcelWorkbook.vsto para o **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_ directory.  
  
##  <a name="SharePoint"></a>Coloque o documento de uma solução em um servidor que está executando o SharePoint (somente no nível do documento personalizações)  
 Você pode publicar sua personalização no nível de documento para os usuários finais usando o SharePoint. Quando os usuários acessam o site do SharePoint e abrem o documento, o tempo de execução instala a solução automaticamente da pasta de rede compartilhada no computador local do usuário. Depois que a solução estiver localmente instalada, a personalização continuará funcionando mesmo que o documento seja copiado em qualquer lugar, como na área de trabalho, por exemplo.  
  
#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Para colocar o documento em um servidor que está executando o SharePoint  
  
1.  Adicione o documento da solução a uma biblioteca de documentos em um site do SharePoint.  
  
2.  Execute as etapas de uma das abordagens a seguir:  
  
    -   Use a Ferramenta de Configuração do Office para adicionar o servidor que está executando o SharePoint à Central de Confiabilidade no Word ou Excel em todos os computadores dos usuários.  
  
         Consulte [políticas de segurança e configurações no Office 2010](http://go.microsoft.com/fwlink/?LinkId=99227).  
  
    -   Assegure-se de que cada usuário execute as etapas a seguir.  
  
        1.  No computador local, abra o Word ou Excel, escolha o **arquivo** guia e, em seguida, escolha o **opções** botão.  
  
        2.  No **Central de confiabilidade** caixa de diálogo caixa, escolha o **locais confiáveis** botão.  
  
        3.  Selecione o **permitir locais confiáveis na minha rede (não recomendado)** caixa de seleção e, em seguida, escolha o **adicionar novo local** botão.  
  
        4.  No **caminho** , digite a URL da biblioteca de documentos do SharePoint que contém o documento que você carregou (por exemplo, *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*).  
  
             Não adicione o nome da página da Web padrão, como. aspx ou AllItems.  
  
        5.  Selecione o **subpastas deste local também são confiáveis** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
             Quando os usuários abrem o documento no site do SharePoint, ele é aberto e a personalização é instalada. Os usuários podem copiar o documento na respectiva área de trabalho. A personalização ainda será executada porque as propriedades no documento apontam para o local de rede do documento.  
  
##  <a name="Custom"></a>Criar um instalador personalizado  
 Você pode criar um instalador personalizado para sua solução do Office, em vez de usar o programa de instalação que é criado quando você publicar a solução. Por exemplo, você pode usar um script de logon para iniciar a instalação ou pode usar um arquivo em lote para instalar a solução sem interação do usuário. Esses cenários funcionarão melhor se os pré-requisitos já estiverem instalados nos computadores dos usuários finais.  
  
 Como parte do processo de instalação personalizado, chame a ferramenta do instalador para soluções do Office (VSTOInstaller.exe), que é instalada no seguinte local por padrão:  
  
 %commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe  
  
 Se a ferramenta não estiver nesse local, você pode usar a chave do Registro HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath ou HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath para localizar o caminho dessa ferramenta.  
  
 É possível usar os parâmetros a seguir com VSTOinstaller.exe.  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|/Install ou /I|Instale a solução. Você deve seguir essa opção com o caminho de um manifesto de implantação. Você pode especificar um caminho no computador local, um compartilhamento de arquivos UNC (convenção) de nomenclatura universal. Você pode especificar um caminho local (*C:\FolderName\PublishFolder*), um caminho relativo (*publicar\\*), ou um local totalmente qualificado (*\\\ServerName\ Nome da pasta* ou http://*ServerName/FolderName*).|  
|/Uninstall ou /U|Desinstale a solução. Você deve seguir essa opção com o caminho de um manifesto de implantação. Você pode especificar que um caminho pode ser no computador local, um compartilhamento de arquivo UNC. Você pode especificar um caminho local (*c:\FolderName\PublishFolder*), um caminho relativo (*publicar\\*), ou um local totalmente qualificado (*\\\ServerName\ Nome da pasta* ou http://*ServerName/FolderName*).|  
|/Silent ou /S|Instale ou desinstale sem solicitar a interação do usuário ou sem exibição de mensagens. Se um prompt confiável for necessário, a personalização não está instalada ou atualizada.|  
|/Ajuda ou /?|Exiba as informações da Ajuda.|  
  
 Quando você executa o VSTOinstaller.exe, os códigos de erro a seguir podem ser exibidos.  
  
|Código do erro|Definição|  
|----------------|----------------|  
|0|A solução foi instalada ou desinstalada com êxito, ou a Ajuda do VSTOInstaller foi exibida.|  
|-100|Uma ou mais opções de linha de comando não são válidas ou foram definidas mais de uma vez. Para obter mais informações, digite "vstoinstaller /?" ou consulte [criando um instalador personalizado para uma solução ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e).|  
|-101|Uma ou mais opções de linha de comando não é válido. Para obter mais informações, insira "vstoinstaller /?".|  
|-200|O URI do manifesto de implantação não é válido. Para obter mais informações, insira "vstoinstaller /?".|  
|-201|A solução não pôde ser instalada porque o manifesto de implantação não é válido. Consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).|  
|-202|A solução não pôde ser instalada porque o Visual Studio Tools para a seção do Office do manifesto do aplicativo não é válido. Consulte [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).|  
|-203|A solução não pôde ser instalada porque ocorreu um erro de download. Verifique o URI ou o local do arquivo de rede do manifesto de implantação e tente novamente.|  
|-300|A solução não pôde ser instalada porque ocorreu uma exceção de segurança. Consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).|  
|-400|A solução não pôde ser instalada.|  
|-401|Não foi possível desinstalar a solução.|  
|-500|A operação foi cancelada porque a solução não pôde ser instalada ou desinstalada, ou o manifesto de implantação não pôde ser baixado.|  
  
##  <a name="Update"></a>Publicar uma atualização  
 Para atualizar uma solução, você publicá-lo novamente usando o **Project Designer** ou **Assistente de publicação**, e, em seguida, copie a solução atualizada para o local de instalação. Ao copiar os arquivos no local da instalação, verifique se substituiu os arquivos anteriores.  
  
 Na próxima vez que a solução verifica uma atualização, ele encontrará e carregar a nova versão automaticamente.  
  
##  <a name="Location"></a>Alterar o local de instalação de uma solução  
 É possível adicionar ou alterar o caminho de instalação depois que uma solução é publicada. Talvez seja conveniente alterar o caminho de instalação por um ou mais dos seguintes motivos:  
  
-   O programa de instalação foi compilado antes que o caminho de instalação fosse conhecido.  
  
-   Os arquivos da solução foram copiados em um local diferente.  
  
-   O servidor que hospeda os arquivos de instalação tem um novo nome ou local.  
  
 Para alterar o caminho de instalação de uma solução, é preciso atualizar o programa de instalação e, em seguida, os usuários devem executá-lo. Para personalização no nível de documento, os usuários também devem atualizar uma propriedade no respectivo documento para que ele aponte para o novo local.  
  
> [!NOTE]  
>  Se você não deseja solicitar aos usuários para atualizar suas propriedades de documento, você pode pedir aos usuários obter o documento atualizado do local de instalação.  
  
#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Para alterar o caminho de instalação no programa de instalação  
  
1.  Abra um **Prompt de comando** janela e, em seguida, alterar diretórios para a pasta de instalação.  
  
2.  Execute o programa de instalação e inclua o parâmetro `/url`, que usa o novo caminho de instalação como uma cadeia de caracteres.  
  
     O exemplo a seguir mostra como alterar o caminho de instalação para um local no site da Fabrikam, mas você pode substituir essa URL pelo caminho que desejar:  
  
    ```  
    setup.exe /url="http://www.fabrikam.com/newlocation"  
    ```  
  
    > [!NOTE]  
    >  Se uma mensagem for exibida informando que a assinatura do executável será invalidada, o certificado que foi usado para assinar a solução não é mais válida e o editor é desconhecido. Consequentemente, os usuários precisarão confirmar que confiam na origem da solução para que possam instalá-la.  
  
    > [!NOTE]  
    >  Para exibir o valor atual da URL, execute `setup.exe /url`.  
  
 Para personalizações no nível do documento, os usuários devem abrir o documento e, em seguida, atualize sua propriedade assemblylocation. As etapas a seguir descrevem como os usuários podem executar essa tarefa.  
  
#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>Para atualizar a propriedade _AssemblyLocation em um documento  
  
1.  Sobre o **arquivo** guia, escolha **informações**, que mostra a ilustração a seguir.  
  
     ![Guia de informações no Excel](../vsto/media/vsto-infotab.png "guia informações no Excel")  
  
2.  No **propriedades** , escolha **propriedades avançadas**, que mostra a ilustração a seguir.  
  
     ![Propriedades avançadas no Excel. ] (../vsto/media/vsto-advanceddocumentproperties.png "Avançado propriedades no Excel.")  
  
3.  No **personalizado** guia o **propriedades** , escolha assemblylocation, como mostra a ilustração a seguir.  
  
     ![A propriedade AssemblyLocation. ] (../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation a propriedade.")  
  
     O **valor** caixa contém o identificador de manifesto de implantação.  
  
4.  Antes do identificador, insira o caminho totalmente qualificado do documento, seguido por uma barra, no formato *caminho*|*identificador* (por exemplo, *File://ServerName/ Nome da pasta/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.  
  
     Para obter mais informações sobre como formatar esse identificador, consulte [visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md).  
  
5.  Escolha o **Okey** botão e, em seguida, salve e feche o documento.  
  
6.  Execute o programa de instalação sem o parâmetro /url para instalar a solução no local especificado.  
  
##  <a name="Roll"></a>Reverter uma solução para uma versão anterior  
 Ao reverter uma solução, você reverte os usuários para uma versão anterior dessa solução.  
  
#### <a name="to-roll-back-a-solution"></a>Para reverter uma solução  
  
1.  Abra o local de instalação da solução.  
  
2.  Na pasta de publicação superior, exclua o manifesto de implantação (o arquivo .vsto).  
  
3.  Localize a subpasta da versão para a qual deseja fazer a reversão.  
  
4.  Copie o manifesto de implantação dessa subpasta na pasta de publicação superior.  
  
     Por exemplo, para reverter uma solução que é chamada **OutlookAddIn1** da versão 1.0.0.1 a versão 1.0.0.0, copie o arquivo **OutlookAddIn1.vsto** do **OutlookAddIn1_1_0_0_0** pasta. Colar o arquivo de nível superior publicar a pasta, substituindo o manifesto de implantação específicos da versão para **OutlookAddIn1_1_0_0_1** que já estava lá.  
  
     A ilustração a seguir mostra a estrutura da pasta de publicação nesse exemplo.  
  
     ![Publicar a estrutura de pasta](../vsto/media/publishfolderstructure.png "publicar estrutura de pastas")  
  
     Da próxima vez que um usuário abrir o aplicativo ou o documento personalizado, a alteração do manifesto de implantação será detectada. A versão anterior da solução do Office é executada do cache do ClickOnce.  
  
> [!NOTE]  
>  Os dados locais são salvos para apenas uma versão anterior de uma solução. Se você reverter duas versões, locais de dados não são mantidas. Para obter mais informações sobre os dados locais, consulte [acesso Local e remoto de dados em aplicativos ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="see-also"></a>Consulte também  
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)   
 [Publicação soluções do Office](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Como: publicar uma solução do Office usando ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Como: instalar uma solução ClickOnce](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)   
 [Como: publicar uma solução de nível de documento em um servidor do SharePoint usando o ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)   
 [Criando um instalador personalizado para uma solução ClickOnce](http://msdn.microsoft.com/en-us/3e5887ed-155f-485d-b8f6-3c02c074085e)  
  
  
