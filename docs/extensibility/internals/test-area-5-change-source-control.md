---
title: 'Área de teste 5: Alterar controle do código-fonte | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7fd014bf520ee2f0515e284f2fb5430961cd407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134328"
---
# <a name="test-area-5-change-source-control"></a>Área de teste 5: Alterar o controle de origem
Essa área de plug-in de teste de controle de origem abrange alterando o controle de origem por meio de **alterar controle de origem** comando.  
  
 **Alterar controle do código-fonte** comando fornece quatro funções básicas para o usuário:  
  
-   **Vincule:**  
  
     Permite que um usuário estabelecer ou restabelecer um vínculo de controle de origem entre uma solução/projeto e o armazenamento de versão.  
  
-   **Desassocie:**  
  
     Remove uma projeto/solução de controle de origem em uma base por conexão.  
  
-   **Conectar/Desconecte:**  
  
 Alterna o estado conectado ou offline da solução controlada, que é abordado na área 3. Para obter mais informações, consulte [teste área 3: Check-Out / desfazer check-out](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Acesso de Menu de comando  
 O seguinte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caminho de menu do ambiente de desenvolvimento integrado é usado nos casos de teste.  
  
 Alterar controle de origem:**arquivo**, **controle de origem**, **alterar controle do código-fonte**.  
  
## <a name="test-cases"></a>Casos de teste  
 Estes são os casos de teste específicos para o **alterar controle de origem** comando área de teste.  
  
### <a name="case-5a-bind"></a>Caso 5a: associar  
 Ligação permite que o usuário adicione informações de controle do código fonte para as soluções e projetos selecionados. Normalmente, o usuário é solicitado a identificar um projeto no controle de origem para o qual eles serão adicionados. O usuário não pode criar um novo projeto no controle de origem como parte dessa operação (contraste com adicionar ao controle de origem).  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Vincular a local vazio|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra **alterar controle de origem** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />4.  Clique em **desassociar**.<br />5.  Aceite a caixa de diálogo de aviso se ele for exibido.<br />6.  Selecione todos os itens.<br />7.  Clique em **associar**.<br />8.  Navegue até um local vazio em um repositório de controle de origem.<br />9. Clique em **Okey** para fechar o **alterar controle de origem** caixa de diálogo.<br />10. Clique em **continuar com estas associações** na caixa de diálogo de confirmação.<br />11. Clique em **Okey** na caixa de diálogo de aviso se ele for exibido.<br />12. Check-in de tudo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />13. Abra a solução do controle de origem para um novo local.|`Result from Step 12:`<br /><br /> Solução e projeto são associadas a e gravados para o novo destino no repositório de versão.<br /><br /> Arquivos de solução e projeto são verificados em.<br /><br /> Hierarquia de projeto do armazenamento de versão coincide com a hierarquia de pasta do projeto no disco.<br /><br /> `Result from Step 13:`<br /><br /> Todos os itens de projeto são baixados.|  
|Vincular a local que está em sincronia com o cliente|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Criar uma duplicata da solução e projeto no repositório de versão (compartilhar e ramificar se usando [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Abra **alterar controle de origem** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />5.  Desassocie todos.<br />6.  Clique em **Okey** para fechar **alterar controle de origem** caixa de diálogo.<br />7.  Reabra **alterar controle de origem** caixa de diálogo.<br />8.  Selecione tudo.<br />9. Clique em **associar**.<br />10. Navegue até o local ramificado da solução e do projeto (da etapa 3)<br />11. Clique em **Okey** para fechar o **alterar controle de origem** caixa de diálogo.<br />12. Obter recursivamente mais recente para todos os itens.|Conteúdo do arquivo depois de get é o mesmo anterior get.|  
|Vincular a local que está fora de sincronia com o cliente|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Criar uma duplicata da solução e projeto no repositório de versão (compartilhar e ramificar se usando [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Modificar os arquivos no projeto ramificado no armazenamento de versão.<br />5.  Abra **alterar controle de origem** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />6.  Desassocie todos.<br />7.  Clique em **Okey** para fechar **alterar controle de origem** caixa de diálogo.<br />8.  Reabra **alterar controle de origem** caixa de diálogo.<br />9. Selecione tudo.<br />10. Clique em **associar**.<br />11. Navegue até ramificado local para a solução e projeto.<br />12. Clique em **Okey** para fechar o **alterar controle de origem** caixa de diálogo.<br />13. Aceite a caixa de diálogo de aviso se ele for exibido.<br />14. Obter recursiva mais recente para todos os itens.|Os arquivos que foram modificados na etapa 4 também são modificados localmente.|  
|Associar a solução foi nunca sob controle do código-fonte|1.  Crie uma pasta vazia no controle de origem.<br />2.  Crie um projeto de cliente.<br />3.  Abra **alterar controle de origem** caixa de diálogo (**arquivo**, **controle de origem**, **alterar controle de origem**).<br />4.  Associe a solução para um local vazio no controle de origem.<br />5.  Clique em **Okey** para fechar o **alterar controle de origem** caixa de diálogo.<br />6.  Clique em **continuar com estas associações** na caixa de diálogo de confirmação.<br />7.  Clique em **Okey** na caixa de diálogo de aviso se ele for exibido.|Solução é adicionada ao controle de origem.<br /><br /> Solução e projeto são check-out.|  
|Cancelar a ligação|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra a caixa de diálogo Alterar controle de origem.<br />4.  Desassocie todos.<br />5.  Clique em **Okey** para fechar a caixa de diálogo. Se essa etapa for bem-sucedida, continue para a próxima etapa.<br />6.  Reabra o **alterar controle de origem** caixa de diálogo.<br />7.  Vincule a local não relacionado.<br />8.  Clique em **Cancelar**.|`Result from Step 5:`<br /><br /> A solução não está mais sob controle do código-fonte<br /><br /> `Result from Step 8:`<br /><br /> Solução é ainda não está em controle de origem.|  
  
### <a name="case-5b-unbind"></a>Caso 5b: desvincular  
 Desassocie remove informações de controle de código fonte da sua solução e projetos. A solução e projetos afetados com base em uma combinação de seleção de usuário e como os itens foram adicionados ao controle de origem.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Desacoplar a solução que contém um sistema de arquivos ou o projeto da Web do IIS local e o projeto de um cliente|1.  Crie um sistema de arquivos ou o projeto da Web do IIS local.<br />2.  Adicione a solução ao controle de origem.<br />3.  Adicione um novo projeto de cliente para a solução.<br />4.  Aceite Check-Out feito da solução, se solicitado.<br />5.  Abra o **alterar controle de origem** caixa de diálogo.<br />6.  Clique em **desassociar**.<br />7.  Clique em **OK** para fechar a caixa de diálogo.<br />8.  Tentativa de fazer check-out da solução, projeto, itens de solução, itens de projeto.|Solução e projetos não estão sob controle do código-fonte.<br /><br /> Comandos de menu de controle de origem não são exibidas.|  
|Desassocie Cancelar|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra o **alterar controle de origem** caixa de diálogo.<br />4.  Clique em **desassociar todos**.<br />5.  Clique em **Cancelar**.|Solução estiver sob controle do código-fonte.|  
  
### <a name="case-5c-rebind"></a>Caso 5c: Reassociar  
 Reassociar é simplesmente uma combinação de desvinculação e ligação — o processo de reassociação de uma projeto/solução que estava sob controle do código-fonte e foi desassociado.  
  
|Ação|Etapas de teste|Resultados esperados para verificar|  
|------------|----------------|--------------------------------|  
|Associar novamente a solução e projetos sem fechar o **alterar controle de origem** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicione a solução ao controle de origem.<br />3.  Abra o **alterar controle de origem** caixa de diálogo.<br />4.  Clique em **desassociar**.<br />5.  Selecione todas as linhas.<br />6.  Clique em **associar**.<br />7.  Clique em **Okey** para fechar o **alterar controle de origem** caixa de diálogo.<br />8.  Aceite check-out, se solicitado.|Solução e projeto estiver sob controle de origem.|  
|Reassociar projeto somente sem fechar **alterar controle de origem** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicionar apenas o projeto ao controle de origem usando (arquivo -> fonte de controle -> adicionar projetos selecionados ao controle de origem.<br />3.  Abra a caixa de diálogo Alterar controle de origem.<br />4.  Desassocie apenas o projeto.<br />5.  Associe apenas o projeto.|Solução permanece não controlada.<br /><br /> Projeto permanece controlado.|  
|Reassociar solução apenas sem fechar **alterar controle de origem** caixa de diálogo|1.  Criar um projeto.<br />2.  Adicionar somente a solução ao controle de origem usando (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**.<br />3.  Abra o **alterar controle de origem** caixa de diálogo.<br />4.  Desassocie apenas a solução (não feche **alterar controle de origem** caixa de diálogo.)<br />5.  Associe apenas a solução.<br />6.  Clique em **OK** para fechar a caixa de diálogo.<br />7.  Check-out de solução e itens de solução (se houver)|Solução permanece controlada.<br /><br /> Projeto permanece não controlado.|  
|Reassociar o projeto/solução apenas no mesmo diretório|1.  Criar um projeto.<br />2.  Adicionar apenas o projeto ao controle de origem usando (**arquivo**, **controle de origem**, **adicionar projetos selecionados ao controle de origem**.<br />3.  Feche a solução.<br />4.  Crie uma nova solução com pelo menos dois projetos.<br />5.  Adicione a solução ao controle de origem.<br />6.  Adicione o projeto criado na etapa 1 do controle de origem.<br />7.  Se solicitado, aceite o check-out da solução.<br />8.  Check-in de toda a solução.<br />9. Abra o **alterar controle de origem** caixa de diálogo.<br />10. Selecione o projeto adicional (da etapa 6) e clique em **desagrupar**.<br />11. Clique em **OK** para fechar a caixa de diálogo.<br />12. Se solicitado, aceite o check-out.<br />13. Reabra **alterar controle de origem** caixa de diálogo.<br />14. Selecione o projeto adicional (da etapa 6) e clique em **associar**.<br />15. Selecione o local original.|Solução e projetos permanecem controlados.|  
  
## <a name="see-also"></a>Consulte também  
 [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)