---
title: 'Como: criar um. Arquivo VSCT | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6456b0b866f08956862fa197719354bedf0ecf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-vsct-file"></a>Como: criar um. Arquivo VSCT  
  
Há várias maneiras de criar um arquivo de configuração (. VSCT) da tabela de comando com base em XML Visual Studio.  
  
-   Você pode criar um novo VSPackage no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] modelo de pacote.  
  
-   Você pode usar o compilador de configuração de tabela do comando baseado em XML, Vsct.exe, para gerar um arquivo de um arquivo .ctc existente.  
  
-   Você pode usar Vsct.exe para gerar um arquivo. VSCT de um arquivo .cto existente.  
  
-   Você pode criar manualmente um novo arquivo. VSCT.  
  
 Este tópico explica como criar manualmente um novo arquivo. VSCT.  
  
### <a name="to-manually-create-a-new-vsct-file"></a>Para criar manualmente um novo arquivo. VSCT  
  
1.  Inicie o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
2.  Sobre o **arquivo** , aponte para **novo**e, em seguida, clique em **arquivo**.  
  
3.  No **modelos** painel, clique em **arquivo XML** e, em seguida, clique em **abrir**.  
  
4.  Sobre o **exibição** menu, clique em **janela propriedades** para exibir as propriedades do arquivo XML.  
  
5.  No **propriedades** janela, clique no botão Procurar (...) na propriedade de esquemas.  
  
6.  Na lista de esquemas XSD, selecione o esquema de vsct.xsd. Se não estiver na lista, clique em **adicionar** e, em seguida, localize o arquivo em uma unidade local. Clique em **Okey** quando tiver terminado.  
  
7.  No arquivo XML, digite `<CommandTable` e, em seguida, pressione TAB. Feche a marca digitando `>`.  
  
     Isso cria um arquivo. VSCT básica.  
  
8.  Preencha os elementos do arquivo XML que você deseja adicionar, de acordo com o [VSCT esquema](../../extensibility/vsct-xml-schema-reference.md). Para obter mais informações, consulte [criação. VSCT arquivos](../../extensibility/internals/authoring-dot-vsct-files.md)  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Como: criar um. Arquivo VSCT de uma já existente. Arquivo ctc  
  
Você pode criar um arquivo. VSCT baseado em XML de um arquivo de origem do comando tabela .ctc existente. Ao fazer isso, você pode tirar proveito do novo com base em XML [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formato de compilador de tabela (VSCT) de comando.  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para criar um arquivo. VSCT de um arquivo .ctc  
  
1.  Obtenha uma cópia da linguagem Perl.  
  
2.  Obtenha uma cópia do script Perl ConvertCTCToVSCT.pl, geralmente localizada no  *\<caminho de instalação do SDK do Visual Studio >* \VisualStudioIntegration\Tools\bin pasta.  
  
3.  Obtenha uma cópia do arquivo de origem .ctc que você deseja converter.  
  
4.  Coloque os arquivos no mesmo diretório.  
  
5.  No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] janela de Prompt de comando, navegue até o diretório.  
  
6.  Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     onde PkgCmd.ctc é o nome do arquivo .ctc e PkgCmd.vsct é o nome do arquivo. VSCT que você deseja criar.  
  
     Isso cria um novo arquivo. VSCT XML comando tabela fonte. Você pode compilar o arquivo usando Vsct.exe, o compilador do VSCT, como você faria com qualquer outro arquivo. VSCT.  
  
    > [!NOTE]
    >  Você pode melhorar a legibilidade do arquivo. VSCT reformatar os comentários XML.  
  
<a name="how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file"></a>

## <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Como: criar um. Arquivo VSCT de uma já existente. Arquivo CTO  
  
Você pode criar um arquivo. VSCT baseado em XML de um arquivo binário .cto existente. Isso permite que você aproveite o novo formato de compilador de tabela do comando. Esse processo funciona mesmo quando o arquivo .cto foi compilado de um arquivo de .ctc. Você pode editar e compilar o arquivo. VSCT em outro arquivo .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para criar um arquivo. VSCT de um arquivo .cto  
  
1.  Obter cópias do arquivo .cto e seu arquivo .ctsym correspondente.  
  
2.  Coloque os arquivos no mesmo diretório que o compilador vsct.exe.  
  
3.  No Visual Studio Prompt de comando, vá para o diretório que contém os arquivos .cto e .ctsym.  
  
4.  Tipo **vsct.exe** *ctofilename * .cto** * vsctfilename ***. VSCT -S***symfilename ***.ctsym**.  
  
     `ctofilename` é o nome do arquivo .cto, `vsctfilename` é o nome do arquivo vsct para criar, e `symfilename` é o nome do arquivo .ctsym.  
  
     Esse processo cria um novo arquivo. VSCT XML comando tabela compilador. Você pode editar e compilar o arquivo com vsct.exe, o compilador do vsct, como você faria com qualquer outro arquivo. VSCT.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Simplesmente adicionando um arquivo. VSCT para um projeto não causa compilá-lo. Você deve incorporá-lo no processo de compilação.  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>Para adicionar um arquivo. VSCT a compilação de projeto  
  
1.  Abra o arquivo de projeto no editor. Se o projeto é carregado, você deve descarregá-la primeiro.  
  
2.  Adicionar uma [elemento ItemGroup](../../msbuild/itemgroup-element-msbuild.md) que contém um elemento VSCTCompile, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     O elemento ResourceName deve sempre ser definido como `Menus.ctmenu`.  
  
3.  Se seu projeto contém um arquivo. resx, adicione um elemento EmbeddedResource que contém um elemento MergeWithCTO, conforme mostrado no exemplo a seguir.  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     Essa marcação deve ficar dentro do elemento ItemGroup que contém recursos inseridos.  
  
4.  Abra o arquivo de pacote, geralmente chamado *ProjectName*Package.cs ou *ProjectName*Package.vb no editor.  
  
5.  Adicione um atributo ProvideMenuResource à classe de pacote, conforme mostrado no exemplo a seguir.  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     O primeiro valor do parâmetro deve corresponder ao valor do atributo ResourceName definido no arquivo de projeto.  
  
## <a name="see-also"></a>Consulte também  
 [Data de criação. VSCT arquivos](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)