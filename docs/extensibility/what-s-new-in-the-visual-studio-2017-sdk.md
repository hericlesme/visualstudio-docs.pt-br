---
title: O que&#39;novo no SDK do Visual Studio 2017 | Microsoft Docs
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: abc1f12a5a6c7368bc47e8f4e924d109dcf87f57
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>O que&#39;novo no SDK do Visual Studio de 2017

O Visual Studio SDK tem os seguintes recursos novos e atualizados para 2017 do Visual Studio.

## <a name="vsix-v3-format"></a>Formato do VSIX v3

Para dar suporte a instalação do novo leve do Visual Studio de 2017, o formato de manifesto de extensão do VSIX foi atualizado para a versão 3 (v3 VSIX).

O novo formato tem suporte para:

* Declarando explicitamente pré-requisitos para ser detectado e instalado pelo VSIXInstaller.
* Assemblies de Ngen'ing na instalação da extensão.
* Instalando ativos fora da raiz de extensão normal.

Para saber mais sobre essas alterações, consulte os tópicos a seguir:

* [Alterações de extensibilidade de 2017](breaking-changes-2017.md)
* [Suporte a Ngen no VSIX v3](ngen-support.md)
* [Instalação fora da pasta de extensões](set-install-root.md)
* [Perguntas frequentes para extensibilidade do Visual Studio de 2017](faq-2017.md)

## <a name="migrating-extensibility-project-to-visual-studio-2017"></a>Migrando projeto de extensibilidade do Visual Studio de 2017

Para saber como atualizar seus projetos de extensibilidade e seus manifestos do VSIX para 2017 do Visual Studio, consulte [como: migrar projetos de extensibilidade para Visual Studio de 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelos de item e projeto personalizados

A partir do Visual Studio de 2017, verificação de modelos de item e projeto personalizados será não executada. Em vez disso, a extensão deve fornecer arquivos de manifesto do modelo que descrevem o local de instalação desses modelos. Você pode usar o Visual Studio de 2017 para atualizar as extensões VSIX. Se você implantar sua extensão usando um MSI, você deve gerar os arquivos de manifesto do modelo manualmente. Para obter mais informações, consulte [atualização personalizar modelos de projeto e Item para Visual Studio de 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). O esquema de manifesto do modelo está documentado em [Visual Studio Template manifesto Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Diretrizes de desempenho de extensão atualizada

Há uma nova [como: diagnosticar o desempenho de extensão](how-to-diagnose-extension-performance.md) tópico em [Gerenciando VSPackages](managing-vspackages.md) para mostrar como detectar e analisar o impacto de extensão no Visual Studio inicialização e solução de tempos de carregamento.
