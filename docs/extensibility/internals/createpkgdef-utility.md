---
title: Utilitário de CreatePkgDef | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8ae53766a42ac2ed218bc92f59088d27e4434e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="createpkgdef-utility"></a>Utilitário de CreatePkgDef
Usa um arquivo. dll para uma extensão do Visual Studio como um parâmetro e cria um arquivo de .pkgdef para acompanhar o. dll. O arquivo .pkgdef contém todas as informações que, caso contrário serão gravadas no registro do sistema quando a extensão está instalada.  
  
> [!NOTE]
>  A maioria dos modelos de projeto que estão incluídos no SDK do Visual Studio automaticamente cria arquivos .pkgdef como parte do processo de compilação. Este documento destina-se para aqueles que desejam criar pacotes manualmente ou converter os pacotes existentes para usar .pkgdef implantação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 limite =`FileName`  
 Necessário. Define o nome do arquivo de saída .pkgdef para`FileName`.  
  
 /codebase  
 Opcional. Registro de forças com o utilitário de base de código.  
  
 /assembly  
 Registro de forças com o utilitário de Assembly.  
  
 `AssemblyPath`  
 O caminho do arquivo. dll do qual você deseja gerar o .pkgdef.  
  
## <a name="remarks"></a>Comentários  
 Implantação de extensão usando arquivos .pkgdef substituirá os requisitos de registro de versões anteriores do Visual Studio.  
  
 Os arquivos de .pkgdef devem ser instalados em um dos seguintes locais: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou %vsinstalldir%\Common7\IDE\Extensions\\. Se a pasta de instalação é %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, a extensão será reconhecida pelo Visual Studio, mas será desabilitada por padrão. O usuário pode habilitar a extensão usando **extensões e atualizações**. Se a pasta de instalação é %vsinstalldir%\Common7\IDE\Extensions\\, a extensão está habilitada por padrão.  
  
> [!NOTE]
>  O **extensões e atualizações** ferramenta não pode ser usada para acessar uma extensão, a menos que ele é instalado como parte de um pacote do VSIX.  
  
## <a name="see-also"></a>Consulte também  
 [Utilitário CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)