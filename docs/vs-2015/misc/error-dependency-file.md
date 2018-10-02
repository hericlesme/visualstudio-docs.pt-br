---
title: 'Erro: a dependência &#39;arquivo&#39; no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ela entraria em conflito com dependência &#39;arquivo&#39; | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: douge
ms.openlocfilehash: 6f571ec21094a28077f63bf86d4afe97af5429dd
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2018
ms.locfileid: "47587382"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Erro: a dependência &#39;arquivo&#39; no projeto &#39;projeto&#39; não pode ser copiado para o diretório de execução porque ela entraria em conflito com dependência &#39;arquivo&#39;
Há um conflito entre referências; mais de uma dependência distinta com o mesmo nome de arquivo que está sendo copiado para o diretório bin para a execução do aplicativo. O diretório de execução não é possível resolver o conflito porque nenhuma das dependências são referências primárias.  
  
 Esse erro fará com que a compilação falhar.  
  
 Clicar duas vezes neste item de lista de tarefas, você serão levado para o nó de referências do projeto no qual o conflito está ocorrendo.  
  
 **Para corrigir este erro**  
  
-   Faça um dos assemblies de referência uma conexão direta do seu projeto. Uma possível desvantagem dessa abordagem é que o assembly que você escolher não é garantido para trabalhar com assemblies que exigem alguma outra versão do assembly referenciado.  
  
     \- ou -  
  
-   Certifique-se de que ambas as cópias do assembly são fortes e no cache de assembly global. Isso elimina a necessidade de copiar os assemblies para o diretório bin.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [Cache de assembly global](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)   
 [Assemblies de nomes fortes](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Controle de versão do assembly](http://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903)   
 [Como criar e remover dependências do projeto](../ide/how-to-create-and-remove-project-dependencies.md)