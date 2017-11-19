---
title: 'Passo a passo: Criando um DataTable no Designer de conjunto de dados | Microsoft Docs'
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 0e1328eda7974b7e4ec04df0c4f5bd969cf09de6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Instruções passo a passo: criando um DataTable no Designer de Conjunto de Dados
Este passo a passo explica como criar um <xref:System.Data.DataTable> (sem um TableAdapter) usando o **Dataset Designer**. Para obter informações sobre como criar tabelas de dados que incluem TableAdapters, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar um novo projeto de aplicativo do Windows Forms  
  
-   Adicionando um novo conjunto de dados para o aplicativo  
  
-   Adicionar uma nova tabela de dados para o conjunto de dados  
  
-   Adicionando colunas à tabela de dados  
  
-   Definindo a chave primária da tabela  
  
## <a name="creating-a-new-windows-forms-application"></a>Criando um novo aplicativo do Windows Forms  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>Para criar um novo projeto de aplicativo do Windows Forms  
  
1. No Visual Studio, no **arquivo** menu, selecione **novo**, **projeto...** .  
  
2. Expanda **Visual C#** ou **Visual Basic** no painel esquerdo, selecione **área de trabalho clássica do Windows**.  

3. No painel central, selecione a **aplicativo do Windows Forms** tipo de projeto.  

4. Nomeie o projeto **DataTableWalkthrough**e, em seguida, escolha **Okey**. 
  
     O **DataTableWalkthrough** projeto é criado e adicionado ao **Gerenciador de soluções**.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Adicionando um novo conjunto de dados para o aplicativo  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Para adicionar um novo item de conjunto de dados ao projeto  
  
1.  Sobre o **projeto** menu, selecione **Adicionar Novo Item...** .  
  
     A caixa de diálogo Adicionar Novo Item é exibida.  
  
2.  No painel esquerdo, selecione **dados**, em seguida, selecione **conjunto de dados** no painel central.  
  
3.  Escolha **Adicionar**.  
  
     O Visual Studio adiciona um arquivo chamado **dataSet1** ao projeto e abre-na **Dataset Designer**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Adicionando uma nova DataTable para o conjunto de dados  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Para adicionar uma nova tabela de dados para o conjunto de dados  
  
1.  Arraste um **DataTable** do **conjunto de dados** guia do **caixa de ferramentas** até o **Dataset Designer**.  
  
     Uma tabela denominada **DataTable1** é adicionado ao conjunto de dados.  
   
2.  Clique na barra de título do **DataTable1** e renomeie- `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Adicionando colunas à tabela de dados  
  
#### <a name="to-add-columns-to-the-data-table"></a>Para adicionar colunas à tabela de dados  
  
1.  Clique com botão direito do **música** tabela. Aponte para **adicionar**e, em seguida, clique em **coluna**.  
  
2.  Nome da coluna `SongID`.  
  
3.  No **propriedades** janela, defina o <xref:System.Data.DataColumn.DataType%2A> propriedade <xref:System.Int16?displayProperty=fullName>.  
  
4.  Repita este processo e adicione as seguintes colunas:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Definindo a chave primária da tabela  
Todas as tabelas de dados devem ter uma chave primária. Uma chave primária identifica exclusivamente um registro específico em uma tabela de dados.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Para definir a chave primária da tabela de dados  
  
-   Clique com botão direito do **SongID** coluna e clique **definir chave primária**.  
  
     Um ícone de chave aparece ao lado de **SongID** coluna.  
  
## <a name="saving-your-project"></a>Salvando seu projeto  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Para salvar o projeto DataTableWalkthrough  
  
-   Sobre o **arquivo** menu, clique em **Salvar tudo**.  
  
## <a name="see-also"></a>Consulte também
[Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validando dados](../data-tools/validate-data-in-datasets.md)   
[Salvando dados](../data-tools/saving-data.md)   