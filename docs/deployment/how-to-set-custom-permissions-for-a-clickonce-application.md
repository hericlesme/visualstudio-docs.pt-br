---
title: 'Como: definir permissões personalizadas para um aplicativo ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0980b2ddb2dd6a8db86078cb600f2486bb63f325
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31560434"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Como definir permissões personalizadas para um aplicativo ClickOnce
Você pode implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que usa as permissões padrão para as zonas da Internet ou Intranet Local. Como alternativa, você pode criar uma zona personalizada para as permissões específicas que o aplicativo precisa. Você pode fazer isso, basta personalizar as permissões de segurança no **segurança** página do **Project Designer**.  
  
### <a name="to-customize-a-permission"></a>Para personalizar uma permissão  
  
1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Segurança**.  
  
3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.  
  
4.  Selecione o **é um aplicativo de confiança parcial** botão de opção.  
  
     Controles de **permissões de segurança do ClickOnce** seção estão habilitados.  
  
5.  Do **seu aplicativo será instalado a partir de zona** lista suspensa, clique em **(personalizada)**.  
  
6.  Clique em **editar permissões XML**.  
  
     O arquivo App. manifest é aberto no Editor de XML.  
  
7.  Antes do `</applicationRequestMinimum>` elemento, adicione o código XML para as permissões que seu aplicativo requer.  
  
    > [!NOTE]
    >  Você pode usar o `ToXml` método de uma permissão definida para gerar o código XML para o manifesto do aplicativo. Por exemplo, para gerar o XML para o <xref:System.Security.Permissions.EnvironmentPermission> conjunto de permissões, chame o <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Protegendo aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)