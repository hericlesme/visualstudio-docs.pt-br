---
title: 'Nova geração de projeto: Nos bastidores, parte 1 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ac31f2866c6b69587f70775d5ed1245b1a2bb0a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Nova geração de projeto: Nos bastidores, parte 1
Já pensou sobre como criar seu próprio tipo de projeto? Saber o que realmente acontece quando você cria um novo projeto? Vamos dar uma olhada nos bastidores e ver o que realmente está acontecendo.  
  
 Há várias tarefas que coordena do Visual Studio para você:  
  
-   Ele exibe uma árvore de todos os tipos de projeto disponíveis.  
  
-   Ele exibe uma lista de modelos de aplicativos para cada tipo de projeto e permite que você selecione um.  
  
-   Ele coleta informações sobre o projeto para o aplicativo, como o nome do projeto e o caminho.  
  
-   Ela transmite essas informações para a fábrica de projeto.  
  
-   Ele gera pastas e itens de projeto na solução atual.  
  
## <a name="the-new-project-dialog-box"></a>Caixa de diálogo Novo projeto  
 Tudo começa quando você seleciona um tipo de projeto para um novo projeto. Vamos começar clicando **novo projeto** no **arquivo** menu. O **novo projeto** caixa de diálogo for exibida, aparência semelhante a este:  
  
 ![Caixa de diálogo Novo projeto](../../extensibility/internals/media/newproject.gif "NewProject")  
  
 Vamos dar uma olhada mais próxima. O **tipos de projeto** árvore lista os vários tipos de projeto, você pode criar. Quando você seleciona um tipo de projeto como **Visual C# Windows**, você verá uma lista de modelos de aplicativos para começar. **Modelos instalados do Visual Studio** são instalados pelo Visual Studio e estão disponíveis para qualquer usuário do computador. Novos modelos que você cria ou coleta podem ser adicionados a **Meus modelos** e estão disponíveis somente para você.  
  
 Quando você seleciona um modelo como **aplicativo do Windows**, uma descrição do tipo de aplicativo é exibida na caixa de diálogo; nesse caso, **um projeto para criar um aplicativo com uma interface de usuário do Windows**.  
  
 Na parte inferior do **novo projeto** caixa de diálogo, você verá vários controles que coletam mais informações. Os controles que você vê dependem do tipo de projeto, mas geralmente elas incluem um projeto **nome** caixa de texto, uma **local** caixa de texto e relacionados **procurar** botão e um **Nome da solução** caixa de texto e relacionados **criar diretório para solução** caixa de seleção.  
  
## <a name="populating-the-new-project-dialog-box"></a>Preenchendo a caixa de diálogo Novo projeto  
 Onde does o **novo projeto** caixa de diálogo obter suas informações do? Existem dois mecanismos funcionam aqui, um deles preterido. O **novo projeto** combina de caixa de diálogo e exibe as informações obtidas de ambos os mecanismos.  
  
 O método (preterido) mais antigo usa entradas de registro do sistema e arquivos de .vsdir. Esse mecanismo é executado quando o Visual Studio é aberto. O método mais recente usa arquivos. vstemplate. Esse mecanismo é executado quando o Visual Studio é inicializado, por exemplo, executando  
  
```  
devenv /setup  
```  
  
 ou  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Tipos de projeto  
 A posição e nomes do **tipos de projeto** raiz nós, como **Visual C#** e **outras linguagens**, é determinado por entradas de registro do sistema. A organização de nós filho, como **banco de dados** e **dispositivo inteligente**, reflete a hierarquia de pastas que contêm os arquivos. vstemplate correspondente. Vamos examinar os nós raiz primeiro.  
  
