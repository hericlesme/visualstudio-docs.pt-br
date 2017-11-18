---
title: "Criando e usando políticas do Check-In de análise de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b16b7e9f4dba55babfc7ad2ad90affe0ca93c508
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Criando e usando políticas de check-in de análise do código
Quando você usa o controle de versão de base da equipe (TFVC), você pode criar uma política de check-in do analysis código para o .NET Framework e projetos de código nativo (C/C++) em um projeto de equipe. Você pode usar a política de check-in do análise código para controlar e melhorar a qualidade do código é verificado para a base de código.  
  
 A política passa quando o local de compilação está atualizado e análise de código foi executada nos arquivos de origem mais recentes. No mínimo, as regras de análise de código que estão habilitadas no projeto de código devem conter as mesmas regras que estão definidos na diretiva team project check-in. Regras que foram especificadas como erros nas configurações do projeto de equipe também devem ser especificadas como erros no código do projeto  
  
> [!IMPORTANT]
>  Diretivas do check-in de análise de código não podem ser aplicadas a projetos de site da web. Elas podem ser aplicadas a projetos de aplicativo web.  
  
 Criar código de políticas de check-in de análise usando as configurações de projeto de equipe do [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]. Políticas de check-in são especificadas e aplicadas a um projeto de equipe, mas é executado de análise de código é configurado e executado para projetos de código individuais em computadores de desenvolvimento local. Esta seção descreve como especificar políticas análise do código check-in para um projeto de equipe e como implementar políticas de análise de código personalizadas para código gerenciado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como criar ou atualizar políticas de check-in de análise de código padrão](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Explica as etapas que você pode usar para definir e modificar uma política de análise de código para um projeto de equipe.  
  
 [Implementando políticas de Check-in personalizadas para código gerenciado](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Explica as etapas que você usa para criar uma regra personalizada definida para a política de check-in de um projeto de equipe e sincronizar os projetos de código do projeto de equipe com a política de check-in.  
  
 [Compatibilidade da versão para políticas de check-in de análise de código](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Explica os problemas de compatibilidade de check-in de análise de código entre as versões do [!INCLUDE[vstsLong](../code-quality/includes/vstslong_md.md)].  
  
 [Como personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Explica como adicionar palavras e os tokens para o dicionário que é referenciado em regras de nomenclatura de análise de código.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Definir e impor barreiras de qualidade](http://msdn.microsoft.com/Library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Melhorando a qualidade do código com políticas de check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)