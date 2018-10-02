---
title: 'CA2228: Não remeter formatos de recurso não lançados | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 84dc7c20f4109f7d66ed83b22fcec36dacc5eb3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47587148"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: não remeter formatos de recurso não lançados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [CA2228: não remeter formatos de recurso não lançados](https://docs.microsoft.com/visualstudio/code-quality/ca2228-do-not-ship-unreleased-resource-formats).

|||
|-|-|
|NomeDoTipo|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Um arquivo de recurso foi criado usando uma versão do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que não é suportada atualmente.

## <a name="rule-description"></a>Descrição da Regra
 Arquivos de recursos que foram compilados usando versões de pré-lançamento do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] não podem ser utilizados por versões com suporte do .NET Framework.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, crie o recurso usando uma versão compatível do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]k.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.