#### <a name="project-type-root-nodes"></a>Nós de raiz do tipo de projeto  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é inicializado, ultrapassa as subchaves da chave do registro de sistema HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs para criar e nomear os nós raiz do **detiposdeprojeto** árvore. Essas informações são armazenadas em cache para uso posterior. Examine o TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 chave. Cada entrada é um GUID VSPackage. O nome da subchave (/ 1) é ignorado, mas sua presença indica que este é um **tipos de projeto** nó raiz. Um nó raiz pode ter várias subchaves que controlam sua aparência no **tipos de projeto** árvore. Vamos examinar algumas delas.  
  
##### <a name="default"></a>(Padrão)  
 Esta é a ID de recurso da cadeia de caracteres localizada que nomeia o nó raiz. O recurso de cadeia de caracteres está localizado na DLL selecionada pelo GUID VSPackage satélite.  
  
 No exemplo, é o GUID VSPackage  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 e a ID de recurso (valor padrão) do nó raiz (/ 1) é 2345 #  
  
 Se você procura o GUID na chave de pacotes próximo e examine a subchave SatelliteDll, você pode encontrar o caminho do assembly que contém o recurso de cadeia de caracteres:  
  
 \<Caminho de instalação do Visual Studio > \VC#\VCSPackages\1033\csprojui.dll  
  
 Para verificar isso, abra o Explorador de arquivos e arraste csprojui.dll no diretório do Visual Studio. A tabela de cadeia de caracteres mostra que o recurso #2345 tem a legenda **Visual C#**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Isso determina a posição do nó raiz de **tipos de projeto** árvore.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Quanto menor o número de prioridade, maior será a posição da árvore.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Se essa subchave estiver presente, a posição do nó raiz é controlada pela caixa de diálogo Configurações do desenvolvedor. Por exemplo,  
  
 REG_SZ DeveloperActivity VC #  
  
 indica que o Visual C# será um nó raiz se o Visual Studio está definido para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] desenvolvimento. Caso contrário, ele será um nó filho do **outras linguagens**.  
  
