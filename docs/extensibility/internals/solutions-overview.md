---
title: Visão geral das soluções | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d64175c570c4fbca26bae0aa587b66e04cbee2be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="solutions-overview"></a>Visão geral das soluções
Uma solução é um agrupamento de um ou mais projetos que trabalham juntos para criar um aplicativo. As informações de status e projeto pertencente à solução são armazenados em dois arquivos de solução diferentes. O arquivo de solução (. sln) é baseado em texto e pode ser colocado sob controle do código fonte e compartilhado entre os usuários. O arquivo de opção (. suo) de usuário de solução é binário. Como resultado, o arquivo. suo não pode ser colocado sob controle do código fonte e contém informações específicas do usuário.  
  
 Qualquer VSPackage pode gravar em qualquer tipo de arquivo de solução. Devido à natureza dos arquivos, há duas interfaces diferentes implementados gravá-los. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface grava as informações de texto para o arquivo e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interface grava fluxos binários para o arquivo. suo.  
  
> [!NOTE]
>  Um projeto não precisa explicitamente gravar uma entrada para si mesmo para o arquivo de solução; o ambiente que trata do projeto. Portanto, a menos que você deseja adicionar o conteúdo adicional especificamente para o arquivo de solução, você não precisa registrar o VSPackage dessa maneira.  
  
 Cada VSPackage dando suporte a persistência de solução usa três interfaces, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface, que é implementado pelo ambiente e chamado pelo VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, que são implementados pelo VSPackage. O `IVsPersistSolutionOpts` interface só precisa ser implementado se informações particulares sejam gravados pelo VSPackage para o arquivo. suo.  
  
 Quando uma solução é aberta, o seguinte processo ocorre.  
  
1.  O ambiente lê a solução.  
  
2.  Se o ambiente de encontrar um `CLSID`, ele carrega o VSPackage correspondente.  
  
3.  Se um VSPackage é carregado, o ambiente chama `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interface para a interface que requer o VSPackage.  
  
    1.  Ao ler de um arquivo. sln, o ambiente chama `QueryInterface` para `IVsPersistSolutionProps`.  
  
    2.  Durante a leitura de um arquivo. suo, o ambiente chama `QueryInterface` para `IVsPersistSolutionOpts`.  
  
 Informações específicas relacionadas ao uso desses arquivos podem ser encontradas no [solução (. Arquivos sln)](../../extensibility/internals/solution-dot-sln-file.md) e [opções de usuário de solução (. Arquivo suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Se você quiser criar uma nova configuração de solução consiste em configurações de dois projetos e excluindo um terço da compilação, você precisa usar a automação ou páginas de propriedade de interface do usuário. Você não pode alterar as configurações de Gerenciador de compilação de solução e suas propriedades diretamente, mas você pode manipular o Gerenciador de compilação da solução usando o `SolutionBuild` classe de DTE no modelo de automação. Para obter mais informações sobre a configuração de soluções, consulte [configuração de solução](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>