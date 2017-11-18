---
title: Avisos de criptografia | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4936482aea909938e135e8f61164955dacc9e20b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="cryptography-warnings"></a>Avisos de criptografia
Avisos de criptografia dão suporte a mais segura bibliotecas e aplicativos com o uso correto da criptografia. Esses avisos ajudam a evitar falhas de segurança em seu programa. Se você desabilitar um desses avisos, você deve marcar claramente a razão no código e também informar o agente de segurança designado para seu projeto de desenvolvimento.  
  
|Regra|Descrição|  
|----------|-----------------|  
|[CA5350: não usar algoritmos criptográficos fracos](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Algoritmos de criptografia fraca e funções de hash são usadas atualmente para vários motivos, mas não deve ser usados para garantir a confidencialidade ou a integridade dos dados que eles protegem.        Essa regra dispara quando ele encontra algoritmos TripleDES, SHA1 ou RIPEMD160 no código.|  
|[CA5351: não usar algoritmos criptográficos desfeitos](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Dividido criptográfico algoritmos não são considerados seguros e seu uso deve ser altamente desaconselhável. Essa regra dispara quando encontra o algoritmo de hash MD5 ou algoritmos de criptografia DES ou do RC2 no código.|