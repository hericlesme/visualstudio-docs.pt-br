---
title: Avisos de criptografia | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 947721de606cb6117ed2fd5f84bbc51e20e08203
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475503"
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [avisos de criptografia](https://docs.microsoft.com/visualstudio/code-quality/cryptography-warnings).  
  
Avisos de criptografia dão suporte a mais segura de bibliotecas e aplicativos por meio do uso correto da criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA5350: não usar algoritmos criptográficos fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fraca e funções de hash são usadas atualmente por uma série de motivos, mas não deve ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra dispara quando ele encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|  
|[CA5351: não usar algoritmos criptográficos desfeitos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Dividido criptográfico algoritmos não são considerados seguros e seu uso deve ser altamente desaconselhável. Essa regra dispara quando ele encontra o algoritmo de hash MD5 ou DES ou RC2 algoritmos de criptografia no código.|



