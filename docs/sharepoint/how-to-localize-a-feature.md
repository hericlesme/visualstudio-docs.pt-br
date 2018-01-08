---
title: 'Como: localizar um recurso | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 03adaa74feacc82c5f63c1930f7dad63cc931433
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-localize-a-feature"></a>Como localizar uma funcionalidade
  Por padrão, descrições e títulos de recurso usam valores de cadeia de caracteres codificada. Para localizar o recurso título e descrição, substitua as cadeias de caracteres com expressões que referenciam recursos localizados.  
  
## <a name="localizing-a-feature"></a>Localizando um recurso  
  
#### <a name="to-localize-a-feature"></a>Para localizar um recurso  
  
1.  Em **Solution Explorer**, abra o menu de atalho para o **Feature1** nó e, em seguida, escolha **adicionar recurso do recurso**.  
  
2.  No **adicionar recurso** caixa de diálogo caixa, escolha **idioma invariável** da lista como a cultura para o arquivo de recurso do recurso de idioma padrão.  
  
3.  Repita a etapa anterior para cada idioma localizado, escolher os idiomas de sua preferência para o recurso localizado em arquivos de recurso.  
  
     Arquivos de recurso separado de recurso são criados: um para o idioma padrão e uma para cada localizado o idioma que você deseja dar suporte.  
  
4.  Abra cada arquivo de recurso no Editor de recursos e, em seguida, insira todas as IDs de cadeia de caracteres e seus valores.  
  
     Por exemplo, no arquivo de recurso do recurso padrão, insira uma ID de cadeia de caracteres de **título** com um valor de **título do recurso Meus**, e uma segunda cadeia de caracteres ID de **descrição** com um valor de **Minha descrição do recurso**. Para cada arquivo de recurso localizado, usar a mesma cadeia IDs usadas no recurso de recurso padrão, mas insira cadeias de caracteres localizadas para os valores.  
  
5.  Depois de inserir todos os valores de recursos, abra o menu de atalho para o recurso (por exemplo, Feature1.feature) e, em seguida, escolha **View Designer** para abrir o recurso no Designer de recursos.  
  
6.  Para localizar o **título** e **descrição** campos no recurso, use o seguinte formato para inserir valores nas caixas:  
  
     `$Resources:`*ID da cadeia de caracteres*  
  
     Por exemplo, digite $Resources:**título** no **título do recurso** caixa e $Resources:**descrição** no **descrição do recurso** caixa .  
  
     A cadeia de caracteres IDs deve corresponder os que são usados nos arquivos de recurso.  
  
7.  Escolha a tecla F5 para compilar e executar o aplicativo.  
  
8.  No SharePoint, abra o **ações do Site** menu, escolha **configurações de Site**e, em seguida, no **ações do Site** seção escolher o **gerenciar recursos de Site** link.  
  
9. No SharePoint, altere o idioma de exibição padrão.  
  
     O recurso localizado título e descrição exibida no aplicativo. Para exibir os recursos localizados, o servidor do SharePoint deve ter um pacote de idiomas instalado que corresponda a cultura do arquivo de recurso.  
  
## <a name="see-also"></a>Consulte também  
 [Localizando soluções do SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Como: adicionar um arquivo de recurso](../sharepoint/how-to-add-a-resource-file.md)   
 [Como: localizar marcação ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Como localizar código](../sharepoint/how-to-localize-code.md)  
  
  