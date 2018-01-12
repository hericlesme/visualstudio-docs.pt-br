---
title: "Compilando e depurando de soluções do SharePoint | Microsoft Docs"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c74c65d091f170b19357058b1d8ae407b2125e77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Compilando e depurando de soluções do SharePoint
  Em geral, compilando e depurando de soluções do SharePoint é o mesmo que a criação e depuração de outros tipos de projetos em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Os tópicos nesta seção explicam as diferenças existentes.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Saída do projeto para soluções do SharePoint  
 Criar soluções do SharePoint cria um arquivo de pacote (. wsp) da solução e assemblies. A tabela a seguir mostra os locais desses arquivos durante uma compilação.  
  
|Criar um item|Pasta de saída|  
|----------------|-------------------|  
|Assembly, banco de dados do programa (PDB) e arquivos. wsp.|*ProjectName*\bin\debug ou *ProjectName*\bin\Release.|  
|Arquivos de item de projeto do SharePoint.|*ProjectName*\pkg\debug ou *ProjectName*\pkg\release|  
|Crie arquivos intermediários.|*ProjectName*\obj\debug ou *ProjectName*\obj\release|  
|Arquivos de pacote intermediários.|*ProjectName*\pkgobj\debug ou *ProjectName*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>Criando soluções do SharePoint  
 Para criar soluções do SharePoint, o computador de desenvolvimento deve ter a versão correta do servidor do SharePoint instalado. Caso contrário, criação de soluções do SharePoint é o mesmo que a criação de outros tipos de projetos em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, consulte [como: criar soluções de SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>Depurando e testando soluções do SharePoint  
 Antes de depurar, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] copia o pacote. wsp para o servidor do SharePoint, ativa o Site e os recursos de escopo de Web e, em alguns casos, o projeto é iniciado. Em outros casos, você terá que abrir o projeto manualmente. Para obter mais informações, consulte [Solucionando problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) e [soluções do SharePoint de depuração](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>Depuração e verificar soluções do SharePoint com recursos do ALM  
 Os recursos do Visual Studio ALM, como testes de unidade e IntelliTrace permitem que você mais precisa identificar problemas em suas soluções do SharePoint. Criação de perfil permite que você localize e identificar áreas de problema de desempenho em suas soluções do SharePoint. Para obter mais informações, consulte [Verificando e depurando código do SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) e [criação de perfil de desempenho de aplicativos do SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Segurança durante o processo de compilação  
 Para compactar ou implantar soluções do SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] deve ter permissão para copiar arquivos para o servidor do SharePoint. Você deve executar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] como um processo elevado e seu usuário da conta deve ser um administrador de coleções de sites no servidor do SharePoint. Além disso, você deve especificar se o projeto é uma solução em modo seguro ou uma solução de farm. Para obter mais informações, consulte [diferenças entre em modo seguro e soluções de Farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Usando o comando Limpar  
 Quando uma solução do SharePoint é instalada em um servidor do SharePoint para depuração, o **limpar** comando não desinstalar a solução. Em vez disso, você deve desativar os recursos por meio da configuração do SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Pesquisa de conexões do SharePoint usando o Gerenciador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Empacotando e implantando recursos do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  