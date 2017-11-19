---
title: "Práticas recomendadas para segurança no VSPackages | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770dff4b531bf4a7347cb648ca4c930b28b79bea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Práticas recomendadas de segurança em VSPackages
Para instalar o [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] em seu computador, você deve estar executando em um contexto com credenciais administrativas. A unidade básica de segurança e implantação de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicativo é o [VSPackages](../../extensibility/internals/vspackages.md). Um VSPackage deve ser registrado usando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que também requer credenciais administrativas.  
  
 Os administradores têm permissões completas para gravar no registro e sistema de arquivos e para executar qualquer código. Você deve ter essas permissões para desenvolver, implantar ou instalar um VSPackage.  
  
 Assim que ele é instalado, um VSPackage é totalmente confiável. Devido a esse nível alto de permissão associada a um VSPackage, é possível instalar inadvertidamente um VSPackage com más intenções.  
  
 Os usuários devem garantir que eles instalam VSPackages somente de fontes confiáveis. Empresas de desenvolvimento de VSPackages fortemente devem nomear e assiná-las garantir que o usuário que viole é evitada. Empresas de desenvolvimento de VSPackages devem examinar suas dependências externas, como serviços web e de instalação remota, para avaliar e corrigir quaisquer problemas de segurança.  
  
 Para obter mais informações, consulte as diretrizes de codificação segura para o .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do suplemento](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Segurança DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)