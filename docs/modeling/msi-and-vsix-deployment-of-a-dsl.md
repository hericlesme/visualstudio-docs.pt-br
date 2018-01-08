---
title: "MSI e implantação do VSIX de uma DSL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: "2"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 0106c63a967e8780c56245d461231f7df47f5b35
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implantação de uma DSL por MSI e VSIX
Você pode instalar uma linguagem específica de domínio em seu próprio computador ou em outros computadores. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]já deve estar instalado no computador de destino.  
  
##  <a name="which"></a>Escolhendo entre VSIX e implantação de MSI  
 Há dois métodos de implantação de uma linguagem específica de domínio:  
  
|Método|Benefícios|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensão)|Muito fácil de implantar: copiar e executar o **.vsix** arquivo do projeto DslPackage.<br /><br /> Para obter mais informações, consulte [instalação e desinstalação de uma DSL usando o VSX](#Installing).|  
|MSI (arquivo)|-Permite que o usuário abra [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] clicando duas vezes em um arquivo DSL.<br />-Associa um ícone com o tipo de arquivo DSL no computador de destino.<br />-Associa um XSD (esquema XML) com o tipo de arquivo DSL. Isso evita avisos quando o arquivo é carregado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Você deve adicionar um projeto de instalação para sua solução para criar um MSI.<br /><br /> Para obter mais informações, consulte [Implantando uma DSL usando um arquivo MSI](#msi).|  
  
##  <a name="Installing"></a>Instalando e desinstalando uma DSL usando o VSX  
 Quando seu DSL é instalado por este método, o usuário pode abrir um arquivo DSL no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], mas não é possível abrir o arquivo do Windows Explorer.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar uma DSL usando o VSX  
  
1.  Em seu computador, localize o **.vsix** arquivo que foi criado pelo seu projeto de pacote de DSL.  
  
    1.  Em **Solution Explorer**, com o botão direito do **DslPackage** do projeto e, em seguida, clique em **Abrir pasta no Windows Explorer**.  
  
    2.  Localize o arquivo **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Copie o **.vsix** arquivo para o computador de destino no qual você deseja instalar o DSL. Isso pode ser seu próprio computador ou outro.  
  
    -   O computador de destino deve ter uma das edições do [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que dá suporte a DSLs em tempo de execução. Para obter mais informações, consulte [suporte para edições do Visual Studio para visualização e modelagem SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   O computador de destino deve ter uma das edições do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] especificado em **DslPackage\source.extensions.manifest**.  
  
3.  No computador de destino, clique duas vezes o **.vsix** arquivo.  
  
     **Instalador de extensão do Visual Studio** abre e instala a extensão.  
  
4.  Iniciar ou reiniciar [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Para testar o DSL, use [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar um novo arquivo com a extensão que você definiu para o DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar uma DSL que tenha sido instalada usando VSX  
  
1.  Sobre o **ferramentas** menu, clique em **Gerenciador de extensões**.  
  
2.  Expanda **extensões instaladas**.  
  
3.  Selecione a extensão na qual o DSL está definida e clique **desinstalação**.  
  
 Raramente, uma extensão com defeito Falha ao carregar e cria um relatório na janela de erro, mas não aparece no Gerenciador de extensões. Nesse caso, você pode remover a extensão excluindo o arquivo de:  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="msi"></a>Implantando uma DSL em um MSI  
 Definindo um arquivo MSI (Windows Installer) para seu DSL, você pode permitir aos usuários abrir arquivos DSL do Windows Explorer. Você também pode associar um ícone e uma descrição curta com sua extensão de nome de arquivo. Além disso, o MSI pode instalar um XSD que pode ser usado para validar os arquivos DSL. Se desejar, você pode adicionar outros componentes no MSI que será instalado ao mesmo tempo.  
  
 Para obter mais informações sobre arquivos MSI e outras opções de implantação, consulte [implantação de aplicativos, serviços e componentes](../deployment/deploying-applications-services-and-components.md).  
  
 Para criar um MSI, você adicionar um projeto de instalação para sua [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solução. O método mais fácil de criar um projeto de instalação é usar o modelo de CreateMsiSetupProject.tt, que pode ser baixado no [site VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implantar uma DSL em um MSI  
  
1.  Definir `InstalledByMsi` no manifesto da extensão. Isso impede que o VSX instalado e desinstalado exceto pelo MSI. Isso é importante se você incluir outros componentes no MSI.  
  
    1.  Abrir DslPackage\source.extension.tt  
  
    2.  Insira a linha a seguir antes de `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Criar ou editar um ícone que representa seu DSL no Windows Explorer. Por exemplo, editar **DslPackage\Resources\File.ico**  
  
3.  Certifique-se de que os seguintes atributos de seu DSL estão corretos:  
  
    -   No Gerenciador de DSL clique no nó raiz e na janela Propriedades, examinar:  
  
        -   Descrição  
  
        -   Versão  
  
    -   Clique o **Editor** nó e na janela Propriedades, clique em **ícone**. Defina o valor para fazer referência a um arquivo de ícone no **DslPackage\Resources**, como **File.ico**  
  
    -   No **criar** menu, abrir **do Configuration Manager**e selecione a configuração que você deseja criar, como **versão** ou **depurar** .  
  
4.  Vá para [home page da visualização e modelagem SDK](http://go.microsoft.com/fwlink/?LinkID=186128)e o **Downloads** guia, baixe **CreateMsiSetupProject.tt**.  
  
5.  Adicionar **CreateMsiSetupProject.tt** ao seu projeto de Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cria um arquivo chamado **CreateMsiSetupProject.vdproj**.  
  
6.  No Windows Explorer, copie Dsl\\*.vdproj para uma nova pasta denominada programa de instalação.  
  
     (Se desejar, você pode excluir CreateMsiSetupProject.tt do seu projeto de Dsl.)  
  
7.  Em **Solution Explorer**, adicionar **instalação\\\*. vdproj** como um projeto existente.  
  
8.  Sobre o **projeto** menu, clique em **dependências do projeto**.  
  
     No **dependências do projeto** caixa de diálogo, selecione o projeto de instalação.  
  
     Marque a caixa ao lado de **DslPackage**.  
  
9. Recompile a solução.  
  
10. No Windows Explorer, localize o arquivo MSI criado em seu projeto de instalação.  
  
     Copie o arquivo MSI para um computador no qual você deseja instalar o DSL. Clique duas vezes no arquivo MSI. O instalador é executado.  
  
11. No computador de destino, crie um novo arquivo que tenha a extensão de arquivo de seu DSL. Verifique se:  
  
    -   Na exibição de lista do Windows Explorer, o arquivo é exibido com o ícone e a descrição que você definiu.  
  
    -   Quando você clicar duas vezes o arquivo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inicia e abre o arquivo DSL em seu editor de DSL.  
  
 Se preferir, você pode criar o projeto de instalação manualmente, em vez de usar o modelo de texto. Para obter uma explicação que inclui esse procedimento consulte o capítulo 5 do [visualização e modelagem SDK laboratório](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar uma DSL instaladas a partir de um MSI  
  
1.  No Windows, abra o **programas e recursos** painel de controle.  
  
2.  Desinstale o DSL.  
  
3.  Reinicie o Visual Studio.