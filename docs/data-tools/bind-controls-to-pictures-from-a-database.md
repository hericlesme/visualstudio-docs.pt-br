---
title: Vincular controles a imagens de um banco de dados | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 77d2780200fd8be7a42d396cdade39b271b04bae
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Vincular controles a imagens de um banco de dados
Você pode usar o **fontes de dados** janela para vincular uma imagem em um banco de dados a um controle em seu aplicativo. Por exemplo, você pode vincular uma imagem a um <xref:System.Windows.Controls.Image> controle em um aplicativo WPF, ou para um <xref:System.Windows.Forms.PictureBox> controle em um aplicativo do Windows Forms.  
  
Imagens em um banco de dados normalmente são armazenadas como matrizes de bytes. Itens a **fontes de dados** janela que são armazenadas como matrizes de bytes tem seu controle de tipo definido como **nenhum** por padrão, como matrizes de bytes podem conter qualquer coisa desde uma matriz de bytes para o arquivo executável de um aplicativo grande. Para criar um controle associado a dados para um item da matriz de bytes no **fontes de dados** janela que representa uma imagem, você deve selecionar o controle a ser criado.  
  
O procedimento a seguir supõe que o **fontes de dados** janela já está preenchida com um item que está associado à imagem. 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Para vincular uma imagem em um banco de dados a um controle  
  
1.  Certifique-se de que a superfície de design que você deseja adicionar o controle é aberta no WPF Designer ou no Designer de formulários do Windows.  
  
2.  No **fontes de dados** janela, expanda a tabela desejada, ou para exibir suas colunas ou propriedades do objeto.  
  
3.  Selecione a coluna ou propriedade que contém os dados de imagem e selecione um dos seguintes controles de sua lista de controle de lista suspensa:  
  
    -   Se o WPF designer estiver aberto, selecione **imagem**.  
  
    -   Se o designer de formulários do Windows é aberto, selecione **PictureBox**.  
  
    -   Como alternativa, você pode selecionar um controle diferente, que oferece suporte à associação de dados e que pode exibir imagens. Se o controle que você deseja usar não estiver na lista de controles disponíveis, você pode adicioná-lo à lista e, em seguida, selecione. Para obter mais informações, consulte [adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Consulte também
[Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)