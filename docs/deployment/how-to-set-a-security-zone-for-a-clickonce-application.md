---
title: "Como: definir uma zona de segurança para um aplicativo ClickOnce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
caps.latest.revision: "18"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 2bba62850791f637e93d6c82ff2186ffc5f09652
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Como definir uma zona de segurança para um aplicativo ClickOnce
Ao definir permissões de segurança para um aplicativo ClickOnce de acesso do código, você precisa iniciar com um conjunto básico de permissões no **segurança** página do **Project Designer**.  
  
 Na maioria dos casos, você também pode escolher o **Internet** zona que contém um conjunto limitado de permissões, ou o **Intranet Local** zona que contém um conjunto maior de permissões. Se seu aplicativo requer permissões personalizadas, você pode fazer isso escolhendo o **personalizado** zona de segurança. Para obter mais informações sobre como definir permissões personalizadas, consulte [como: definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).  
  
### <a name="to-set-a-security-zone"></a>Para definir uma zona de segurança  
  
1.  Com um projeto selecionado no **Solution Explorer**, no **projeto** menu clique **propriedades**.  
  
2.  Clique na guia **Segurança**.  
  
3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.  
  
4.  Selecione o **é um aplicativo de confiança parcial** botão de opção.  
  
     Controles de **permissões de segurança do ClickOnce** seção estão habilitados.  
  
5.  No **seu aplicativo será instalado a partir de zona** lista suspensa, selecione uma zona de segurança.  
  
## <a name="see-also"></a>Consulte também  
 [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)