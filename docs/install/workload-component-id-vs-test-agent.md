---
title: IDs de carga de trabalho e de componente do Test Agent do Visual Studio 2017 | Microsoft Docs
description: Usar IDs de carga de trabalho e de componente do Visual Studio para executar testes automatizados e testes de carga remotamente
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 08/30/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: 55aea29b-1066-4e5a-aa99-fc87d4efb6d5
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 96018963278cd1d53b226473baade41da1e98111
ms.openlocfilehash: 78a656f32068055326567223b8ce6cd68095e647
ms.contentlocale: pt-br
ms.lasthandoff: 09/06/2017

---

# <a name="visual-studio-test-agent-2017-component-directory"></a>Diretório de componentes do Test Agent do Visual Studio 2017

As tabelas desta página listam as IDs que podem ser usadas para instalar o Visual Studio usando a linha de comando. Observe que adicionaremos outros componentes conforme atualizações forem liberadas para o Visual Studio.

Além disso, observe o seguinte sobre a página:

* Cada carga de trabalho tem sua própria seção, seguida pela ID da carga de trabalho e por uma tabela dos componentes que estão disponíveis para a carga de trabalho.
* Por padrão, os componentes **Obrigatórios** serão instalados durante a instalação da carga de trabalho. Se preferir, também será possível instalar os componentes **Recomendados** e **Opcionais**.
* Também adicionamos uma seção que lista os componentes adicionais que não são afiliados a nenhuma carga de trabalho.

Para obter mais informações sobre como usar essas IDs, consulte a página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Além disso, para obter uma lista de IDs de carga de trabalho e de componente para outros produtos, consulte a página [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md).

## <a name="test-agent"></a>Test Agent

**ID:** Microsoft.VisualStudio.Workload.TestAgent

**Descrição:** dá suporte à execução de testes automatizados e testes de carga remotamente

### <a name="components-included-by-this-workload"></a>Componentes incluídos por essa carga de trabalho

ID do componente | Nome | Versão | Tipo de dependência
--- | --- | --- | ---
Microsoft.VisualStudio.ComponentGroup.TestTools.TestAgent | Principais recursos do Test Agent | 15.0.26606.0 | Necessária

## <a name="unaffiliated-components"></a>Componentes não afiliados

Estes são os componentes que não são incluídos com nenhuma carga de trabalho, mas que podem ser selecionados como um componente individual.

ID do componente | Nome | Versão
--- | --- | ---
N/D | N/D | N/D


## <a name="see-also"></a>Consulte também

* [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)
