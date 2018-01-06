---
title: "Solucionando problemas de implantação de solução do Office | Microsoft Docs"
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
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
ms.assetid: 2206aeb6-44b3-4786-ba99-9c7dad5cce7c
caps.latest.revision: "74"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a778aa9e257773ca186bba8b99d5e426f8f26aed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-office-solution-deployment"></a>Solucionando problemas da implantação de solução do Office
  Este tópico contém informações sobre como resolver problemas comuns que você pode encontrar ao implantar soluções do Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="troubleshooting-office-solutions-by-using-the-event-viewer"></a>Solucionando problemas de soluções do Office usando o Visualizador de eventos  
 Você pode usar o Visualizador de eventos do Windows para ver mensagens de erro que são capturadas pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando você instalar ou desinstalar soluções do Office. Você pode usar essas mensagens do agente de log de eventos para solucionar problemas de implantação e instalação. Para obter mais informações, consulte [log de eventos para soluções do Office](../vsto/event-logging-for-office-solutions.md).  
  
## <a name="changing-the-assembly-name-causes-conflicts"></a>Alterar o nome de Assembly faz com que os conflitos  
 Se você alterar o **nome do Assembly** valor no **aplicativo** página do **Project Designer** depois que você já implantou uma solução, as ferramentas de publicação irá modificar o Pacote de instalação de um arquivo Setup.exe e dois manifestos de implantação. Se você implantar dois arquivos de manifesto, as condições a seguir podem ocorrer:  
  
-   Se o usuário final instala as versões, o aplicativo carregará os dois suplementos do VSTO.  
  
-   Se o suplemento do VSTO foi instalado antes do nome do assembly foi alterado, o usuário final nunca receberá atualizações.  
  
 Para evitar essas condições, não altere a solução **nome do Assembly** valor depois de implantar a solução.  
  
## <a name="checking-for-updates-takes-a-long-time"></a>Verificando atualizações demora muito  
 Visual Studio 2010 Tools for Office Runtime fornece uma entrada de registro que os administradores podem usar para definir o valor de tempo limite para baixar os manifestos e a solução.  
  
#### <a name="to-set-the-time-out-value"></a>Para definir o valor de tempo limite  
  
1.  No registro, navegue até a seguinte chave:  
  
     HKEY_CURRENT_USER\Software\Microsoft\VSTA  
  
2.  No **AddInTimeout** subchave, defina o valor de tempo limite em milissegundos.  
  
     Se o **AddInTimeout** subchave não existe, criá-lo como uma DWORD.  
  
## <a name="cant-update-or-publish-to-a-network-file-share"></a>Não é possível atualizar ou publicar em um compartilhamento de arquivos de rede  
 Soluções do Office que estão em um compartilhamento de arquivos de rede podem exibir uma mensagem enganosa durante as atualizações, se o arquivo de Setup.exe da solução está bloqueado em um processo, enquanto a atualização está sendo publicada. A mensagem pode dizer o seguinte: "não é possível adicionar 'setup.exe' para a Web. O arquivo 'setup.exe' já existe nesta Web".  
  
 Para ajudar a evitar o bloqueio de arquivos, você pode fazer o compartilhamento somente leitura para os usuários finais. No entanto, se documentos forem no compartilhamento, eles também se tornará somente leitura para os usuários finais.  
  
## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Pré-requisitos para o Microsoft Office não instalados  
 Você pode adicionar o .NET Framework, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]e os Office assemblies de interoperabilidade primários para seu pacote de instalação como pré-requisitos que são implantados com sua solução do Office. Para obter informações sobre como instalar os assemblies de interoperabilidade primários, consulte [Configurando um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) e [como: instalar o Office Assemblies de interoperabilidade primários](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
## <a name="publishing-using-localhost-can-cause-installation-problems"></a>Publicação usando 'Localhost' pode causar problemas de instalação  
 Quando você usa "http://localhost" como o local de publicação ou instalação de soluções no nível do documento, o **Assistente de publicação** não converte a cadeia de caracteres para o nome real do computador. Nesse caso, a solução deve ser instalada no computador de desenvolvimento. Para criar soluções implantadas usam o IIS no computador de desenvolvimento, use o nome totalmente qualificado para todos os locais de HTTP/HTTPS/FTP em vez de localhost.  
  
## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Armazenado em cache de Assemblies é carregado em vez de conjuntos atualizados  
 Fusão, o carregador de assembly do .NET Framework, carrega a cópia armazenada em cache de assemblies quando o caminho de saída do projeto está em um compartilhamento de arquivos de rede, o assembly é assinado com um nome forte e não altera a versão do assembly da personalização. Se você atualizar um assembly que atende a essas condições, a atualização não aparecerá na próxima vez que você executar o projeto porque a cópia armazenada em cache é carregada.  
  
 Você pode configurar o Visual Studio para que a fusão baixar assemblies toda vez que o projeto é executado.  
  
#### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Ao baixar assemblies em vez de carregar cópias armazenadas em cache  
  
1.  Na barra de menus, escolha **projeto**, *ProjectName***propriedades**.  
  
2.  Sobre o **aplicativo** escolha **informações de Assembly**.  
  
3.  Na primeira **versão do Assembly** , digite um asterisco (\*) e, em seguida, escolha o **Okey** botão.  
  
 Depois de alterar a versão do assembly, você pode continuar a assinar o assembly com um nome forte e fusão carregará a versão mais recente da personalização.  
  
## <a name="installation-fails-when-the-uri-has-characters-that-aret-us-ascii"></a>A instalação falha quando o URI tem caracteres que Are't US-ASCII  
 Quando você publica uma solução do Office em um local HTTP/HTTPS/FTP, o caminho não pode ter quaisquer caracteres Unicode que não estejam em US-ASCII. Esses caracteres podem causar um comportamento inconsistente do programa de instalação. Use caracteres US-ASCII para o caminho de instalação.  
  
## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>Prompt para desinstalar manualmente aparece quando você publica e instala uma solução no computador de desenvolvimento  
 Quando você compila uma solução do Office, a versão interna é registrada automaticamente. Se você tiver publicado anteriormente e instalado a mesma solução em seu computador de desenvolvimento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] detecta que o caminho de instalação para a versão publicada e a versão interna são diferentes depois que a solução é criada em seguida, recriado, ou publicado. A mensagem de erro dizendo "a personalização não pode ser instalada porque outra versão instalada no momento e não pode ser atualizada nesse local." As chaves do registro são atualizadas sempre que uma solução é reconstruída. Portanto, você deve desinstalar a versão anterior antes de publicar, depurar ou executar a nova versão.  
  
 Para impedir que a mensagem que aparece, crie outra conta de usuário no computador de desenvolvimento para testar a implantação. Como alternativa, você pode desinstalar a versão da lista de programas instalados no computador antes de Avançar publicar, depurar ou recompile a solução.  
  
## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Exceção não percebida ou método não encontrado erro quando você instala uma solução  
 Quando você instala soluções do Office abrindo o manifesto de implantação (um arquivo .vsto), mensagens de erro de aplicativo, documento ou pasta de trabalho do Office em condições a seguir podem aparecer:  
  
-   Método não encontrado.  
  
-   MissingMethodException.  
  
-   Exceção não tratada.  
  
 Para evitar essas mensagens de erro, instale a solução, executando o programa de instalação.  
  
 Quando você instala a solução sem executar o programa de instalação, o instalador não verificar ou instalar os pré-requisitos. O programa de instalação verifica a versão correta do pré-requisitos e instala-os conforme necessário.  
  
## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Manifesto de chaves do registro para suplementos alteração depois que um projeto do InstallShield Limited Edition for criado  
 A chave de registro de manifesto que faz parte de uma instalação do suplemento do VSTO de programa, às vezes, as alterações do .vsto para. dll.manifest quando você compila um projeto do InstallShield Limited Edition.  
  
 Para contornar esse problema, crie o projeto do InstallShield Limited Edition em uma solução diferente ou usar CompanyName.AddinName como o valor da chave do registro que contém o nome do suplemento do VSTO.  
  
## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>O instalador do ClickOnce para sua solução do Office não instala os Assemblies de interoperabilidade primários  
 Quando você executa o programa de instalação ClickOnce cria sua solução do Office, o instalador para a assemblies de interoperabilidade primários (PIAs) do Office é executado somente se nenhuma PIAs já estão instalados.  
  
 Se o programa de instalação não instala os PIAs corretamente, instalá-los manualmente, executando o arquivo do instalador chamado o2007pia.msi do diretório de instalação.  
  
## <a name="reinstalling-office-solutions-causes-an-argument-out-of-range-exception"></a>Reinstalar as soluções do Office faz com que um argumento exceção fora do intervalo  
 Quando você reinstalar uma solução do Office, um <xref:System.ArgumentOutOfRangeException> exceção poderá aparecer com a seguinte mensagem de erro: argumento especificado estava fora do intervalo de valores válidos.  
  
 Essa situação ocorrerá se o uso de maiusculas e minúsculas para a URL para o local de instalação é diferente. Por exemplo, esse erro apareceria se você instalou uma solução do Office do [http://fabrikam.com/ExcelSolution.vsto](http://fabrikam.com/ExcelSolution.vsto) na primeira vez e, em seguida, usado [http://fabrikam.com/excelsolution.vsto](http://fabrikam.com/excelsolution.vsto) o segunda vez.  
  
 Para impedir que a mensagem que aparece, use maiusculas e minúsculas mesmo quando você instalar soluções do Office.  
  
## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>Não é possível instalar uma solução ClickOnce abrindo o manifesto de implantação da Web  
 Os usuários podem instalar soluções do Office, abrindo o manifesto de implantação da web. No entanto, algumas instalações de serviços de informações da Internet (IIS) uma bloqueia a extensão de nome de arquivo .vsto. Você deve definir o tipo MIME no IIS antes de usá-lo para implantar uma solução do Office.  
  
 Para obter informações sobre como definir o tipo MIME no IIS 6, consulte [configurar tipos de MIME (IIS 6.0)](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/cd72c0dc-c5b8-42e4-96c2-b3c656f99ead.mspx?mfr=true).  
  
 Para obter informações sobre como definir o tipo MIME no IIS 7, consulte [adicionar um tipo de MIME (IIS7).](http://technet.microsoft.com/library/cc725608(WS.10).aspx).  
  
 Definir a extensão **.vsto** e o tipo MIME para **application/x-ms-vsto**.  
  
## <a name="see-also"></a>Consulte também  
 [Solucionando problemas de implantações do ClickOnce](/visualstudio/deployment/troubleshooting-clickonce-deployments)   
 [Implantando uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  