---
title: MSSCCPRJ. Arquivos SCC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b61478b482ed10aba61ea9ce412dc0fe0725b0bd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Arquivos SCC
Quando uma solução do Visual Studio ou o projeto está sob controle de origem usando o IDE, o IDE recebe duas partes importantes de informações de controle de origem de plug-in na forma de cadeias de caracteres. Essas cadeias de caracteres "AuxPath" e "Nomedoprojeto" são opacas para o IDE, mas eles são usados pelo plug-in para localizar a solução ou projeto no controle de versão. O IDE normalmente obtém essas cadeias de caracteres na primeira vez chamando o [SccGetProjPath](../extensibility/sccgetprojpath-function.md), e ele salva em seguida, no arquivo de solução ou projeto para chamadas futuras para o [SccOpenProject](../extensibility/sccopenproject-function.md). Quando inserido nos arquivos de solução e projeto, as cadeias de caracteres "AuxPath" e "Nomedoprojeto" não são atualizadas automaticamente quando um usuário ramificações bifurcações, ou copia arquivos de solução e projeto que estão no controle de versão. Para certificar-se de que os arquivos de solução e projeto apontem para o local correto no controle de versão, os usuários devem atualizar manualmente as cadeias de caracteres. Porque as cadeias de caracteres devem ser opaco, ele não sempre estar claro como eles devem ser atualizados.  
  
 O plug-in de controle de origem pode evitar esse problema, armazenando as cadeias de caracteres "AuxPath" e "Nomedoprojeto" em um arquivo especial chamado de MSSCCPRJ. Arquivos SCC. É um arquivo local, do lado do cliente que é de propriedade e mantido pelo plug-in. Esse arquivo nunca é colocado sob controle do código-fonte, mas é gerado pelo plug-in para cada diretório que contém arquivos de origem controlada. Para determinar quais arquivos são arquivos de solução e projeto do Visual Studio, um plug-in de controle de origem pode comparar as extensões de arquivo com uma lista padrão ou fornecido pelo usuário. Depois que o IDE detecta que um plug-in oferece suporte a MSSCCPRJ. Arquivos SCC, ele inserir "AuxPath" e cadeias de caracteres "Nomedoprojeto" na solução e arquivos de projeto e ele lê essas cadeias de caracteres da MSSCCPRJ. SCC arquivo em vez disso.  
  
 Um controle de origem plug-in que oferece suporte a MSSCCPRJ. Arquivos SCC devem cumprir as diretrizes a seguir:  
  
-   Pode haver apenas um MSSCCPRJ. Arquivos SCC por diretório.  
  
-   Um MSSCCPRJ. Arquivos SCC podem conter a "AuxPath" e "Nomedoprojeto" para vários arquivos que estão sob o controle de origem em um determinado diretório.  
  
-   A cadeia de caracteres "AuxPath" não deve ter aspas dentro dele. É permitido ter aspas como delimitadores (por exemplo, um par de aspas duplas pode ser usado para indicar uma cadeia de caracteres vazia). O IDE removeremos todas as aspas de cadeia de caracteres "AuxPath" quando o MSSCCPRJ é lido. Arquivos SCC.  
  
-   A cadeia de caracteres "Nomedoprojeto" no MSSCCPRJ. Arquivos SCC devem corresponder exatamente a cadeia de caracteres retornada do `SccGetProjPath` função. Se a cadeia de caracteres retornada pela função tiver aspas ao redor dele, a cadeia de caracteres no MSSCCPRJ. Arquivos SCC devem ter aspas ao redor dele e vice-versa.  
  
-   Um MSSCCPRJ. Arquivos SCC é criado ou atualizado sempre que um arquivo é colocado sob controle do código-fonte.  
  
-   Se um MSSCCPRJ. Arquivos SCC é excluído, um provedor deve gerá-la novamente na próxima vez que ele executa uma operação de controle de origem com relação a esse diretório.  
  
-   Um MSSCCPRJ. Arquivos SCC estritamente devem seguir o formato definido.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Uma ilustração do MSSCCPRJ. Formato de arquivo de SCC  
 A seguir está um exemplo da MSSCCPRJ. Formato de arquivo do SCC (os números de linha são fornecidos apenas como um guia e não devem ser incluídos no corpo do arquivo):  
  
 [Linha 1]`SCC = This is a Source Code Control file`  
  
 [Linha 2]  
  
 [Linha 3]`[TestApp.sln]`  
  
 [Linha 4]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Linha 5]`SCC_Project_Name = "$/TestApp"`  
  
 [Linha 6]  
  
 [Linha 7]`[TestApp.csproj]`  
  
 [Linha 8]`SCC_Aux_Path = "\\server\vss\"`  
  
 [Linha 9]`SCC_Project_Name = "$/TestApp"`  
  
 A primeira linha declara a finalidade do arquivo e serve como a assinatura para todos os arquivos desse tipo. Essa linha deve aparecer exatamente como isso em todas as MSSCCPRJ. Arquivos SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 O que vem a seguir é uma seção de configurações para cada arquivo, marcado pelo nome do arquivo entre colchetes. Esta seção é repetida para cada arquivo que está sendo rastreado. Essa linha é um exemplo de um nome de arquivo, ou seja, `[TestApp.csproj]`. O IDE espera que as duas linhas a seguir. No entanto, ele não define o estilo dos valores definidos. As variáveis são `SCC_Aux_Path` e `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Não há nenhum delimitador final para essa seção. O nome do arquivo, bem como todos os literais que aparecem no arquivo, são definidas no arquivo de cabeçalho scc.h. Para obter mais informações, consulte [cadeias de caracteres usadas como chaves para localizar um plug-in de controle de origem](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [Cadeias de caracteres usadas como chaves para localizar um plug-in de controle do código-fonte](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)