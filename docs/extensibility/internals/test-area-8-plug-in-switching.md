---
title: 'Teste área 8: Alternância de plug-in | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 534bd9338181c5b682779b62a9c118a5ccaf8cda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148854"
---
# <a name="test-area-8-plug-in-switching"></a>Teste área 8: Alternância de plug-in
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) tem a interface do usuário (UI) para alterar o plug-in de controle de origem atual. Essa área de teste fornece casos de teste para o processo de separação o plug-in para usar a solução para controle de origem.  
  
## <a name="command-menu-access"></a>Acesso de Menu de comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminhos de menu do ambiente de desenvolvimento integrado são usados nos casos de teste.  
  
-   Controle de origem atual plug-in: **ferramentas** -> **opções** -> **controle de origem** -> **seleção de plug-in** .  
  
-   Alterar origem ligação de controle: **arquivo** -> **controle de origem** -> **alterar controle de origem**...  
  
## <a name="common-expected-behavior"></a>Comportamento esperado comuns  
 É possível alterar o plug-in de uma solução de controle de origem sem sair do Visual Studio ou o recarregamento da solução. Além disso, o plug-in atual de controle do código-fonte altera automaticamente à usada por uma solução quando essa solução é carregada.  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para a área de teste de comutação plug-in.  
  
### <a name="case-8a-automatic-change"></a>Caso 8a: alterações automáticas  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
 Quando um usuário carrega uma solução que está sob controle do código-fonte, a solução é carregada automaticamente e o plug-in de controle de origem apropriado está selecionada como atual.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Alteração de plug-in de controle de origem automática|1.  Selecione plug-in em teste como atual (**ferramentas** -> **opções** -> **controle de origem** -> **plug-in Seleção**.)<br />2.  Crie um novo projeto.<br />3.  Adicione a solução ao controle de origem.<br />4.  Selecione outro plug-in (por exemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />5.  Aceite solicitação de solução de descarregamento.<br />6.  Reabra a solução do disco.|Solução é aberta.<br /><br /> Plug-in em teste é o plug-in atual de controle do código-fonte.|  
  
### <a name="case-8b-solution-based-change"></a>Caso 8b: alteração de solução  
  
#### <a name="expected-behavior"></a>Comportamento esperado  
 A solução pode ter seu plug-in de controle de origem associado alterado.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Alteração de plug-in para uma solução|1.  Selecione plug-in em teste como atual (**ferramentas** -> **opções** -> **controle de origem** -> **plug-in Seleção de**).<br />2.  Crie um novo projeto e solução.<br />3.  Adicione a solução ao controle de origem.<br />4.  Desacoplar a solução do controle de origem (usando o **alterar controle de origem** caixa de diálogo).<br />5.  Selecione outro plug-in (por exemplo, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />6.  Recarregue a solução de disco se descarregado.<br />7.  Adicione a solução ao controle de origem.<br />8.  Desacoplar a solução do controle de origem (usando **alterar controle de origem** caixa de diálogo).<br />9. Selecione plug-in em teste novamente.<br />10. Recarrega solução de disco se descarregado.<br />11. Associar a solução no local original (usando o **alterar controle de origem** caixa de diálogo).|Solução é adicionada ao controle de origem usando selecionado plug-in.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)