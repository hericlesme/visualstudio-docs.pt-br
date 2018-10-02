---
title: Como excluir projetos de um build | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 569f0db1294bd7df2451c4ec496dc5064b122b73
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468330"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Como excluir projetos de um Build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [como: excluir projetos de uma compilação](https://docs.microsoft.com/visualstudio/ide/how-to-exclude-projects-from-a-build).  
  
É possível compilar uma solução sem compilar todos os projetos que ela contém. Por exemplo, é possível excluir um projeto que interrompe o build. É possível compilar o projeto depois de investigar e resolver os problemas.  
  
 É possível excluir um projeto adotando as seguintes abordagens:  
  
-   Removê-lo temporariamente da configuração da solução ativa.  
  
-   Criar uma configuração da solução que não inclua o projeto.  
  
 Para obter mais informações, consulte [Understanding Build Configurations (Noções básicas sobre configurações de build)](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Para remover temporariamente um projeto da configuração da solução ativa  
  
1.  Na barra de menus, escolha **Build**, **Configuration Manager**.  
  
2.  Na tabela **Contextos do projeto**, localize o projeto que você deseja excluir do build.  
  
3.  Na coluna **Build** do projeto, desmarque a caixa de seleção.  
  
4.  Escolha o botão **Fechar** e, em seguida, recompile a solução.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Para criar uma configuração da solução que exclui um projeto  
  
1.  Na barra de menus, escolha **Build**, **Configuration Manager**.  
  
2.  Na lista **Configuração da solução ativa**, escolha **\<Nova>**.  
  
3.  Na caixa **Nome**, insira um nome para a configuração da solução.  
  
4.  Na lista **Copiar configurações de**, escolha a configuração da solução na qual você deseja basear a nova configuração (por exemplo, **Depurar**) e, em seguida, escolha o botão **OK**.  
  
5.  Na caixa de diálogo **Configuration Manager**, desmarque a caixa de seleção na coluna **Build** do projeto que você deseja excluir e, em seguida, escolha o botão **Fechar**.  
  
6.  Na barra de ferramentas **Padrão**, verifique se a nova configuração da solução é a configuração ativa na caixa **Configurações da Solução**.  
  
7.  Na barra de menus, escolha **Compilar**, **Recompilar Solução**.  
  
## <a name="see-also"></a>Consulte também  
 [Noções sobre configurações de build](../ide/understanding-build-configurations.md)   
 [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md)   
 [Como compilar várias configurações simultaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)



