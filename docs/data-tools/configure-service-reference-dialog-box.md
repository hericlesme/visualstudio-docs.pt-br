---
title: Caixa de diálogo Configurar Referência de Serviço
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ed20865726832b57d4d0624d6305daa6ba0fe6fa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="configure-service-reference-dialog-box"></a>Caixa de diálogo Configurar Referência de Serviço

O **configurar referência de serviço** caixa de diálogo permite que você configure o comportamento dos serviços do Windows Communication Foundation (WCF).

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha Importar e Exportar Configurações no menu Ferramentas. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Para acessar o **configurar referência de serviço** caixa de diálogo, com o botão direito, um serviço de referência em **Solution Explorer** e escolha **configurar referência de serviço**. Você também pode acessar a caixa de diálogo clicando o **avançado** no botão de **Adicionar caixa de diálogo de referência de serviço**.

## <a name="task-list"></a>Lista de Tarefas

- Para alterar o endereço onde um serviço WCF é hospedado, digite o novo endereço na **endereço** campo.

- Para alterar o nível de acesso para classes em um cliente de WCF, selecione uma palavra-chave de nível de acesso no **nível para as classes geradas de acesso** lista.

- Para chamar os métodos de um serviço WCF de forma assíncrona, selecione o **gerar operações assíncronas** caixa de seleção.

- Para gerar tipos de contrato de mensagem em um cliente de WCF, selecione o **sempre gerar contratos de mensagem** caixa de seleção.

- Para especificar os tipos de coleção de dicionário ou lista para um cliente WCF, selecione os tipos do **tipo de coleção** e **tipo de coleção de dicionário** lista.

- Para desabilitar o compartilhamento de tipo, desmarque o **reutilizar tipos em assemblies referenciados** caixa de seleção. Para habilitar o compartilhamento para um subconjunto de assemblies referenciados de tipo, selecione o **reutilizar tipos em assemblies referenciados** caixas de seleção **reutilizar tipos em determinados assemblies consultados**e selecione o desejado referências no **lista de assemblies referenciados**.

## <a name="uielement-list"></a>Lista UIElement

 **Endereço**

 Usado para atualizar o endereço da Web onde uma referência de serviço procura por um serviço. Por exemplo, durante o desenvolvimento de serviço pode estar hospedado em um servidor de desenvolvimento e posteriormente movido para um servidor de produção, a necessidade de uma alteração de endereço.

> [!NOTE]
> O elemento endereço não está disponível quando o **configurar referência de serviço** caixa de diálogo é exibida do **Adicionar caixa de diálogo de referência de serviço**.

 **Nível de acesso para classes geradas**

 Determina o nível de acesso de código para classes de cliente do WCF.

> [!NOTE]
> Para projetos de site, essa opção é sempre definida como `Public` e não pode ser alterado. Para obter mais informações, consulte [Solucionando problemas de referências de serviço](../data-tools/troubleshooting-service-references.md).

 **Gerar operações assíncronas**

 Determina se os métodos de serviço WCF serão chamados síncrona (o padrão) ou assíncrona.

 **Gerar operações com base em tarefa**

 Ao escrever código assíncrono, esta opção permite que você tire proveito da tarefa paralela TPL (biblioteca) que foi introduzido com o .net 4. Consulte [tarefas biblioteca paralelas (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

 **Sempre gerar contratos de mensagem**

 Determina se os tipos de contrato de mensagem serão gerados para um cliente do WCF. Para obter mais informações sobre contratos de mensagem, consulte [usando contratos de mensagem](/dotnet/framework/wcf/feature-details/using-message-contracts).

 **Tipo de coleção**

 Especifica o tipo de coleção da lista para um cliente do WCF. O tipo padrão é <xref:System.Array>.

 **Tipo de coleção de dicionário**

 Especifica o tipo de coleção de dicionário para um cliente do WCF. O tipo padrão é <xref:System.Collections.Generic.Dictionary%602>.

 **Reutilizar tipos em assemblies consultados**

 Determina se um cliente WCF irá tentar reutilizar que já existem em assemblies referenciados em vez de gerar novos tipos quando um serviço é adicionado ou atualizado. Por padrão, essa opção é selecionada.

 **Tipos de reutilização em todos os assemblies referenciados**

 Quando selecionada, todos os tipos de **lista de assemblies referenciados** serão reutilizados se possível. Por padrão, essa opção é selecionada.

 **Usar novamente os tipos em determinados assemblies consultados**

 Quando selecionada, somente os tipos selecionados no **lista de assemblies referenciados** será reutilizada.

 **Lista de assemblies referenciados**

 Contém uma lista de assemblies referenciados para o projeto ou o site da Web. Quando **reutilizar tipos em determinados assemblies consultados** for selecionada, assemblies individuais podem ser marcados ou desmarcados.

 **Adicionar referência da Web**

 Exibe a caixa de diálogo Adicionar referência da Web.

> [!NOTE]
> Essa opção deve ser usada apenas para projetos que usam a versão 2.0 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> O **adicionar referência Web** botão está disponível apenas quando o **configurar referência de serviço** caixa de diálogo é exibida do **Adicionar caixa de diálogo de referência de serviço**.

## <a name="see-also"></a>Consulte também

- [Como: adicionar uma referência a um serviço Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Serviços do Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)