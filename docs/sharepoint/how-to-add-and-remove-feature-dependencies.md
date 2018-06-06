---
title: 'Como: adicionar e remover dependências de recurso | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65963c43c5a4facd8a3ca7c0f8ab1ed1988342f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767784"
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Como: adicionar e remover dependências de recurso
  O recurso do SharePoint pode depender de outros recursos de funcionalidade ou dados. Nesses casos, você pode marcar esses outros recursos como dependências para o recurso. Dessa forma, o servidor do SharePoint assegura que os recursos dependentes são ativados antes que o recurso está ativado.  
  
## <a name="adding-dependencies"></a>Adicionando dependências  
 Você pode adicionar outros recursos em sua solução como dependências. Dessa forma, você pode verificar se que os recursos necessários são instalados e ativados antes que o recurso é instalado.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Para adicionar uma dependência em um recurso na solução
  
1.  Abra o Designer de recursos, expanda o **dependências de ativação de recurso** nó e, em seguida, escolha o **adicionar** botão.  
  
2.  No **adicionar dependências de ativação de recurso** caixa de diálogo caixa, escolha o **adicionar uma dependência de recursos na solução** botão de opção, escolha o título do recurso que você deseja adicionar como uma dependência e, em seguida, Escolha o **adicionar** botão.  
  
     Você pode adicionar mais de um recurso escolhendo vários títulos ao escolher o **Ctrl** chave.  
  
## <a name="adding-custom-dependencies"></a>Adicionando dependências personalizadas  
 Você pode adicionar recursos que já estão implantados em um servidor do SharePoint como uma dependência. Dessa forma, o processo de ativação do SharePoint verifica para ter certeza de que todos os recursos dependentes são ativados antes que o recurso é instalado.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Para adicionar uma dependência pela ID de recurso
  
1.  Abra o Designer de recursos, expanda o **dependências de ativação de recurso** nó e, em seguida, escolha o **adicionar** botão.  
  
2.  No **adicionar dependências de ativação de recurso** caixa de diálogo caixa, escolha o **adicionar uma dependência personalizada** botão de opção.  
  
3.  No **ID do recurso** texto, digite o GUID para o recurso que você deseja marcar como uma dependência de ativação e, em seguida, escolha o **adicionar** botão.  
  
## <a name="editing-custom-dependencies"></a>Edição de dependências personalizadas  
 Você pode editar dependências personalizadas que você adicionou anteriormente. No entanto, os recursos dependentes na solução pode somente ser removidos, não editado.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Para alterar uma dependência em um recurso na solução
  
1.  Abra o Designer de recursos e, em seguida, expanda o **dependências de ativação de recurso** nó.  
  
2.  Escolha o nome do recurso que você deseja editar e, em seguida, escolha o **editar** botão.  
  
3.  No **Editar dependência de ativação de recurso personalizado** caixa de diálogo, altere o título, a ID do recurso ou a descrição e, em seguida, escolha o **enviar** botão.  
  
## <a name="removing-dependencies"></a>Remoção de dependências  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Para remover uma dependência em um recurso na solução
  
1.  No Designer de recursos, expanda o **dependências de ativação de recurso** nó, escolha o nome do recurso que você deseja remover e, em seguida, escolha o **remover** botão.  
  
## <a name="see-also"></a>Consulte também
 [Criar recursos do SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Como: personalizar um recurso do SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Como adicionar e remover itens de funcionalidades do SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
