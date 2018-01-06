---
title: "Criar instâncias de projeto por meio de fábricas de projeto | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a331c131eaf48eb7be8bc3709599412aa01b1ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-instances-by-using-project-factories"></a>Criar instâncias de projeto por meio de fábricas de projeto
Projeto tipos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar um *fábrica de projeto* para criar instâncias de objetos do projeto. Uma fábrica de projeto é semelhante a uma fábrica de classe padrão para objetos cocreatable. No entanto, os objetos do projeto não estão cocreatable: só pode ser criados usando uma fábrica de projeto.  
  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chama a fábrica de projeto implementada no seu VSPackage quando um usuário carrega um projeto existente ou cria um novo projeto no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. O novo objeto de projeto fornece o IDE com informações suficientes para popular o Gerenciador de soluções. O novo objeto de projeto também fornece as interfaces necessárias para dar suporte a todas as ações de interface de usuário relevantes iniciadas pelo IDE.  
  
 Você pode implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interface em uma classe em seu projeto. Normalmente, ela reside em seu próprio módulo.  
  
 Para obter um exemplo de implementação do `IVsProjectFactory` interface, consulte PrjFac.cpp que está contida no [básicas do projeto](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) diretório de exemplo.  
  
 Projetos que oferecem suporte a que está sendo agregada por um proprietário devem manter uma chave de proprietário no seu arquivo de projeto. Quando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> método for chamado em um projeto com uma chave de proprietário, o projeto de propriedade converte sua chave de proprietário para uma fábrica de projeto GUID, em seguida, chama o `CreateProject` método nesta fábrica de projeto para fazer a criação real.  
  
## <a name="creating-an-owned-project"></a>Criando um projeto de propriedade  
 Um proprietário cria um projeto de propriedade em duas fases:  
  
1.  Chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> método. Isso fornece o projeto pertencente a oportunidade de criar um objeto de projeto agregado com base na entrada controla `IUnknown`. O projeto de propriedade interna é passado `IUnknown` e o objeto agregado do projeto proprietário. Isso fornece o projeto pertencente a chance de repositório interno `IUnknown`.  
  
2.  Chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> método. O projeto de propriedade não todos os seu instanciação quando este método é chamado em vez de chamar `IVsProjectFactory::CreateProject` como seria o caso para projetos que não são de propriedade. A entrada `VSOWNEDPROJECTOBJECT` enumeração normalmente é o projeto de propriedade agregado. O projeto de propriedade pode usar essa variável para determinar se o seu objeto de projeto já foi criado (cookie não é igual a NULL) ou deve ser criado (cookie igual a NULL).  
  
 Tipos de projeto são identificados por um GUID, semelhante a CLSID de um objeto COM cocreatable exclusivo do projeto. Normalmente, os identificadores de fábrica de um projeto, criar instâncias de um único tipo de projeto, embora seja possível ter uma fábrica de projeto lidar com a mais de um GUID de tipo de projeto.  
  
 Tipos de projeto estão associados com uma extensão de nome de arquivo específico. Quando um usuário tenta abrir um arquivo de projeto existente ou tenta criar um novo projeto pela clonagem de um modelo, o IDE usa a extensão no arquivo para determinar o GUID de projeto correspondente.  
  
 Assim que o IDE determina que se deve criar um novo projeto ou abrir um projeto existente de um determinado tipo, o IDE usa as informações no registro do sistema em [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] para encontrar qual VSPackage implementa a fábrica de projeto necessárias. O IDE carrega neste VSPackage. No <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método, o VSPackage deve registrar sua fábrica de projeto no IDE chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> método.  
  
 O principal método de `IVsProjectFactory` interface é <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> que deve lidar com dois cenários: abrir um projeto existente e criar um novo projeto. A maioria dos projetos armazenar seu estado de projeto em um arquivo de projeto. Normalmente, os novos projetos são criados por fazer uma cópia do arquivo de modelo passada para o `CreateProject` método e, em seguida, abrir a cópia. Projetos existentes são instanciados por diretamente a abertura do arquivo de projeto passado para `CreateProject` método. O `CreateProject` método pode exibir recursos adicionais de interface do usuário para o usuário conforme necessário.  
  
 Um projeto pode também não usar nenhum arquivo e, em vez disso, armazenar o estado do projeto em um mecanismo de armazenamento que não sejam de sistema de arquivos, como um servidor Web ou de banco de dados. Nesse caso, o parâmetro de nome de arquivo é passado para o `CreateProject` método não é realmente um caminho de sistema de arquivos, mas uma cadeia de caracteres exclusiva — uma URL — para identificar os dados do projeto. Você não precisa copiar os arquivos de modelo que são passados para `CreateProject` para disparar a sequência de construção apropriado a ser executado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Lista de verificação: criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)