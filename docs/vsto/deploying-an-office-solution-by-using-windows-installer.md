---
title: Implantar uma solução do Office usando o Windows Installer
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6f9936111360d6734e1280e84f34416efbedb05c
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-an-office-solution-by-using-windows-installer"></a>Implantar uma solução do Office usando o Windows Installer
Saiba como criar um Windows Installer para sua solução do Office usando [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
Usando o Visual Studio para criar um instalador do Windows, você pode implantar uma solução do Office que requer acesso administrativo no computador do usuário final. Por exemplo, você pode usar esse arquivo para instalar uma solução apenas uma vez para todos os usuários de um computador. Você também pode implantar uma solução do Office usando o ClickOnce, mas essa solução deve ser instalada separadamente para cada usuário do computador.  
  
  
## <a name="in-this-topic"></a>Neste tópico  
  
- [Baixe amostras de suplemento do VSTO](#Download)  
  
- [Obter o InstallShield Limited Edition](#Obtain)  
  
- [Decidir como conceder confiança para a solução](#ApplySecurity)  
  
- [Criar um projeto de instalação](#Create)  
  
- [Adicionar a saída do projeto](#Add)  
  
- [Adicionar os manifestos de aplicativo e implantação](#AddD)  
  
- [Configurar os componentes dependentes como pré-requisitos](#Configure)  
  
- [Especifique onde você deseja implantar a solução no computador do usuário](#Location)  
  
- [Configurar um suplemento do VSTO](#ConfigureRegisitry)  
  
- [Configurar uma personalização no nível do documento](#ConfigureDocument)  
  
- [Compilar o projeto de instalação](#Build)  
  
Para obter mais informações sobre como implantar uma solução do Office usando o ClickOnce, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
Para obter informações sobre como criar um arquivo do Windows Installer usando [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], consulte [implantar um Visual Studio 2010 Tools para soluções do Office usando o Windows Installer](http://go.microsoft.com/fwlink/?LinkId=201807).  
  
  
## <a name="Download"></a>Baixar exemplos  
Este tópico refere-se aos seguintes exemplos que você pode baixar.  
  
  
  
|Amostra<br /><br />|Descrição<br /><br />|  
|----------|---------------|  
|[ExcelAddIn](http://go.microsoft.com/fwlink/?LinkID=275492)<br /><br />|Um Add-in do VSTO do Excel que você pode instalar em um computador que executa uma versão de 32 bits ou 64 bits do Office.<br /><br />|  
|[ExcelWorkbook](http://go.microsoft.com/fwlink/?LinkID=275493)<br /><br />|Uma personalização do Excel no nível de documento que você pode instalar em um computador que execute uma versão do Office de 32 bits ou de 64 bits.<br /><br />|  
  
## <a name="ApplySecurity"></a>Decidir como conceder confiança para a solução  
Para que uma solução possa ser executada nos computadores dos usuários, você deve conceder confiança de qualquer uma das seguintes formas ou os usuários devem responder a uma solicitação de confiança quando instalam a solução.  
  
  
- Assine os manifestos usando um certificado que identifica um editor conhecido e confiável. Para obter mais informações, consulte [a solução de confiança ao assinar os manifestos de aplicativo e implantação](../vsto/granting-trust-to-office-solutions.md#Signing).  
  
- Instale a solução para o diretório de arquivos de programas no computador do usuário.  
  
> [!NOTE]  
> Para personalizações em nível de documento, a localização do documento também deve ser confiável. Para obter mais informações, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
  
## <a name="Obtain"></a>Obter o InstallShield Limited Edition  
Você pode criar um arquivo do Windows Installer usando o ISLE (InstallShield Limited Edition), que é gratuito se você instalou o Visual Studio. O ISLE substitui a funcionalidade dos modelos de projeto para instalação e implantação que as versões anteriores do Visual Studio ofereceram.  
  
  
### <a name="to-get-installshield-limited-edition"></a>Para obter o InstallShield Limited Edition  
  
1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**.  
  
   A caixa de diálogo **Novo Projeto** é aberta.  
  
2. No painel de modelos, expanda **outros tipos de projetos**e, em seguida, escolha o **instalação e implantação** modelo.  
  
3. Na lista de tipos de projeto para **instalação e implantação**, escolha **habilitar o InstallShield Limited Edition**e, em seguida, escolha o **Okey** botão.  
  
   Você verá uma página que fornece informações sobre como obter o InstallShield Limited Edition.  
  
4. Nessa página, escolha o **ir para o site de download da** link.  
  
5. Na página de download para o InstallShield Limited Edition, insira as informações necessárias para os campos apropriados e, em seguida, escolha o **baixar agora** link.  
  
   Depois de baixar, instalar e ativar o produto, o **projeto do InstallShield Limited Edition** modelo aparece no Visual Studio.  
  
  
## <a name="Create"></a>Criar um projeto de instalação  
  
1. No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], abra o projeto do Office que você deseja implantar.  
  
   Os exemplos de suplemento do VSTO que estão associados este tópico contém um projeto chamado **ExcelAddIn**. Os exemplos de personalização de nível de documento contém um projeto chamado **ExcelWorkbook**. Este tópico se referirá ao projeto do Office em sua solução usando um desses dois nomes.  
  
2. Na barra de menus, escolha **arquivo** > **adicionar** > **novo projeto**.  
  
   A caixa de diálogo **Adicionar Novo Projeto** é aberta.  
  
3. No painel de modelos, expanda **outros tipos de projetos**e, em seguida, escolha o **instalação e implantação** modelo.  
  
4. Na lista de tipos de projeto para **instalação e implantação**, escolha **projeto do InstallShield Limited Edition**, nomeie o projeto e, em seguida, escolha o **Okey** botão.  
  
   O projeto de instalação do InstallShield que você acabou de criar aparecerá na sua solução.  
  
   Os exemplos deste tópico contém um projeto de instalação que é nomeado **OfficeAddInSetup**. Este tópico se referirá ao projeto em sua solução usando o mesmo nome.  
  
  
## <a name="Add"></a>Adicionar a saída do projeto  
Configurar o **OfficeAddInSetup** projeto para incluir a saída de seu projeto do Office. Para projetos de suplemento do VSTO, a saída do projeto é somente o assembly de solução. Para os projetos de personalização no nível de documento, a saída do projeto inclui não apenas o assembly da solução, mas também do próprio documento.  
  
  
### <a name="to-add-the-project-output"></a>Para adicionar a saída do projeto  
  
1. Em **Solution Explorer**, expanda o **OfficeAddInSetup** nó do projeto e, em seguida, escolha o **Assistente de projeto** arquivo, que mostra a ilustração a seguir.  
  
   ![Assistente de arquivo no Gerenciador de soluções do projeto](../vsto/media/installshield-projectassistant.png "Assistente de arquivo no Gerenciador de soluções do projeto")  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
3. Na parte inferior da **Assistente de projeto** página, escolha o **arquivos de aplicativo** botão, que mostra a ilustração a seguir.  
  
   ![O botão de arquivos de aplicativo. ] (../vsto/media/installshield-applicationfiles.png "Botão os arquivos do aplicativo.")  
  
4. No **arquivos de aplicativo** página, escolha o **adicionar saídas do projeto** botão.  
  
5. No **seletor de saída do Visual Studio** caixa de diálogo, selecione o **saída primária** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
  
## <a name="AddD"></a>Adicionar os manifestos de aplicativo e implantação  
  
###  
1. No **arquivos de aplicativo** página, escolha o **adicionar arquivos** botão.  
  
2. No **abrir** caixa de diálogo, navegue até o diretório de saída do **ExcelAddIn** projeto.  
  
   Geralmente, o diretório de saída é o **bin\release** subpasta da pasta raiz do projeto, dependendo da configuração de compilação que você escolher.  
  
3. No diretório de saída, escolha o **ExcelAddIn.vsto** e **ExcelAddIn.dll.manifest** arquivos e, em seguida, escolha o **abrir** botão.  
  
   O **arquivos de aplicativo** página agora contém o arquivo de saída do projeto, o manifesto de implantação e o manifesto do aplicativo, como mostra a ilustração a seguir.  
  
   ![Os arquivos de saída do seu projeto de instalação. ] (../vsto/media/installshield-outputfiles.png "Os arquivos de saída do seu projeto de instalação.")  
  
  
## <a name="Configure"></a>Configurar os componentes dependentes como pré-requisitos  
Em seu aplicativo de instalação, além dos seguintes componentes, inclua todos os outros componentes que são necessários para que a sua solução seja executada.  
  
  
- A versão do .NET Framework que a sua solução do Office terá como alvo.  
  
- Microsoft Visual Studio 2010 Tools for Office Runtime.  
  
  
### <a name="add-the-net-framework-4-or-the-net-framework-45-as-a-prerequisite"></a>Adicionar o .NET Framework 4 ou o .NET Framework 4.5 como um pré-requisito  
  
1. Em **Solution Explorer**, expanda o **OfficeAddInSetup** nó do projeto, expanda o **especificar dados de aplicativo** nó e, em seguida, escolha o  **Redistribuíveis** arquivo, que mostra a ilustração a seguir.  
  
   ![Os arquivos redistribuíveis no Gerenciador de soluções](../vsto/media/installshield-redistributablesfile.png "redistribuíveis o arquivo no Gerenciador de soluções")  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
   O **redistribuíveis** página será aberta.  
  
3. Na lista de componentes redistribuíveis, marque a caixa de seleção adequada para a versão do .NET Framework de destino da sua solução.  
  
   Por exemplo, se seus destinos de solução de [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], selecione o **Microsoft .NET Framework 4.5 Full** caixa de seleção. Uma caixa de diálogo aparecerá perguntando se você deseja instalar o componente redistribuído, que o InstallShield exige antes de adicionar o componente como um pré-requisito. Se essa caixa de diálogo não aparecer, o componente já existe em seu computador.  
  
4. Se essa caixa de diálogo for exibida, escolha o **não** botão.  
  
  
### <a name="AddToolsForOffice"></a>Adicione o Visual Studio 2010 Tools for Office Runtime  
O **redistribuíveis** página contém um item chamado **Microsoft VSTO 2010 Runtime**, mas ele se refere a uma versão mais antiga do tempo de execução. Portanto, você pode criar manualmente um arquivo de configuração que se refere a versão mais recente. Em seguida, você deve colocar esse arquivo no mesmo diretório que os arquivos de configuração para todos os outros itens que aparecem no **redistribuíveis** página.  
  
  
#### <a name="to-add-the-visual-studio-2010-tools-for-office-runtime-as-a-prerequisite"></a>Para adicionar o Visual Studio 2010 Tools para Office runtime como um pré-requisito  
  
1. Abra o Bloco de Notas e cole o seguinte XML em um arquivo de texto.  
  
  
   ```xml  
   <?xml version="1.0" encoding="UTF-8"?>  
   <SetupPrereq>  
   <conditions>  
       <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   <condition Type="32" Comparison="2" Path="HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4R" FileName="Version" ReturnValue="10.0.50903" Bits="2"></condition>  
   </conditions>  
   <files>  
       <file LocalFile="<ISProductFolder>\SetupPrerequisites\VSTOR\vstor_redist.exe" URL="http://download.microsoft.com/download/C/0/0/C001737F-822B-48C2-8F6A-CDE13B4B9E9C/vstor_redist.exe" CheckSum="88b8aa9e8c90818f98c80ac4dd998b88" FileSize=" 0,40117912"></file>  
   </files>  
   <execute file="vstor_redist.exe" returncodetoreboot="1641,3010" requiresmsiengine="1">  
   </execute>  
   <properties Id="{15965040-56BB-49B8-A88F-3525C48D9BA8}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
     
   </SetupPrereq>  
   ```  
  
2. Gere uma GUID no Visual Studio. Sobre o **ferramentas** menu, escolha **criar GUID**.  
  
3. No **gerador GUID** de programa, escolha o **formato do registro** botão de opção, escolha o **cópia** botão e, em seguida, escolha o **sair** botão.  
  
4. No bloco de notas, substitua o texto **seu GUID aqui** colando o GUID em seu lugar.  
  
   O **&lt;propriedades&gt;** elemento do arquivo semelhante ao seguinte.  
  
  
   ```xml  
   <properties Id="{87989B73-21DC-4403-8FD1-0C68A41A6D8C}" Description="This prerequisite installs the most recent version of the Microsoft Visual Studio 2010 Tools for Office Runtime." >  
   </properties>  
   ```  
  
5. Na barra de menus no bloco de notas, escolha **arquivo** > **salvar**.  
  
6. No **Salvar como** caixa de diálogo, navegue até seu **Desktop** pasta.  
  
7. No **Salvar como tipo** , escolha **todos os arquivos (&#42;.&#42;)** .  
  
8. No **nome de arquivo** , digite **Visual Studio 2010 Tools para Office Runtime.prq**e, em seguida, escolha o **salvar** botão.  
  
   > [!NOTE]  
   >    Certifique-se de que você adicione **.prq** no final do nome do arquivo para identificar este arquivo como um arquivo de pré-requisito.  
  
9. Feche o Bloco de Notas.  
  
10. De seu **Desktop** pasta, copie o *Visual Studio 2010 Tools para Office Runtime.prq* arquivo a um dos seguintes diretórios no seu computador.  
  
   Para sistemas operacionais de 32 bits: *%ProgramFiles%\InstallShield\2013LE\SetupPrerequisites\\*  
  
   Para sistemas operacionais de 64 bits: *% ProgramFiles (x86) %\2013LE\SetupPrerequisites\\*  
  
11. No **Redistributable** página do projeto do InstallShield, escolha o **atualização** botão para atualizar a lista de componentes redistribuíveis, como mostra a ilustração a seguir.  
  
   ![O botão Atualizar. ] (../vsto/media/installshield-refreshbutton.png "No botão de atualização.")  
  
12. Na lista de componentes redistribuíveis, selecione o **Visual Studio 2010 Tools for Office Runtime** caixa de seleção.  
  
   Uma caixa de diálogo aparecerá perguntando se você deseja instalar o componente redistribuível. Se essa caixa de diálogo não aparecer, você pode passar para o [especifique onde você deseja implantar a solução no computador do usuário](#Location) seção deste tópico.  
  
13. Se essa caixa de diálogo for exibida, escolha o **não** botão.  
  
  
## <a name="Location"></a>Especifique onde instalar a solução no computador do usuário  
  
1. Em **Solution Explorer**, expanda o **OfficeAddInSetup** nó, expanda o **organizar sua instalação** nó e, em seguida, escolha o **asinformaçõesgerais** arquivo.  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
3. Na lista de propriedades, escolha o **procurar** lado a **INSTALLDIR** propriedade.  
  
4. No **definir INSTALLDIR** caixa de diálogo caixa, escolha uma pasta no computador do usuário em que você deseja instalar a solução.  
  
   > [!NOTE]  
   >    Você também pode criar subdiretórios no **definir INSTALLDIR** caixa de diálogo, abra o menu de atalho para qualquer pasta na lista.  
  
  
## <a name="ConfigureRegisitry"></a>Configurar um suplemento do VSTO  
Você pode especificar se deseja que seu suplemento do VSTO para ser instalado para todos os usuários do computador (por computador) ou apenas para o usuário que está executando a instalação (por usuário).  
  
Se você quiser oferecer suporte a instalações por computador, crie dois instaladores separados. Você pode dividir os instaladores com base na versão do Office (32 bits e 64 bits) ou na versão do Windows (32 bits e 64 bits) que o usuário está executando.  
  
As instalações por usuário exigem apenas um instalador independente do Office ou versão do Windows.  
  
> [!NOTE]  
> Esta seção se aplica somente se você estiver implantando um suplemento do VSTO. Se você estiver implantando uma personalização no nível do documento, você pode ir imediatamente para o [configurar uma personalização no nível do documento](#ConfigureDocument) seção.  
  
  
### <a name="to-specify-whether-you-want-to-support-per-user-or-per-computer-installations"></a>Para especificar se você quer oferecer suporte a instalações por usuário ou por computador  
  
1. Em **Solution Explorer**, expanda o **OfficeAddInSetup** nó do projeto, expanda o **organizar sua instalação** nó e, em seguida, escolha o **informações gerais**  arquivo.  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
   Você verá as propriedades do projeto de instalação.  
  
3. Na lista para o **AllUSERS** propriedade, especifique se deseja que essa solução para ser instalado para todos os usuários do computador ou somente para o usuário que instala a solução.  
  
   Para instalar o suplemento do VSTO para o usuário atual, escolha **ALLUSERS = "" (instalação por usuário)**. Para instalar o suplemento do VSTO para todos os usuários do computador, escolha **ALLUSERS = 1 (instalação por máquina)**  
  
   No próximo procedimento, você criará as chaves de registro para habilitar o aplicativo do Office descobrir e carregar o suplemento do VSTO. Consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
  
### <a name="to-create-registry-keys"></a>Para criar chaves de registro  
  
1. Em **Solution Explorer**, escolha o **Assistente de projeto** nó.  
  
   Na barra de menus, escolha **exibição** > **abrir**.  
  
2. Na parte inferior da **Assistente de projeto** página, escolha o **registro de aplicativos** botão, que mostra a ilustração a seguir.  
  
   ![O botão de registro de aplicativo. ] (../vsto/media/installshield-applicationregistry.gif "Botão de registro de aplicativo.")  
  
   O **registro de aplicativos** página será exibida.  
  
3. Em **você deseja configurar os dados de registro que seu aplicativo será instalado?**, escolha o **Sim** botão de opção.  
  
4. No **exibição de registro do computador de destino** lista, adicione a hierarquia de chave que permite que o tipo de instalador que você deseja criar.  
  
   O caminho que você configura nesta seção depende da criação de um instalador por usuário ou um instalador por computador.  
  
   **Instalador por usuário**  
  
   **HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**  
  
   **Instaladores por computador com base na versão do Office**  
  
  
  
|Versão do Office<br /><br />|Configuração do caminho do InstallShield<br /><br />|  
|------------------|------------------------------------|  
|32 bits<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
|64 bits<br /><br />|**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
   **Instaladores por computador com base na versão do Windows**  
  
  
  
|Versão do Windows<br /><br />|Configuração do caminho do InstallShield<br /><br />|  
|-------------------|------------------------------------|  
|32 bits<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
|64 bits<br /><br />|**HKEY_LOCAL_MACHINE\Software(32-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />**HKEY_LOCAL_MACHINE\Software(64-bit) \Microsoft\Office\Excel\Addins\SampleCompany.ExcelAddIn**<br /><br />|  
   > [!NOTE]  
   >    Um instalador para Windows de 64 bits requer dois caminhos de registro, pois é possível que os usuários executem as versões de 32 bits e 64 bits do Office em um computador que executa o Windows de 64 bits.  
  
   > [!NOTE]  
   >    Como uma prática recomendada, inicie o nome de seu suplemento do VSTO com o nome da sua empresa. Essa convenção aumenta a chance de que a chave seja exclusiva e diminui a chance de conflito com um suplemento do VSTO de outro fornecedor. Os suplementos que têm o mesmo nome podem, por exemplo, substituir as chaves de registro um do outro. Essa abordagem não pode garantir que a chave será única, mas pode reduzir possíveis conflitos de nome.  
  
5. Depois de criar a hierarquia de chaves, abra o menu de atalho para o **SampleCompany.ExcelAddIn** chave, escolha **novo**e, em seguida, escolha **valor de cadeia de caracteres**.  
  
   O novo valor de cadeia de caracteres aparece no **dados de registro do computador de destino** lista. O nome do valor da cadeia de caracteres é realçado e você pode renomeá-lo.  
  
6. Renomeie o valor como **descrição**.  
  
7. Repita esse processo para criar os seguintes valores.  
  
  
  
|Tipo do Valor<br /><br />|Nome<br /><br />|  
|--------------|--------|  
|Valor da cadeia de caracteres<br /><br />|**Nome amigável**<br /><br />|  
|Valor DWORD<br /><br />|**LoadBehavior**<br /><br />|  
|Valor da cadeia de caracteres<br /><br />|**Manifesto**<br /><br />|  
  
8. Abra o menu de atalho para o **descrição** valor e, em seguida, escolha **modificar**.  
  
   O **editar dados** caixa de diálogo é exibida.  
  
9. No **dados do valor** texto, digite **suplemento do Excel demonstração**e, em seguida, escolha o **Okey** botão.  
  
   Essa descrição é exibida quando o usuário abre o aplicativo do Office, abre o **opções** caixa de diálogo e, em seguida, no **Add-Ins** painel, escolher o suplemento do VSTO.  
  
10. Abra o menu de atalho para o **FriendlyName** valor e, em seguida, escolha **modificar**.  
  
   O **editar dados** caixa de diálogo é exibida.  
  
11. No **dados do valor** texto, digite **suplemento do Excel demonstração**e, em seguida, escolha o **Okey** botão.  
  
   Essa cadeia de caracteres aparece no **suplementos COM** caixa de diálogo no aplicativo do Office. Por padrão, o valor da cadeia de caracteres é a ID do suplemento do VSTO  
  
12. Abra o menu de atalho para o **LoadBehavior** valor e, em seguida, escolha **modificar**.  
  
   O **editar dados** caixa de diálogo é exibida.  
  
13. No **dados do valor** texto, digite **3**e, em seguida, escolha o **Okey** botão.  
  
   Um valor de 3 carrega o suplemento do VSTO quando o aplicativo for iniciado. Para obter mais informações sobre valores LoadBehavior, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
14. Abra o menu de atalho para o **manifesto** valor e, em seguida, escolha **modificar**.  
  
   O **editar dados** caixa de diálogo é exibida.  
  
15. No **dados do valor** texto, digite **file:///[INSTALLDIR]ExcelAddIn.vsto|vstolocal**e, em seguida, escolha o **Okey** botão.  
  
   O Visual Studio 2010 Tools for Office Runtime usa esse caminho para localizar o manifesto de implantação. O **[INSTALLDIR]** parte do caminho é uma macro que mapeia para o **INSTALLDIR** propriedade o **informações gerais** página de propriedades de seu projeto de instalação do InstallShield. Essa propriedade especifica o local no computador de destino para instalar o suplemento do VSTO. O **| vstolocal** sufixo garante que sua solução seja carregada da pasta de instalação, não o cache do ClickOnce.  
  
> [!IMPORTANT]  
> Se você criar uma região de formulário personalizado em um suplemento do VSTO para Outlook, você deve criar mais entradas de registro para registrar a região com o Outlook. Para obter mais informações, consulte [regiões de formulário de entradas do registro para Outlook](../vsto/registry-entries-for-vsto-add-ins.md#OutlookEntries).  
  
  
## <a name="ConfigureDocument"></a>Configurar uma personalização no nível do documento  
Esta seção se aplica somente se você estiver implantando uma personalização no nível do documento. Se você estiver implantando um suplemento do VSTO, você pode ir imediatamente para o [compilar o projeto de instalação](#Build) seção.  
  
Personalizações no nível do documento não usam as chaves do registro. Em vez disso, as propriedades personalizadas do documento contêm o local do manifesto de implantação.  
  
Para modificar as propriedades personalizadas, crie um programa que remova a personalização no nível de documento do documento, modifique as propriedades adequadas e reatribua personalização ao documento. Crie uma ação personalizada que execute o programa, adicione essa ação ao seu projeto de instalação.  
  
### <a name="to-create-a-program-that-modifies-document-properties"></a>Para criar um programa que modifica as propriedades do documento  
  
1. Na barra de menus, escolha **arquivo** > **adicionar** > **novo projeto**.  
  
   A caixa de diálogo **Adicionar Novo Projeto** é exibida.  
  
2. No painel modelos, sob o nó para o idioma que você deseja usar, escolha o **Windows** pasta.  
  
3. Na lista de tipos de projeto para **Windows**, escolha o **aplicativo de Console** modelo.  
  
4. Nomeie o projeto **SetExcelDocumentProperties**e, em seguida, escolha o **Okey** botão.  
  
5. Em **Solution Explorer**, escolha o **Mostrar todos os arquivos** botão, abra o menu de atalho para o **SetExcelDocumentProperties** nó do projeto e escolha **Adicionar referência**.  
  
6. No **Gerenciador de referências** caixa de diálogo caixa, escolha o **extensões** guia e, em seguida, selecione a caixa de seleção ao lado de assemblies a seguir e, em seguida, escolha o **Okey** botão.  
  
  
   - Microsoft.VisualStudio.Tools.Applications.Runtime  
  
   - Microsoft.VisualStudio.Tools.Applications.ServerDocument  
  
7. Em **Solution Explorer**, escolha o **Program.cs** arquivo (para aplicativos em c#) ou o **Module1. vb** arquivo (para aplicativos do Visual Basic).  
  
8. Na barra de menus, escolha **exibição** > **abrir**.  
  
9. Substitua o conteúdo do arquivo inteiro pelo seguinte código.  
  
[!code-vb[Trin_CustomAction#1](../vsto/codesnippet/VisualBasic/setexceldocumentproperties/module1.vb#1)]
[!code-csharp[Trin_CustomAction#1](../vsto/codesnippet/CSharp/setexceldocumentproperties/program.cs#1)]  
  
10. Compile o projeto.  
  
  
### <a name="to-add-a-custom-action-that-runs-your-program"></a>Para adicionar uma ação personalizada que executa o seu programa  
  
1. Em **Solution Explorer**, expanda o **OfficeAddInSetup** nó do projeto e, em seguida, escolha o **Assistente de projeto** arquivo, que mostra a ilustração a seguir.  
  
   ![Assistente de arquivo no Gerenciador de soluções do projeto](../vsto/media/installshield-projectassistant.png "Assistente de arquivo no Gerenciador de soluções do projeto")  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
3. Na parte inferior da **Assistente de projeto** página, escolha o **arquivos de aplicativo** botão, que mostra a ilustração a seguir.  
  
   ![O botão de arquivos de aplicativo. ] (../vsto/media/installshield-applicationfiles.png "Botão os arquivos do aplicativo.")  
  
4. No **arquivos de aplicativo** página, escolha o **adicionar saídas do projeto** botão.  
  
   O **seletor de saída do Visual Studio** caixa de diálogo é exibida.  
  
5. Sob o **SetExcelDocumentProperties** nó, selecione o **saída primária** caixa de seleção e, em seguida, escolha o **Okey** botão.  
  
6. Em **Solution Explorer**, no **OfficeAddInSetup** nó, expanda o **ações e definir os requisitos de configuração** nó e, em seguida, escolha o **personalizado Ações** pasta.  
  
7. Na barra de menus, escolha **exibição** > **abrir**.  
  
   A lista de eventos aparece em um painel na lateral da tela.  
  
   > [!NOTE]  
   >    Apenas alguns eventos que aparecem nessa lista estão disponíveis no InstallShield Limited Edition. Neste procedimento, você executará o programa usando o **caixa de diálogo após a instalação completa sucesso** eventos.  
  
8. Na lista de eventos, em **ações durante a instalação personalizada**, abra o menu de atalho para o **caixa de diálogo após a instalação completa sucesso** evento e, em seguida, escolha **EXE novo**.  
  
   Uma ação personalizada chamada **NewCustomAction1** aparece sob o **caixa de diálogo após a instalação completa sucesso** evento. Um conjunto de propriedades para a ação personalizada é exibido em um painel ao lado dos eventos.  
  
   > [!IMPORTANT]  
   >    Dois **caixa de diálogo após a instalação completa sucesso** eventos aparecem na lista de eventos. Certifique-se de que você escolha a instância do **caixa de diálogo após a instalação completa sucesso** eventos que aparece sob o **ações durante a instalação personalizada** nó.  
  
9. Na lista para o **local de origem** propriedade, escolha **instalados com o produto**.  
  
10. Escolha o **procurar** lado a **nome de arquivo** propriedade.  
  
11. No **procurar um arquivo de destino** caixa de diálogo, navegue até o **SetExcelDocumentProperties.Primary.output** de arquivo e, em seguida, escolha o **abrir** botão.  
  
   O local do arquivo depende da pasta que você especificou para o **INSTALLDIR** propriedade do projeto de instalação. Por exemplo, se você definir essa propriedade para uma pasta denominada **[PersonalFolder] DemoWorkbookApp**, você pode encontrar o **SetExcelDocumentProperties.Primary.output** arquivo navegando até **[ ProgramFilesFolder] \DemoWorkbookApp**.  
  
   Nas próximas etapas, você obtém a ID da solução do documento e passar essa ID como um parâmetro para o aplicativo de console. Você também vai passar o local do documento, o manifesto de implantação e o assembly do documento.  
  
12. Abra o menu de atalho para o **ExcelWorkbook** do projeto e, em seguida, escolha **Abrir pasta no Windows Explorer** ou **Abrir pasta no Explorador de arquivos** dependendo de seu sistema sistema.  
  
   A pasta que contém a solução é aberta.  
  
13. Abra o arquivo de projeto da sua solução no Bloco de Notas. Para projetos do Visual Basic, o nome do arquivo é *ExcelWorkbook.vbproj*. Para projetos c#, o nome do arquivo é *ExcelWorkbook.csproj*.  
  
14. No arquivo de projeto, procure o **&lt;ID da solução&gt;** elemento, copie seu valor para a área de transferência e, em seguida, feche o bloco de notas.  
  
   Passe esse valor para o aplicativo de console como um parâmetro.  
  
15. Na página de propriedades de **NewCustomAction1**, defina o **linha de comando** propriedade para a seguinte linha de texto.  
  
  
   ```cmd
   /assemblyLocation="[INSTALLDIR]ExcelWorkbook.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbook.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbook.xlsx" /solutionID="Your Solution ID"  
   ```  
  
16. Substituir **sua ID da solução** com a ID de solução que você copiou para a área de transferência.  
  
   > [!IMPORTANT]  
   >    Teste o seu instalador para verificar se o aplicativo de console que essa ação personalizada executa pode acessar os documentos no diretório [INSTALLDIR]. Alguns diretórios no computador do usuário podem exigir acesso administrativo (por exemplo, o diretório de arquivos de programa). Se você estiver implantando sua solução para um diretório que requer acesso administrativo, você deve abrir o **propriedades** caixa de diálogo do *setup.exe* de arquivo, escolha o **compatibilidade** guia e, em seguida, selecione o **executar este programa como administrador** caixa de seleção antes de distribuir o instalador. Se você não quiser que os usuários executem o programa de instalação com permissões administrativas, defina a propriedade de [INSTALLDIR] para um diretório no qual o usuário provavelmente tem acesso, como o **documentos** directory. Para obter mais informações, consulte o [especifique onde você deseja instalar a solução no computador do usuário](#Location) seção deste tópico.  
  
  
## <a name="Build"></a>Compilar o projeto de instalação  
  
1. Em **Solution Explorer**, expanda o **preparar para versão** nó e, em seguida, escolha o **versões** arquivo.  
  
2. Na barra de menus, escolha **exibição** > **abrir**.  
  
   O **cria** explorer é aberto em um painel lateral para que você pode escolher o tipo de versão que você deseja criar.  
  
3. No **cria** explorer, escolha o **SingleImage** pasta.  
  
4. No painel de Avançar para o **cria** explorer, escolha o **Setup.exe** guia.  
  
5. No **Setup.exe** página de propriedades, do **InstallShield pré-requisitos local** , escolha **baixar da Web**.  
  
6. Na barra de menus, escolha **Build** > **Gerenciador de Configurações**.  
  
7. No **configuração de solução ativa** , escolha **SingleImage**.  
  
8. No **contextos do projeto** tabela, no **configuração** coluna o **OfficeAddInSetup** projeto, escolha **SingleImage**e, em seguida, Escolha o **fechar** botão.  
  
9. Na barra de menus, escolha **criar** > **OfficeAddInSetup criar**.  
  
   Após a compilação, você pode localizar o *setup.exe* arquivo o **OfficeAddInSetup** projeto no seguinte local: *OfficeAddInSetupProjectRoot * \OfficeAddInSetup\ Express\SingleImage\DiskImages\DISK1\**  
  
  
## <a name="see-also"></a>Consulte também  
[Pré-requisitos de solução do Office para implantação](http://msdn.microsoft.com/en-us/library/9f672809-43a3-40a1-9057-397ce3b5126e)  
[Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)  
[Entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md)  
[Visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md)  
[Relação de confiança de concessão para soluções do Office](../vsto/granting-trust-to-office-solutions.md)  
[Conceder confiança a documentos](../vsto/granting-trust-to-documents.md)  
[Implantar um Visual Studio 2010 Tools para soluções do Office usando o Windows Installer](http://go.microsoft.com/fwlink/?LinkId=201807)  
  