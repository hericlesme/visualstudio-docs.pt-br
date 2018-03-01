---
title: "Caixa de diálogo Configurações Avançadas de Segurança | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ff3f23af3bf9358f47251a7ea45082f5508349b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-security-settings-dialog-box"></a>Caixa de diálogo Configurações de Segurança Avançadas
Essa caixa de diálogo permite especificar configurações de segurança relacionadas à depuração na zona.  
  
 Para acessar essa caixa de diálogo, selecione um nó do projeto no **Gerenciador de Soluções** e, no menu **Projeto**, clique em **Propriedades**. Quando o **Designer de Projeto** for exibido, clique na guia **Segurança**. Na página **Segurança** página, selecione **Habilitar Configurações de Segurança do ClickOnce**, clique em **Este é um aplicativo de confiança parcial** e, em seguida, clique em **Avançado**.  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Depurar este aplicativo com o conjunto de permissões selecionado**  
 Se você marcar essa caixa de seleção, o conjunto de permissões selecionado na página **Segurança** será usado durante a depuração. Por padrão, essa opção é selecionada.  
  
 Para depurar em uma zona de segurança para trabalhar, essa opção deve ser habilitada; além disso, a opção **Habilitar o processo de hospedagem do Visual Studio** (disponível na página **Depurar** página do **Designer de Projeto**) deve ser habilitada.  
  
 Para projetos de Aplicativos de Navegador da Web WPF, a opção **Depurar este aplicativo com o conjunto de permissões selecionado** é marcada e desabilitada.  
  
 **Conceder ao aplicativo acesso ao site de origem**  
 Se você marcar esta caixa de seleção, o aplicativo poderá acessar o site da Web ou o compartilhamento do servidor no qual ele é publicado. Por padrão, essa opção é selecionada.  
  
 **Depurar este aplicativo como se ele tivesse sido baixado da seguinte URL**  
 Se você precisar permitir que o aplicativo acesse o site da Web ou o compartilhamento de servidor correspondente à **URL de Instalação** especificado na página **Publicar**, digite a URL aqui. Essa opção está disponível apenas quando **Conceder ao aplicativo acesso ao site de origem** está selecionado.  
  
## <a name="see-also"></a>Consulte também  
 [Página Segurança, Designer de Projeto](../../ide/reference/security-page-project-designer.md)