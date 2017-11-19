---
title: "Criação de soluções do Office | Microsoft Docs"
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
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
ms.assetid: c4b79ea8-df70-4a72-b76e-26e337d65727
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3df5fca6d41070b09ceb8b8be9b05212b7caa69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="building-office-solutions"></a>Compilando soluções do Office
  Em geral, compilar e depurar projetos do Office é o mesmo que a criação e depuração de outros tipos de projetos no Visual Studio, como formulários do Windows. Os tópicos nesta seção explicam as diferenças existentes. Para obter informações gerais sobre como criar aplicativos, consulte [compilar e criar no Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Interessado em desenvolvimento de soluções que estendem a experiência do Office em [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com suplementos do VSTO e soluções, e você pode criá-los usando quase qualquer tecnologia, como JavaScript, HTML5, CSS3 e XML de programação da web.  
  
## <a name="project-output-for-office-projects"></a>Saída do projeto para projetos do Office  
 É o local de saída para projetos do Office *projectname*\bin\Release. ou *projectname*\bin\debug. Não é possível criar um diretório de implantação.  
  
### <a name="document-level-projects"></a>Projetos no nível de documento  
 Quando você compila um projeto no nível do documento, os seguintes itens são incluídos na saída do projeto:  
  
-   Uma cópia do documento do projeto.  
  
-   O assembly de projeto e todos os assemblies referenciados que têm suas **Copy Local** propriedade definida como **true**.  
  
-   O manifesto do aplicativo, que tem a extensão de nome de arquivo. manifest. Para obter mais informações, consulte [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   O manifesto de implantação, que tem o .vsto de extensão de nome de arquivo. Para obter mais informações, consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Um arquivo do programa (PDB) de banco de dados.  
  
> [!NOTE]  
>  Se você criar uma solução de nível de documento em um local remoto em vez de no computador local, adicione o caminho totalmente qualificado para a lista de locais confiáveis na Central de confiabilidade do aplicativo. Para obter mais informações, consulte a seção chamada concedendo confiança a documentos [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Projetos no nível de aplicativo  
 Quando você compila um projeto de suplemento do VSTO, os seguintes itens são incluídos na saída do projeto:  
  
-   O assembly de projeto e todos os assemblies referenciados que têm suas **Copy Local** propriedade definida como **true**.  
  
-   O manifesto do aplicativo, que tem a extensão de nome de arquivo. manifest. Para obter mais informações, consulte [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   O manifesto de implantação, que tem o .vsto de extensão de nome de arquivo. Para obter mais informações, consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Um arquivo de programa (PDB) de banco de dados para o assembly de projeto.  
  
 O processo de compilação para projetos de suplemento do VSTO também cria um conjunto de entradas do registro no computador de desenvolvimento que são necessárias para carregar o suplemento do VSTO. Para obter mais informações, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Se você criar um projeto de suplemento do VSTO do Outlook que contém regiões de formulário, o processo de compilação adiciona as seguintes informações adicionais no registro:  
  
-   Uma chave para cada classe de mensagem que está associado uma ou mais regiões de formulário.  
  
-   Uma entrada para cada região de formulário e um valor que representa o nome do suplemento do VSTO do Outlook.  
  
 Outlook precisa dessas informações para carregar as regiões de formulário.  
  
## <a name="referenced-assemblies"></a>Assemblies Referenciados  
 Você pode fazer referência a assemblies (incluindo a projetos de biblioteca de classe) do seu projeto criando soluções do Office. Cada assembly referenciado tem uma propriedade chamada **Copy Local**. **Local da cópia** indica se o assembly é copiado para o diretório de saída. Por padrão, ele é definido como **true**. Cada assembly referenciado tem **Copy Local** definida como **true** é copiado para o diretório de saída.  
  
## <a name="security-during-the-build-process"></a>Segurança durante o processo de compilação  
 O Visual Studio configura automaticamente as configurações de segurança no computador de desenvolvimento para conceder a relação de confiança para a solução durante o processo de compilação. Isso permite que a solução seja executado enquanto você depurá-lo.  
  
 Projetos do Office usam certificados para verificar o Editor. Visual Studio automaticamente cria um certificado temporário para identificar as soluções do Office e configura o computador de desenvolvimento para confiar no certificado temporário.  
  
 Para obter mais informações, consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Projetos de rede  
 Se o local de assembly ou o documento está em um compartilhamento de rede, a atualização de política de segurança local do (nível de usuário) não é suficiente para permitir que a solução seja executada. Um administrador deve conceder confiança total no nível do computador para assemblies e documentos que estão em um compartilhamento de rede antes da solução será executado. Para obter mais informações sobre como definir a política de segurança, consulte [Protegendo soluções do Office](../vsto/securing-office-solutions.md).  
  
 Para projetos de nível de documento, você também deverá adicionar a localização totalmente qualificada do documento para a lista de pastas confiáveis do Office. Para obter mais informações, consulte [concedendo confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
## <a name="changing-the-platform-target"></a>Alterar o destino de plataforma  
 Por padrão, é o destino da plataforma para projetos do Office **qualquer CPU**. Normalmente, você não deve alterar essa configuração. Soluções do Office que são criadas com o **qualquer CPU** destino da plataforma configuração executado em versões de 32 bits e 64 bits do Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Você deve definir o destino da plataforma x64 somente se você estiver criando uma solução que será executado somente nas versões de 64 bits do Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ou [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], e sua solução chama APIs nativas de 64 bits. Para obter mais informações sobre como alterar a configuração de destino da plataforma, consulte [como: configurar projetos para destinar plataformas](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Se você definir o destino de plataforma como x64, a solução não será executado em versões de 32 bits do Windows ou do Office. Plataforma de destino requer a solução seja executada em um processo de 64 bits x64.  
  
## <a name="using-the-clean-command"></a>Usando o comando Limpar  
 Para remover os arquivos de projeto de compilação do computador de desenvolvimento, você pode usar o **limpar** comando o **criar** menu em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. O **limpar** comando exclui todos os arquivos no local de saída da compilação. Para projetos de nível de aplicativo, o **limpar** comando também remove as entradas do registro que são criadas pelo processo de compilação.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Depurando projetos do Office](../vsto/debugging-office-projects.md)|Apresenta problemas envolvidos na depuração de projetos do Office.|  
|[Instruções passo a passo: criando a primeira personalização no nível de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Demonstra como criar uma personalização básica de nível de documento para Excel.|  
|[Como habilitar novamente um suplemento do VSTO que tenha sido desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Descreve como habilitar novamente um Add-in do VSTO que foi desabilitado rígida ou flexível.|  
|[Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)|Fornece links para informações sobre como criar soluções do Office e a função de assemblies em sua solução.|  
  
  