##### <a name="folder"></a>Pasta  
 Se essa subchave estiver presente, o nó raiz se torna um nó filho da pasta especificada. É exibida uma lista de possíveis pastas sob a chave  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Por exemplo, a entrada de projetos de banco de dados tem uma chave de pasta que corresponda à entrada de outros tipos de projetos em PseudoFolders. No **tipos de projeto** árvore, **projetos de banco de dados** será um nó filho do **outros tipos de projetos**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Nós filho de tipo e vstdir arquivos do projeto  
 A posição de nós filho de **tipos de projeto** árvore segue a hierarquia de pastas nas pastas ProjectTemplates. Para modelos de máquina (**modelos instalados do Visual Studio**), o local típico é \Program Files\Microsoft 14.0\Common7\IDE\ProjectTemplates\ Visual Studio e modelos de usuário (**Meus modelos**), o local típico é Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Hierarquias de pasta desses dois locais são mescladas para criar o **tipos de projeto** árvore.  
  
 Para o Visual Studio com c# configurações do desenvolvedor, o **tipos de projeto** árvore pode ter esta aparência:  
  
 ![Tipos de projeto](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 A pasta ProjectTemplates correspondente tem esta aparência:  
  
 ![Modelos de projeto](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Quando o **novo projeto** abre a caixa de diálogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] atravessa a pasta ProjectTemplates e recria a estrutura no **tipos de projeto** árvore com algumas alterações:  
  
-   O nó raiz de **tipos de projeto** árvore é determinada pelo modelo do aplicativo.  
  
-   O nome do nó pode ser localizado e pode conter caracteres especiais.  
  
-   A ordem de classificação pode ser alterada.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Localizando o nó raiz de um tipo de projeto  
 Quando o Visual Studio atravessa as pastas ProjectTemplates, ele abre todos os arquivos. zip e extrai os arquivos. vstemplate. Um arquivo. vstemplate usa XML para descrever um modelo de aplicativo. Para obter mais informações, consulte [nova geração de projeto: sob o escopo, a segunda parte](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 O \<ProjectType > marca determina o tipo de projeto para o aplicativo. Por exemplo, o arquivo \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip contém um arquivo EmptyProject.vstemplate com esta marca:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 O \<ProjectType > marca e não a subpasta na pasta ProjectTemplates, determina o nó raiz do aplicativo de **tipos de projeto** árvore. No exemplo, os aplicativos do Windows CE seriam exibido sob o **Visual C#** nó raiz, e mesmo se você mover a pasta WindowsCE para a pasta VisualBasic, os aplicativos do Windows CE ainda seriam exibido sob o  **Visual c#** nó raiz.  
  
##### <a name="localizing-the-node-name"></a>Localizando o nome do nó  
 Quando o Visual Studio atravessa as pastas ProjectTemplates, ele examina todos os arquivos vstdir encontrar. Um arquivo vstdir é um arquivo XML que controla a aparência do tipo de projeto no **novo projeto** caixa de diálogo. No arquivo vstdir, use o \<LocalizedName > marca como nome de **tipos de projeto** nó.  
  
 Por exemplo, o arquivo \CSharp\Database\TemplateIndex.vstdir contém esta marca:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Isso determina a ID de DLL e o recurso de satélite da cadeia de caracteres localizada que nomeia o nó raiz, nesse caso, **banco de dados**. O nome localizado pode conter caracteres especiais que não estão disponíveis para nomes de pasta, como **.NET**.  
  
 Se nenhum \<LocalizedName > marca estiver presente, o tipo de projeto é denominado com a pasta propriamente dita, **SmartPhone2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Localizando a ordem de classificação para um tipo de projeto  
 Para determinar a ordem de classificação do tipo de projeto, os arquivos de vstdir usam o \<SortOrder > marca.  
  
 Por exemplo, o arquivo \CSharp\Windows\Windows.vstdir contém esta marca:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 O arquivo \CSharp\Database\TemplateIndex.vstdir tem uma marca com um valor maior:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Quanto menor o número do \<SortOrder > marca, maior será a posição na árvore, para que o **Windows** nó aparece maior do que o **banco de dados** nó no **tipos de projeto**  árvore.  
  
 Se nenhum \<SortOrder > marca é especificada para um tipo de projeto, ele aparece em ordem alfabética quaisquer tipos de projeto que contém a seguir \<SortOrder > especificações.  
  
 Observe que não existem arquivos vstdir em Meus documentos (**Meus modelos**) pastas. Nomes de tipo de projeto de aplicativo do usuário não são localizados e aparecem em ordem alfabética.  
  
#### <a name="a-quick-review"></a>Um exame rápido  
 Vamos modificar o **novo projeto** caixa de diálogo caixa e criar um novo modelo de projeto do usuário.  
  
1.  Adicione uma subpasta MyProjectNode a pasta de 14.0\Common7\IDE\ProjectTemplates\CSharp \Program Visual Studio.  
  
2.  Crie um arquivo MyProject.vstdir na pasta MyProjectNode usando qualquer editor de texto.  
  
3.  Adicione essas linhas ao arquivo vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Salve e feche o arquivo vstdir.  
  
5.  Crie um arquivo MyProject.vstemplate na pasta MyProjectNode usando qualquer editor de texto.  
  
6.  Adicione essas linhas para o arquivo. vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Salve o arquivo the.vstemplate e feche o editor.  
  
8.  Envie o arquivo. vstemplate para uma nova pasta MyProjectNode\MyProject.zip compactada.  
  
9. Na janela de comando do Visual Studio, digite:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Abra o Visual Studio.  
  
1.  Abra o **novo projeto** caixa de diálogo caixa e expanda o **Visual C#** nó do projeto.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** aparece como um nó filho do Visual C# apenas sob o nó do Windows.  
  
## <a name="see-also"></a>Consulte também  
 [Nova geração de projeto: Nos bastidores, parte 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)