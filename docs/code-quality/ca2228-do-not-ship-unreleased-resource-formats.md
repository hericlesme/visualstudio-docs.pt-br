---
title: 'CA2228: não remeter formatos de recurso não lançados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f444779fc5db725c090f96ec51a86d8427a14d17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919175"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: não remeter formatos de recurso não lançados
|||
|-|-|
|NomeDoTipo|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separáveis|

## <a name="cause"></a>Causa
 Um arquivo de recurso foi criado usando uma versão do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que não é suportada atualmente.

## <a name="rule-description"></a>Descrição da Regra
 Arquivos de recursos que foram criados usando versões de pré-lançamento do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] não pode ser usado por versões com suporte do .NET Framework.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra, criar o recurso usando uma versão com suporte a [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]k.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.