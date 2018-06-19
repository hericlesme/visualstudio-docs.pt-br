---
title: Decisões de Design do tipo de projeto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131483"
---
# <a name="project-type-design-decisions"></a>Decisões de Design de tipo de projeto
Antes de criar um novo tipo de projeto, você deve tomar várias decisões de design sobre o tipo de projeto. Você deve decidir quais tipos de itens que contém seus projetos, como arquivos de projeto serão mantidos e qual modelo de confirmação que você usará.  
  
## <a name="project-items"></a>Itens de projeto  
 Seu projeto usará arquivos ou objetos abstratos? Se você usar arquivos, eles será baseada no diretório ou referência de arquivos? São os arquivos ou objetos abstratos indo para ser local ou remoto?  
  
 Os itens em um projeto podem ser arquivos, ou podem ser objetos mais abstratos, como objetos em um banco de dados repositório ou conexões de dados pela Internet. Se os itens são arquivos, o projeto pode ser uma base de referência ou um projeto baseado no diretório.  
  
 Em projetos de referência, os itens podem aparecer em mais de um projeto. No entanto, o arquivo real que representa um item está localizado em um diretório somente. Em projetos com base no diretório, todos os itens de projeto existem na estrutura de diretório.  
  
 Os itens locais são armazenados no mesmo computador onde o aplicativo está instalado. Os itens remotos podem ser armazenados em um servidor separado em uma rede local ou em outro lugar na Internet.  
  
## <a name="project-file-persistence"></a>Persistência de arquivo de projeto  
 Serão armazenados os dados em sistemas de arquivos simples comuns ou em armazenamento estruturado? Arquivos serão abertos usando um editor padrão ou um editor específico do projeto?  
  
 Para manter seus dados, a maioria dos aplicativos salvar seus dados em um arquivo e, em seguida, lê-lo novamente quando um usuário deve examinar ou alterar as informações.  
  
 Armazenamento estruturado, também chamado de arquivos compostos, normalmente é usado quando vários objetos de modelo de objeto de componente (COM) necessário armazenar seus dados persistentes em um único arquivo. Com o armazenamento estruturado, vários componentes de software diferente podem compartilhar um arquivo de disco único.  
  
 Você tem várias opções para serem considerados relativos à persistência para os itens em seu projeto. Você pode executar qualquer uma das seguintes opções:  
  
-   Salve cada arquivo individualmente quando ele foi alterado.  
  
-   Capturar a quantidade de transações em uma única **salvar** operação.  
  
-   Salve arquivos localmente e publicar em um servidor ou usar outra abordagem para salvar itens de projeto quando o item representa uma conexão de dados para um objeto remoto.  
  
 Para obter mais informações sobre a persistência, consulte [persistência de projeto](../../extensibility/internals/project-persistence.md) e [abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modelo de compromisso do projeto  
 Objetos de dados persistentes ser abertos em modo direto ou transacionado?  
  
 Quando objetos de dados são abertos em modo direto, as alterações feitas nos dados são incorporadas imediatamente ou quando o usuário salva manualmente o arquivo.  
  
 Quando objetos de dados são abertos usando o modo de transação, as alterações são salvas em um local temporário na memória e não são confirmadas até que o usuário escolhe manualmente salvar o arquivo. Nesse momento, todas as alterações devem ser feitos juntos ou nenhuma alteração será feita.  
  
## <a name="see-also"></a>Consulte também  
 [Lista de verificação: Criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Abrir e salvar itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistência de projeto](../../extensibility/internals/project-persistence.md)   
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)   
 [Criar tipos de projeto](../../extensibility/internals/creating-project-types.md)