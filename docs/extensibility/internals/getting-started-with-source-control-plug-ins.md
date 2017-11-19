---
title: "Guia de Introdução com Plug-ins de controle de origem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ccbc7536a899226b7f2d9433b6c451df33bbde5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-source-control-plug-ins"></a>Guia de Introdução com Plug-ins de controle de origem
Para criar um controle de origem plug-in, você deve criar uma DLL que implementa funções definidas na API de plug-in de controle de origem, e, em seguida, para registrar a DLL com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para torná-lo disponível para uso no controle de versão do código fonte.  
  
 Três versões da API do plug-in de controle de origem (versões 1.1 e 1.2 1.3) estão disponíveis para o plug-ins de controle de origem. A API de plug-in de controle de origem documentadas aqui é a versão 1.3. Ele foi projetado para ser totalmente compatível com o plug-ins de controle de origem com suporte a versões 1.1 e 1.2. O [o que há de novo na fonte de controle de plug-in API versão 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) seção detalha os novos recursos de suporte para a versão mais recente do que a API de plug-in de controle de origem.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como instalar um plug-in de controle do código-fonte](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Descreve como criar as entradas do registro necessárias para conectar uma DLL de controle do código-fonte.  
  
 [Novidades na Versão 1.3 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Fornece uma visão geral das alterações que foram feitas para a API de plug-in de controle de origem na versão 1.3.  
  
 [Novidades na Versão 1.2 da API do plug-in de controle de código-fonte](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Fornece uma visão geral das alterações que foram feitas para a API de plug-in de controle de origem na versão 1.2.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)  
 Fornece uma lista completa de todos os elementos da API de plug-in de controle de origem.  
  
 [Criar um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define o SDK de plug-in de controle de origem e descreve os recursos incluídos.