---
title: "Solução (. Arquivos sln) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7be9b3bf7783980cfbbe1abfc44fe1748dd20a2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="solution-sln-file"></a>Solução (. Arquivos sln)
Uma solução é uma estrutura para organizar projetos no Visual Studio. A solução mantém as informações de estado para projetos em. sln (baseado em texto, compartilhado) e arquivos. suo (opções de solução de binário, especificada pelo usuário). Para obter mais informações sobre arquivos. suo, consulte [opções de usuário de solução (. Arquivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se seu VSPackage é carregado como resultado de que está sendo referenciado no arquivo. sln, o ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para ler o arquivo. sln.  
  
 O arquivo. sln contém informações com base em texto que usa o ambiente para localizar e carregar os parâmetros de nome-valor para os dados persistentes e o projeto VSPackages faz referência a ele. Quando um usuário abre uma solução, o ambiente percorre o `preSolution`, `Project`, e `postSolution` as informações no arquivo. sln para carregar a solução, projetos na solução e quaisquer informações persistentes anexado à solução.  
  
 Arquivo de cada projeto contém informações adicionais de leitura pelo ambiente de preencher a hierarquia com itens do projeto. A persistência de dados da hierarquia é controlada pelo projeto; os dados não são normalmente armazenados no arquivo. sln, embora seja possível escrever intencionalmente informações do projeto para o arquivo se você optar por fazer isso. Para obter mais informações relacionadas à persistência, consulte [persistência de projeto](../../extensibility/internals/project-persistence.md) e [abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Conteúdo do arquivo de solução  
 O arquivo. sln consiste em várias seções conforme ilustrado no código a seguir.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Para carregar uma solução, o ambiente executa a seguinte sequência de tarefas.  
  
1.  O ambiente lê a seção Global do arquivo. sln e processa todas as seções marcadas `preSolution`. Nesse caso, há uma essa instrução:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Quando o ambiente lê o `GlobalSection('name')` marca, ele mapeia o nome para um VSPackage usando o registro. O nome da chave deve existir no Registro [HKLM\\< raiz do registro de ID de aplicativo\>\SolutionPersistence\AggregateGUIDs]. Valor padrão das chaves é o GUID de pacote (REG_SZ) do VSPackage que gravou as entradas.  
  
2.  O ambiente carrega o VSPackage, chamadas `QueryInterface` sobre o VSPackage para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface e chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método com os dados na seção de forma que o VSPackage pode armazenar os dados. O ambiente se repetir esse processo para cada `preSolution` seção.  
  
3.  O ambiente itera através dos blocos de persistência de projeto. Nesse caso, há um projeto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Esta instrução contém o GUID exclusivo do projeto e o GUID do tipo de projeto. Essas informações são usadas pelo ambiente de localizar o arquivo de projeto ou arquivos que pertencem à solução e o VSPackage necessária para cada projeto. O projeto GUID é passado para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para carregar o VSPackage específico relacionado ao projeto, em seguida, o projeto é carregado pelo VSPackage. Nesse caso, o VSPackage que é carregado para este projeto é Visual Basic.  
  
     Cada projeto pode manter uma ID de instância exclusivo do projeto para que ele possa ser acessado conforme necessário por outros projetos na solução. Idealmente, se a solução e projetos estão sob controle do código fonte, o caminho para o projeto deve ser relativo ao caminho para a solução. Quando a solução for carregada pela primeira vez, os arquivos de projeto não podem ser no computador do usuário. Fazendo com que o arquivo de projeto armazenado no servidor em relação ao arquivo de solução, é relativamente simple para o arquivo de projeto a ser encontrado e copiados para o computador do usuário. Em seguida, ele copia e carrega o restante dos arquivos necessários para o projeto.  
  
4.  Com base nas informações contidas na seção de projeto do arquivo. sln, o ambiente carrega cada arquivo de projeto. O projeto em si, em seguida, é responsável pela população da hierarquia do projeto e carregar os projetos aninhados.  
  
5.  Após o processamento de todas as seções do arquivo. sln, a solução é exibida no Gerenciador de soluções e está pronta para modificação pelo usuário.  
  
 Se qualquer VSPackage que implementa um projeto na solução falhar ao carregar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> método é chamado e todos os outros projetos na solução tem a oportunidade de ignorar as alterações que pode ter feito durante o carregamento. Se ocorrerem erros de análise, o máximo possível de informações são preservadas com os arquivos de solução e o ambiente exibe uma caixa de diálogo de aviso ao usuário que a solução está corrompida.  
  
 Quando a solução é salvo ou fechada, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> método é chamado e passado para a hierarquia para ver se as alterações foram feitas para a solução que precisam ser inseridos no arquivo. sln. Um valor nulo, passado para `QuerySaveSolutionProps` em <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica que as informações está sendo persistente para a solução. Se o valor não for null, as informações persistentes serão para um projeto específico, determinado pelo ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.  
  
 Se não houver informações a serem salvas, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface é chamada com um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> método. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> método é chamado pelo ambiente de recuperar os pares nome-valor do `IPropertyBag` interface e gravar as informações para o arquivo.  
  
 `SaveSolutionProps`e `WriteSolutionProps` objetos são chamados recursivamente pelo ambiente de recuperar as informações sejam salvos do `IPropertyBag` interface até que todas as alterações que tenham sido inseridas no arquivo. sln. Dessa forma, você pode assegurar que as informações serão mantidas com a solução e o tempo disponível do próximo que a solução é aberta.  
  
 Cada VSPackage carregado é enumerado para ver se ele tiver qualquer coisa para salvar em arquivo. sln. Ele é somente no tempo de carregamento que as chaves do registro são consultadas. O ambiente conhece todos os pacotes carregados porque eles estão na memória no momento em que a solução é salvo.  
  
 Somente o arquivo. sln contém entradas na `preSolution` e `postSolution` seções. Não há nenhum semelhantes seções no arquivo. suo desde que a solução precisa dessas informações para carregar corretamente. O arquivo. suo contém opções específicas do usuário, como notas privadas, que não se destina a ser compartilhado ou colocado sob controle do código fonte.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opções de usuário de solução (. Arquivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluções](../../extensibility/internals/solutions.md)