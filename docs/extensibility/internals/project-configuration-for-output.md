---
title: "Configuração para a saída de projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>Configuração de projeto para saída
Cada configuração pode dar suporte a um conjunto de processos de compilação que produzir saída de itens, como arquivos executáveis ou de recurso. Esses itens de saída são particulares para o usuário e podem ser colocados em grupos que vinculam tipos relacionados de saída, como arquivos executáveis (.exe,. dll,. lib) e arquivos de origem (. idl, arquivos. h).  
  
 Itens de saída podem ser disponibilizados através de <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> métodos e enumerados com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos. Quando você quiser agrupar os itens de saída, o projeto também deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interface.  
  
 A construção desenvolvido pela implementação `IVsOutputGroup` permite que os projetos saídas de grupo de acordo com o uso. Por exemplo, uma DLL pode ser agrupada com seu banco de dados do programa (PDB).  
  
> [!NOTE]
>  Um arquivo PDB contém informações de depuração e ele é criado quando a opção 'Gerar informações de depuração' é especificada ao criar o arquivo. dll ou .exe. O arquivo. PDB normalmente é gerado para a configuração de projeto de depuração somente.  
  
 O projeto deve retornar o mesmo número de grupos para cada configuração de seu suporte, embora o número de saídas contido dentro de um grupo pode variar para cada configuração. Por exemplo, Matt do projeto DLL pode incluir mattd.dll e mattd.pdb na configuração de depuração, mas apenas incluir matt.dll na configuração de varejo.  
  
 Os grupos também têm as mesmas informações de identificador, como nome canônico, nome de exibição e informações de grupo de configuração em um projeto. Essa consistência permite que a implantação e a embalagem continuam a operar mesmo que alterar as configurações.  
  
 Grupos também podem ter uma saída de chave que permite que os atalhos de empacotamento apontar para algo significativo. Qualquer grupo pode ser vazio em uma determinada configuração, portanto não deve ser feita nenhuma suposição sobre o tamanho de um grupo. O tamanho (número de saídas) de cada grupo em qualquer configuração pode ser diferente do tamanho de outro grupo na mesma configuração. Ele também pode ser diferente do tamanho do mesmo grupo em outra configuração.  
  
 ![Gráfico de grupos de saída](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Grupos de saída  
  
 O principal uso do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interface é fornecer acesso para compilar, implantar e depurar objetos de gerenciamento e permitir que os projetos a liberdade de saídas de grupo. Para obter mais informações sobre o uso desta interface, consulte [o objeto de configuração do projeto](../../extensibility/internals/project-configuration-object.md).  
  
 No diagrama anterior, o grupo criado tem uma chave de saída em configurações (bD.exe ou b.exe) para o usuário pode criar um atalho para criação e saber que o atalho funcionará independentemente da configuração implantada. Origem do grupo não tem uma chave de saída, para que o usuário não é possível criar um atalho para ele. Se a depuração grupo criado tem uma saída de chave, mas o grupo de varejo criados não, que poderá ser uma implementação incorreta. Ele segue, em seguida, que se qualquer configuração tem um grupo que não contenha nenhuma saída, e, como resultado, nenhum arquivo chave e outras configurações que contêm as saídas com esse grupo não podem ter arquivos de chave. Os editores de instalador pressupõem a nomes canônicos e nomes para exibição de grupos, além da existência de um arquivo de chave, não são alterados com base em configurações.  
  
 Observe que, se um projeto tem um `IVsOutputGroup` que ele deseja empacotar ou implantar, é suficiente para não colocar essa saída em um grupo. A saída ainda pode ser enumerada normalmente Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> método que retorna todas as saídas da configuração, independentemente do agrupamento.  
  
 Para obter mais informações, consulte a implementação de `IVsOutputGroup` do exemplo de projeto personalizado na [MPF de projetos](http://mpfproj12.codeplex.com).  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciar opções de configuração](../../extensibility/internals/managing-configuration-options.md)   
 [Configuração de projeto para criação](../../extensibility/internals/project-configuration-for-building.md)   
 [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)   
 [Configuração da solução](../../extensibility/internals/solution-configuration.md)