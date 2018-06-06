---
title: Proteger as soluções do Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dd86b7c15fa198b37ce15c75b13d2863f56ca3ba
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693364"
---
# <a name="secure-office-solutions"></a>Proteger as soluções do Office
  O modelo de segurança para soluções do Office envolve várias tecnologias: o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], Central de confiabilidade no Microsoft Office e a zona de sites restritos do Internet Explorer. As seções a seguir descrevem como funcionam os recursos de segurança diferentes:  
  
-   [Relação de confiança de concessão para soluções do Office](#GrantingTrustToSolutions)  
  
-   [Conceder confiança a documentos](#GrantingTrustToDocuments)  
  
-   [Conceder confiança ao usar o Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Considerações sobre segurança específicas para soluções do Office](#Security)  
  
-   [Segurança durante o desenvolvimento](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools for Office runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a> Relação de confiança de concessão para soluções do Office  
 Concedendo confiança a soluções do Office significa a modificação da política de segurança de cada usuário final para confiar a solução do Office com base na evidência a seguir:  
  
-   O certificado usado para assinar o manifesto de implantação.  
  
-   A URL do manifesto de implantação.  
  
 Para obter mais informações, consulte [conceder confiança a soluções do Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a> Conceder confiança a documentos  
 Uma personalização no nível do documento exige que o documento seja em um diretório que é designado como um local confiável. Para obter mais informações, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a> Conceder confiança ao usar o Windows Installer  
 Você pode usar o Windows Installer para criar um arquivo MSI para instalar soluções do Office para o diretório de arquivos de programa, o que exige direitos de administrador. Para soluções do Office no diretório de arquivos de programa, o Visual Studio 2010 Tools para Office runtime considera essas soluções do Office sejam confiáveis e não exibe o prompt de confiança do ClickOnce.  
  
##  <a name="Security"></a> Considerações sobre segurança específicas para soluções do Office  
 Os recursos de segurança fornecidos pelo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], e o Microsoft Office pode ajudar a proteger contra uma variedade de possíveis ameaças de segurança em soluções do Office. Para obter mais informações, consulte [considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a> Segurança durante o desenvolvimento  
 Para facilitar o processo de desenvolvimento, o Visual Studio define a política de segurança é necessária para executar e depurar toda vez que você compilar um projeto de sua solução em seu computador. Em alguns cenários, pode ser necessário executar etapas adicionais de segurança para desenvolver o projeto.  
  
### <a name="document-level-solutions"></a>Soluções no nível do documento  
 O caminho totalmente qualificado de um documento deve ser adicionado à lista de locais confiáveis no aplicativo do Microsoft Office se você estiver desenvolvendo os seguintes tipos de projetos:  
  
-   Soluções que estão em um compartilhamento de arquivos de rede, como no nível do documento  *\\\servername\sharename*.  
  
-   Soluções de nível de documento do Word que usam *. doc* ou *docm* arquivos.  
  
 Inclua subpastas quando você adiciona o local do documento para a lista de locais confiáveis, ou especificamente incluem a depuração e criar pastas. Para obter mais informações, consulte o artigo de Ajuda Online do Microsoft Office [criar, remover ou alterar um local confiável para seus arquivos](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Certificados temporários  
 Visual Studio cria um certificado temporário se um certificado de assinatura ainda não existir. Você deve usar este certificado temporário durante o desenvolvimento e adquirir um certificado oficial para implantação.  
  
 O certificado temporário é gerado depois que um projeto do Office for criado pela primeira vez. Na próxima vez que você pressiona **F5**, o projeto é recompilado porque o projeto está marcado como alterada quando o certificado é adicionado.  
  
 Pode haver muitos certificados temporários após algum tempo, portanto você deve limpar os certificados temporários ocasionalmente.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools for Office runtime  
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tem recursos para verificar a identidade do publicador e as permissões que são concedidas a uma personalização. Ele verifica essas permissões por meio de uma sequência de verificações de segurança.  
  
### <a name="security-during-customization-loading"></a>Segurança durante o carregamento de personalização  
 Quando uma personalização no nível do documento é carregada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sempre verifica se o documento está na lista de locais confiáveis. Além disso, o tempo de execução verifica se a solução solicitações FullTrust no manifesto do aplicativo. Ele executa nenhuma verificação de segurança adicional, enquanto a personalização é carregado.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Sequência de verificações de segurança durante a instalação  
 Quando uma solução do Office está instalada ou atualizada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] realiza uma série de verificações de segurança em uma sequência específica para tomar uma decisão de confiança. Uma solução é instalada ou atualizada apenas se o tempo de execução determina se a solução é confiável.  
  
 Você pode iniciar o processo de instalação de uma das quatro maneiras: executando o programa de instalação, abrindo o manifesto de implantação, abrindo o host de aplicativo do Microsoft Office ou executando *VSTOInstaller.exe*.  
  
 A primeira verificação de segurança se aplicam apenas às soluções no nível do documento. O documento de uma solução de nível de documento deve estar em um local confiável. Se o documento está em um compartilhamento de arquivos de rede remota ou tem um *. doc* ou *docm* extensão de nome de arquivo local do documento deve ser adicionado à lista de locais confiáveis. Para obter mais informações, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).  
  
 ![Segurança do VSTO - instalação do Microsoft Office](../vsto/media/host-install.png "segurança do VSTO - instalação do Microsoft Office")  
  
 O próximo conjunto de verificações de segurança são da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e ClickOnce. Para passar essas verificações, soluções do Office devem solicitar permissões FullTrust, sejam assinadas com um certificado que não esteja listado na lista de editor não confiável e estar em um local que não está na zona restrita do Internet Explorer. Se o certificado estiver na lista de fornecedor confiável, a solução é instalada imediatamente. Caso contrário, se ele não desobedecesse a uma das verificações, a solução continuará o conjunto final de verificações.  
  
 ![Segurança do VSTO para instalação de soluções](../vsto/media/installing.png "segurança do VSTO para instalação de soluções")  
  
 Se o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] prompt confiável é permitido e a solução ainda não foi concedida confiança, o tempo de execução permitirá que a decisão de confiança a ser feita pelo usuário final. Se o usuário concede confiança para a solução, uma entrada é adicionada à lista de inclusão de usuário. Todas as soluções na lista de inclusão de usuário têm confiança total e podem ser instaladas e executadas.  
  
 A partir do Visual Studio 2010, a lista de inclusão será ignorada se a solução do Office está instalada usando o Windows Installer (MSI) para o diretório de arquivos de programa. Para obter mais informações, consulte [soluções do Office de relação de confiança usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Segurança do VSTO - usando o programa de instalação para instalar](../vsto/media/setup-vstoinstaller.png "segurança do VSTO - usando o programa de instalação para instalar")  
  
## <a name="see-also"></a>Consulte também  
 [Relação de confiança de concessão para soluções do Office](../vsto/granting-trust-to-office-solutions.md)   
 [Conceder confiança a documentos](../vsto/granting-trust-to-documents.md)   
 [Confiar em soluções do Office usando listas de inclusão](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Como: configurar a segurança da lista de inclusão](../vsto/how-to-configure-inclusion-list-security.md)   
 [Como: assinar soluções do Office](../vsto/how-to-sign-office-solutions.md)   
 [Solucionar problemas de segurança de solução do Office](../vsto/troubleshooting-office-solution-security.md)   
 [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Referência de ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)  
  
  