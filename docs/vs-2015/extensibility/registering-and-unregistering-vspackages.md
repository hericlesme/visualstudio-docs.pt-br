---
title: Registrar e cancelar o registro de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8995bbb47f9a65a101256029a28313768a0b04ab
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464860"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrando e cancelando o registro de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Registrando e Cancelando o registro de VSPackages](https://docs.microsoft.com/visualstudio/extensibility/registering-and-unregistering-vspackages).  
  
Usar atributos para registrar um VSPackage, mas  
  
## <a name="registering-a-vspackage"></a>Registrando um VSPackage  
 Você pode usar atributos para controlar o registro de VSPackages gerenciados. Todas as informações de registro estão contidas em um arquivo. pkgdef. Para obter mais informações sobre o registro baseado em arquivo, consulte [utilitário CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 O código a seguir mostra como usar os atributos padrão de registro para registrar o VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Cancelar o registro de uma extensão  
 Se você estiver fazendo experiências com muita VSPackages diferentes e deseja removê-los da instância experimental, é possível executar o **redefinir** comando. Procure **redefinir a instância Experimental do Visual Studio** na página inicial do seu computador, ou execute este comando da linha de comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se você quiser desinstalar uma extensão que você instalou na sua instância de desenvolvimento do Visual Studio, acesse **ferramentas / extensões e atualizações**, localize a extensão e clique em **desinstalar**.  
  
 Se por alguma razão, nenhum desses métodos bem-sucedida em desinstalar a extensão, você pode cancelar o registro do assembly de VSPackage da linha de comando da seguinte maneira:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)

