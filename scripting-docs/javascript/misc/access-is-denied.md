---
title: Acesso negado | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 8a512060-d744-47af-a83e-4ba42ea2c5b2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9c097cd09712d19acf5a0e4999b5c7a47469f958
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="access-is-denied"></a>O acesso foi negado
Um script tentou acessar dados de uma fonte que não é o host da página atual. A Política de Mesma Origem seguida pelo Internet Explorer e outros navegadores permite que scripts acessem dados somente de fontes com o mesmo esquema, host e porta de URL da página atual.  
  
 Por exemplo, se a página atual for https://employees.mycompany.com, você não pode acessar dados nas URLs a seguir:  
  
-   http://data.contoso.com, porque ela está usando HTTP em vez de HTTPS.  
  
-   https://somedatasource.com, porque se trata de um domínio diferente.  
  
-   https://employees.mycompany.com:8888, pois ela usa uma porta diferente.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Investigue se a API que você está tentando chamar dá suporte para JSONP ou CORS, que são duas abordagens que permitem o uso de scripts entre origens de forma segura.  
  
-   Se você estiver tentando chamar uma API REST, refatore essa chamada para seu código do lado do servidor e exponha um novo ponto de extremidade REST para seus scripts do lado do cliente.  
  
     Para saber mais, procure a documentação online relacionada a Política de Mesma Origem, JSONP e CORS.