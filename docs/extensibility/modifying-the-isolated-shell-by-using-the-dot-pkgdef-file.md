---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: Modificando o Shell isolado usando o. Arquivo Pkgdef | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a0e654e603abe0e4f1546e5b06c2b3644af2067e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modificando o Shell isolado usando o. Arquivo Pkgdef
O arquivo .pkgdef oferece suporte a configurações que você pode usar para personalizar um aplicativo de shell isolado. Especifica valores que são criados quando um aplicativo é instalado em um computador e que são referenciados pelo shell do Visual Studio quando ele inicia o aplicativo. As configurações são organizadas no arquivo com base nas chaves do registro aplicável.  
  
> [!WARNING]
>  Observe que .pkgdef arquivos que não sejam declarados no arquivo .vsixmanifest do VSPackage não sejam verificados quando o Visual Studio inicia.  
  
 O arquivo .pkgdef contém seções que são identificadas por uma chave, ou `[$RootKey$]` ou `[$RootKey$\` *subchave*`]`, onde $RootKey$ é a chave de raiz para o aplicativo.  
  
 Cada seção contém pares nome/valor que têm o seguinte formato: `"` *ValueName*`"=`*valor*.  
  
 Os valores são uma cadeia de caracteres que está entre aspas ou um inteiro de 32 bits que é representado como uma dword. Valores têm as seguintes restrições:  
  
-   Todos os valores dword estão em formato hexadecimal, por exemplo `dword:00000001`.  
  
     Para valores booleanos, 1 representa verdadeiro e 0 representa false.  
  
-   Todas as cadeias de caracteres do GUID estão no formato de registro, por exemplo, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Todos os identificadores de recurso localizável têm o formato "@*resourceID*" ou "#*resourceID*", onde *resourceID* é o identificador de recurso no pacote de interface do usuário do aplicativo, Por exemplo, `"@102"`. O pacote de interface do usuário do aplicativo é o pacote que é referenciado na configuração de AppLocalizationPackage.  
  
 Por exemplo,  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Você pode adicionar comentários para o arquivo .pkgdef. Um comentário de linha única tem duas barras como os dois primeiros caracteres.  
  
 Para obter uma lista de cadeias de caracteres de substituição, consulte [substituição de cadeias de caracteres usadas no. Pkgdef e. Arquivos de Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 As seções a seguir descrevem os valores de registro específicos que afetam o comportamento do shell do Visual Studio em modo isolado. Você também pode definir valores de registro adicionais para o aplicativo nesse arquivo.  
  
> [!NOTE]
>  Se uma configuração não é fornecida no arquivo .pkgdef, nenhuma entrada correspondente é feita no registro.  
  
## <a name="settings"></a>Configurações  
 A tabela a seguir descreve os valores definidos em [$RootKey$].  
  
|Nome|Tipo|Valor|  
|----------|----------|-----------|  
|AddinsAllowed|DWORD|True se os suplementos podem ser carregados; Caso contrário, false.<br /><br /> O valor padrão é true.|  
|AllowsDroppedFilesOnMainWindow|DWORD|True se a janela principal pode aceitar arquivos ignorados; Caso contrário, false. Arquivos removidos na janela principal são abertos usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> método. Isso é equivalente a abrir um documento usando o **abrir** comando o **arquivo** menu no aplicativo.<br /><br /> O valor padrão é true.|  
|AppIcon|cadeia de caracteres|O caminho completo do ícone de programa. Esse ícone é exibido na barra de título à esquerda do nome do aplicativo.<br /><br /> O valor padrão é "$ $RootFolder\\*solutionName*. ico", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|AppLocalizationPackage|cadeia de caracteres|O GUID do VSPackage que contém o assembly satélite de interface do usuário para o aplicativo. Neste VSPackage inclui uma versão compilada do arquivo. VSCT e pode incluir outras cadeias de caracteres localizadas. Conjuntos de recursos e grupos de comando de menu podem ser habilitados ou desabilitados, alterando as configurações no arquivo. VSCT de projeto de interface do usuário.<br /><br /> O valor padrão é "{*vsUiPackageGuid*}", onde *vsUiPackageGuid* é o GUID atribuído ao pacote de interface do usuário do aplicativo.|  
|AppName|cadeia de caracteres|O nome do aplicativo. O nome aparece na barra de título da janela do aplicativo.<br /><br /> O valor padrão é o nome do arquivo de solução do aplicativo.|  
|CommandLineLogo|cadeia de caracteres|O texto da faixa quando o aplicativo é executado em uma janela de console. Essa configuração afeta somente os aplicativos que dão suporte a operações de criação de linha de comando.<br /><br /> O valor padrão é "*companyName**solutionName* versão 1.0.", onde *companyName* é o nome da empresa fornecido quando o Windows foi instalado e *solutionName* é o nome do arquivo de solução do aplicativo.|  
|DefaultDebugEngine|cadeia de caracteres|O GUID do padrão o mecanismo usado para o aplicativo de depuração.<br /><br /> Observação: Um GUID vazio (todos os zeros à esquerda) indica que o aplicativo não especificar um mecanismo de depuração padrão. Isso permite que o depurador selecionar o mecanismo de depuração a ser usado.<br /><br /> O valor padrão é "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|cadeia de caracteres|A URL da página inicial padrão para a janela do navegador da Web interna.<br /><br /> Se o **Home page** opção está disponível no aplicativo, em seguida, essa configuração também afeta o estado padrão da opção. Para obter mais informações, consulte [caixa de diálogo do navegador da Web, ambiente, opções](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> O valor padrão é a URL da empresa fornecida quando o Windows foi instalado.|  
|DefaultProjectsLocation|cadeia de caracteres|O caminho completo da pasta de projetos de padrão. Por exemplo,<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Se o **local de projetos do Visual Studio** opção está disponível no aplicativo, em seguida, essa configuração também afeta o estado padrão da opção. Para obter mais informações, consulte [NIB: caixa de diálogo Geral, Projetos e Soluções, Opções](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> O valor padrão é "$ $MyDocuments\\*solutionName*", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|DefaultSearchPage|cadeia de caracteres|A URL de página de pesquisa padrão para a janela do navegador da Web interna.<br /><br /> Se o **página Pesquisa** opção está disponível no aplicativo, em seguida, essa configuração também afeta o estado padrão da opção. Para obter mais informações, consulte [caixa de diálogo do navegador da Web, ambiente, opções](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> O valor padrão é "http://search.live.com".|  
|DefaultUserFilesFolderRoot|cadeia de caracteres|O nome da pasta de usuário, o usuário atual em relação a pasta Meus documentos do.<br /><br /> O valor padrão é o nome do arquivo de solução do aplicativo.|  
|DisableOutputWindow|DWORD|Indica se o shell isolado deve tratar a janela de saída como desabilitado.<br /><br /> Se esse valor é definido como true, o Visual Studio não exibe a saída de Gerenciador de build de solução no **saída** janela e oculta o **janela de saída mostrar início da compilação** caixa de seleção a  **Projetos e soluções** categoria no **opções** caixa de diálogo.<br /><br /> O valor padrão é false.|  
|HideMiscellaneousFilesByDefault|DWORD|True para ocultar o **arquivos diversos** pasta por padrão em **Solution Explorer**; caso contrário, false.<br /><br /> Se o **Mostrar arquivos diversos no Gerenciador de soluções** opção está disponível no aplicativo, em seguida, essa configuração também afeta o estado padrão da opção. Para obter mais informações, consulte [documentos, ambiente, caixa de diálogo de opções](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> O valor padrão é false.|  
|HideSolutionConcept|DWORD|True para criar projetos de todos os projetos como autônomos e ocultar a solução e comandos relacionados a uma solução para projetos autônomos por padrão. Caso contrário, false.<br /><br /> Se o **sempre mostrar solução** opção está disponível no aplicativo, em seguida, essa configuração também afeta o estado padrão da opção. Para obter mais informações, consulte [NIB: caixa de diálogo Geral, Projetos e Soluções, Opções](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> O valor padrão é false.|  
|NewProjDlgInstalledTemplatesHdr|cadeia de caracteres|O nome para o cabeçalho de modelos do Visual Studio instalou no **modelos** lista o **novo projeto** caixa de diálogo. Isso é uma cadeia de caracteres ou um identificador de recurso localizável carregado a partir do pacote de interface do usuário do aplicativo.<br /><br /> O valor padrão é "*solutionName* modelos instalados", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|NewProjDlgSlnTreeNodeTitle|cadeia de caracteres|O nome para o **soluções do Visual Studio** nó o **tipos de projeto** árvore no **novo projeto** caixa de diálogo. Isso é uma cadeia de caracteres ou um identificador de recurso localizável carregado a partir do pacote de interface do usuário do aplicativo.<br /><br /> O valor padrão é "*solutionName* modelos instalados", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|SolutionFileCreatorIdentifier|cadeia de caracteres|O identificador do aplicativo, que aparece como a segunda linha nos arquivos de solução que são gerados pelo aplicativo. Essa linha indica que o aplicativo que criou o arquivo. Por convenção, esse valor inclui o nome do aplicativo e o número de versão do aplicativo. Por exemplo,<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> O programa VSLauncher.exe, que é o programa padrão para abrir um arquivo de solução do Visual Studio, usa essa segunda linha para determinar a versão do Visual Studio para abrir o arquivo de solução. O aplicativo requer seu próprio iniciador para lidar com seus arquivos de solução associada. O iniciador também pode usar essa segunda linha no arquivo de solução para determinar em qual versão do aplicativo para abrir a solução.<br /><br /> Observação: O programa Visual Studio VSLauncher.exe não processa arquivos. sln que foram criados por um aplicativo de shell isolado.<br /><br /> O valor padrão é "*solutionName* arquivo de solução, versão de formato 10,00", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|SolutionFileExt|cadeia de caracteres|A extensão de nome de arquivo de solução para o aplicativo. É recomendável que você escolher uma extensão de nome de arquivo exclusivo (not.sln).<br /><br /> O valor padrão é "*solutionName*_sln", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|SplashScreenBitmap|cadeia de caracteres|O caminho completo do arquivo de bitmap para a tela inicial do aplicativo.<br /><br /> O valor padrão é "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|cadeia de caracteres|O identificador de classe (CLSID) do objeto de automação para o aplicativo.<br /><br /> O objeto de automação do aplicativo é o objeto de nível superior para o aplicativo no modelo de automação do Visual Studio shell e implementa o <xref:EnvDTE._DTE?displayProperty=fullName> interface.<br /><br /> Se o objeto de automação do aplicativo está registrado corretamente sob a chave de registro HKEY_CLASSES_ROOT\CLSID, você pode usar o [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) função para criar uma instância do aplicativo.<br /><br /> Shell do Visual Studio usa esse CLSID para registrar o objeto de automação do aplicativo na tabela de objeto em execução (CORROMPIDOS) usando o sinalizador ACTIVEOBJECT_WEAK. Isso permite que você use o [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)função para recuperar um ponteiro para uma instância em execução do aplicativo. Além disso, se você definir um ProgID para o objeto de automação do aplicativo, em seguida, o shell do Visual Studio também registra cada instância do aplicativo no CORROMPIDOS usando um item de moniker do formulário *progID*:*processID* , onde *progID* é o ProgID do objeto de automação do aplicativo, e *processID* é o identificador de processo para essa instância do aplicativo. Por exemplo, se você criar um moniker da seguinte maneira:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> onde `instanceString` é o *progID*:*processID* cadeia de caracteres. Você poderia usar `instanceMoniker` com a função GetObject ROT para obter a instância.<br /><br /> Se a configuração ThisVersionDTECLSID for omitida, o aplicativo não é exposto por meio do modelo COM (Component Object). Nesse caso, uma instância do aplicativo não pode ser criada chamando o [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) de função e não pode ser registrado no CORROMPIDOS.<br /><br /> Cada versão de um VSPackage deve ter um CLSID diferente.<br /><br /> O valor padrão é o GUID que o Visual Studio gerado para o objeto de automação do aplicativo.|  
|ThisVersionSolutionCLSID|cadeia de caracteres|O CLSID do objeto de solução para o aplicativo.<br /><br /> O objeto de automação da solução contém informações sobre a solução aberta atual em uma instância do aplicativo e implementa o <xref:EnvDTE._Solution?displayProperty=fullName> interface.<br /><br /> Se o objeto de automação da solução está registrado corretamente sob a chave de registro HKEY_CLASSES_ROOT\CLSID, você pode usar o [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) função para criar um objeto de solução para o aplicativo.<br /><br /> Shell do Visual Studio usa esse CLSID para registrar o objeto de automação da solução no CORROMPIDOS usando o sinalizador ACTIVEOBJECT_WEAK.<br /><br /> Se essa configuração for omitida, em seguida, a classe da solução não está registrada com o modelo COM (Component Object) e um objeto de solução não pode ser criado chamando o [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) de função e não pode ser registrado no CORROMPIDOS.<br /><br /> O valor padrão é um GUID que o Visual Studio gerado para o objeto de solução do aplicativo.|  
|UserFilesSubFolderName|cadeia de caracteres|O nome da subpasta na pasta de documentos do usuário no qual o aplicativo cria subpastas e arquivos do usuário.<br /><br /> O valor padrão é o nome do arquivo de solução do aplicativo.|  
|UserOptsFileExt|cadeia de caracteres|A extensão para arquivos de opções de usuário de solução para o aplicativo.<br /><br /> O valor padrão é o nome do arquivo de solução do aplicativo.|  
  
## <a name="binding-path-settings"></a>Configurações de caminho de associação  
 O [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] chave contém a lista de diretórios que o shell verifica para assemblies. Esses diretórios são adicionados à lista de diretórios que o shell de testes para assemblies privados para o aplicativo.  
  
 Por padrão, nenhuma entrada de caminho de associação é adicionada ao arquivo .pkgdef. No entanto, os seguintes subdiretórios do diretório de instalação do Visual Studio são adicionados automaticamente à lista de caminho de associação de aplicativo no registro.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Para adicionar um diretório para o caminho de associação, adicione uma entrada no formato "*directoryName*"="", onde *directoryName* é um caminho absoluto. Por exemplo,  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Configurações de perfil  
 A tabela a seguir descreve os valores que são definidos para cada pacote associado em [$RootKey$ \Profile].  
  
|Nome|Tipo|Valor|  
|----------|----------|-----------|  
|AutoSaveFile|cadeia de caracteres|O diretório no qual o aplicativo armazena arquivos de salvamento automático.<br /><br /> O valor padrão é "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Configurações de DLL satélite de pacote  
 A tabela a seguir descreve os valores que estão definidos em [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] para a DLL de cada pacote associado, satélite onde *vsPackageGuid* é o GUID do pacote associado.  
  
|Nome|Tipo|Valor|  
|----------|----------|-----------|  
|Nomedadll|cadeia de caracteres|O nome do arquivo da DLL.<br /><br /> O valor padrão é "*solutionName*ui.dll", onde *solutionName* é o nome do arquivo de solução do aplicativo.|  
|Caminho|cadeia de caracteres|O diretório que contém a DLL satélite.<br /><br /> O valor padrão é "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Configurações de Item de Menu do pacote  
 Chave do Registro [$RootKey$ \Menus] define os arquivos de recursos de interface do usuário para o aplicativo.  
  
 Valores de item de menu têm o formato "{*vsUiPackageGuid*}"=" *resourceId*, *versionNumber*", onde *vsUiPackageGuid* é o GUID do o pacote de interface do usuário do aplicativo, *resourceId* é o identificador de recurso do recurso CTMENU que contém os elementos de interface do usuário, e *versionNumber* é um número de versão virtual para o CTMENU recurso. Para obter mais informações, consulte [Registrando manipuladores de comandos de Assembly de interoperabilidade](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Por padrão, uma entrada de item de menu é criada no arquivo .pkgdef para o pacote de interface do usuário do aplicativo.  
  
 Para cada pacote que fornece os itens de menu que é distribuída como parte do aplicativo, adicione uma entrada de item de menu para o pacote.  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md)   
 [. Arquivos de Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)