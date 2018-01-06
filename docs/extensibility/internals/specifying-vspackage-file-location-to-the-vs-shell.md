---
title: Especificando o local do arquivo de VSPackage ao Shell do VS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 35bd935683f8ace47536389ebc65f34311e9fcfd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificando o local do arquivo de VSPackage ao Shell do VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve ser capaz de localizar a DLL para carregar o VSPackage do assembly. Você pode localizá-lo de várias maneiras, conforme descrito na tabela a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|Use a chave de registro de base de código.|A chave de base de código pode ser usada para direcionar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar o assembly de VSPackage qualquer caminho de arquivo totalmente qualificado. O valor da chave deve ser o caminho de arquivo para a DLL. Essa é a melhor maneira de ter [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carregar seu assembly de pacote. Às vezes, essa técnica é conhecida como a "técnica de diretório de instalação de base de código/privadas". Durante o registro o valor da Base de código é passado para as classes de atributo do registro por meio de uma instância das <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Coloque a DLL para o **PrivateAssemblies** directory.|Coloque o assembly no **PrivateAssemblies** subdiretório do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Assemblies localizados em **PrivateAssemblies** são detectadas automaticamente, mas não são visíveis no **adicionar referências** caixa de diálogo. A diferença entre **PrivateAssemblies** e **PublicAssemblies** é que os assemblies em **PublicAssemblies** são enumerados no **adicionar referências**  caixa de diálogo. Se você optou por não usar a técnica "diretório de instalação de base de código/privada", você deve instalar para o **PrivateAssemblies** directory.|  
|Use um assembly de nome forte e a chave de registro do Assembly.|A chave do Assembly pode ser usada para direcionar explicitamente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para carregar um forte chamado assembly VSPackage. O valor da chave deve ser o nome forte do assembly.|  
|Coloque a DLL para o **PublicAssemblies** directory.|Por fim, o assembly também pode ser colocado no **PublicAssemblies** subdiretório. Assemblies localizados em **PublicAssemblies** são detectadas automaticamente e também aparecerá no **adicionar referências** da caixa de diálogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Assemblies de VSPackage só devem ser colocados no **PublicAssemblies** diretório se eles contêm gerenciados componentes que devem ser reutilizada por outros desenvolvedores VSPackage. A maioria dos assemblies não atendem esse critério.|  
  
> [!NOTE]
>  Use assemblies de nome forte, assinados para todos os assemblies dependentes. Esses assemblies também devem ser instalados em seu próprio diretório ou o cache de assembly global (GAC). Isso protege contra está em conflito com os assemblies que têm o mesmo nome de arquivo base, conhecido como associação de nome fraco.