---
title: Guia de Plug-ins de controle de origem de teste | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0fdab6cb0b259fe169a9ebd43c92158a5ce20d4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guia de teste para Plug-ins de controle de origem
Esta seção fornece orientação para testar o controle de origem plug-in com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É fornecida uma visão geral abrangente de áreas mais comuns de teste, bem como algumas das áreas mais complexas que podem ser problemáticas. Esta visão geral não deve ser uma lista completa de casos de teste.  
  
> [!NOTE]
>  Algumas correções de bug e aprimoramentos para a versão mais recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pode descobrir problemas com existente fonte plug-ins de controle que anteriormente não foram encontrados durante o uso de versões anteriores do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. É altamente recomendável que você teste seu controle de origem existente plug-in para as áreas enumeradas nesta seção, mesmo que nenhuma alteração foi feita para o plug-in desde a versão anterior do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Preparação comuns  
 Uma máquina com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e plug-in de controle de origem destino instalado, é necessário. Uma segunda máquina configurada de maneira semelhante pode ser usada para algumas das abrir dos testes de controle de origem.  
  
## <a name="definition-of-terms"></a>Definição de termos  
 Com a finalidade deste guia de teste, use as seguintes definições de termos:  
  
 Projeto de cliente  
 Tipo de disponível em qualquer projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que oferece suporte à integração de controle de origem (por exemplo, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ou [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Projeto Web  
 Há quatro tipos de projetos Web: sistema de arquivos, IIS Local, Sites remotos e FTP.  
  
-   Projetos do sistema de arquivos são criados em um caminho local, mas eles não exigem o Internet Information Services (IIS) para ser instalado como elas são acessadas internamente por meio de um caminho UNC e podem ser colocadas sob controle de origem de dentro do IDE, semelhante a projetos de cliente.  
  
-   Projetos do IIS locais funcionam com o IIS está instalado no mesmo computador e é acessado com uma URL que aponta para o computador local.  
  
-   Projetos de Sites remotos também são criados em um serviços do IIS, mas eles são colocados sob controle de origem na máquina do servidor IIS e não de dentro do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
-   Projetos FTP são acessados por meio de um servidor FTP remoto, mas eles não podem ser colocados sob controle de origem.  
  
 Inscrição  
 Outro termo para a solução ou projeto sob controle de origem.  
  
 Armazenamento de versão  
 O banco de dados que está sendo acessado por meio da API de plug-in de controle de origem.  
  
## <a name="test-areas-covered-in-this-section"></a>Áreas de teste abordadas nesta seção  
  
-   [Área de teste 1: Adicionar / Abrir do controle de origem](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Adicionar solução ao controle de origem  
  
    -   Caso 1b: Abra a solução do controle de origem  
  
    -   Caso 1C: adicionar a solução do controle de origem  
  
-   [Área de teste 2: Obter do controle do código-fonte](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Área de teste 3: Check-Out / desfazer check-out](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Check-Out / desfazer check-out  
  
    -   Caso 3a: Check-Out  
  
    -   Caso 3b: desconectado check-out  
  
    -   Caso 3C: Editar consulta/salvar (QEQS)  
  
    -   Caso 3d: Check-out silencioso  
  
    -   Caso 3e: desfazer check-out  
  
-   [Área de teste 4: Fazer check-in](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: modificado itens  
  
    -   Caso 4b: adicionando arquivos  
  
    -   Caso 4c: adicionando a projetos  
  
-   [Área de teste 5: Alterar controle do código-fonte](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: associar  
  
    -   Caso 5b: desvincular  
  
    -   Caso 5c: Reassociar  
  
-   [Área de teste 6: Excluir](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Área de teste 7: Compartilhar](../../extensibility/internals/test-area-7-share.md)  
  
-   [Área de teste 8: Alternância de plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: alterações automáticas  
  
    -   Caso 8b: alteração de solução  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)