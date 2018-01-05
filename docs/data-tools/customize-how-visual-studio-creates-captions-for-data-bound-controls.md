---
title: Personalizar como o Visual Studio cria legendas para controles associados a dados | Microsoft Docs
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 60d98d6b8cefc2f7fb7829d841001f92bd9063de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar como o Visual Studio cria legendas para controles associados a dados
Quando você arrasta itens do [janela fontes de dados](add-new-data-sources.md) para um designer, uma consideração especial entra em jogo: os nomes de coluna nos rótulos de legenda são reformatados em uma cadeia de caracteres mais legível quando duas ou mais palavras são encontradas concatenados. Você pode personalizar a maneira na qual esses rótulos são criados, definindo o **SmartCaptionExpression**, **SmartCaptionReplacement**, e **SmartCaptionSuffix** valores em o **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data Designers** chave do registro.  
  
> [!NOTE]
> Essa chave do registro não existe até que você criá-lo.  
  
Títulos inteligentes são controlados pela expressão regular inserida no valor da **SmartCaptionExpression** valor. Adicionando o **Data Designers** chave do Registro substitui a expressão regular do padrão que controla os rótulos de legenda. Para obter mais informações sobre expressões regulares, consulte [usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
A tabela a seguir descreve os valores do registro que controlam os rótulos de legenda.  
  
|Item do registro|Descrição|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|A expressão regular usada para fazer a correspondência de padrões.|  
|**SmartCaptionReplacement**|O formato para exibir quaisquer grupos correspondidos no **SmartCaptionExpression**.|  
|**SmartCaptionSuffix**|Uma cadeia de caracteres opcional para acrescentar ao final da legenda.|  
  
A tabela a seguir lista as configurações padrão interno para esses valores do registro.  
  
|Item do registro|Valor padrão|Explicação|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) &#124; _ +|Corresponde a um caractere minúsculo seguido por um caractere maiusculo ou um sublinhado.|  
|**SmartCaptionReplacement**|$1 $2|$1 representa quaisquer caracteres correspondidas no primeiro parênteses da expressão, e $2 representa quaisquer caracteres correspondidas no segundo parênteses. A substituição é a primeira correspondência, um espaço e, em seguida, a segunda correspondência.|  
|**SmartCaptionSuffix**|:|Representa um caractere acrescentado à cadeia de caracteres retornada. Por exemplo, se a legenda for `Company Name`, o sufixo torna`Company Name:`|  
  
> [!CAUTION]
> Você deve ser muito cuidado ao fazer qualquer coisa no Editor do registro. Faça backup do registro antes de editá-lo. Se você usar o Editor do Registro incorretamente, você poderá causar sérios problemas que talvez exijam a reinstalação do sistema operacional. A Microsoft não garante que os problemas causados por você usando o Editor do Registro incorretamente podem ser resolvidos. Use o Editor do Registro por sua conta e risco.  
>   
>  O seguinte artigo da Base de conhecimento contém instruções para fazer backup, editar e restaurar o registro: [descrição do registro do Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb;en-US; 256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Para modificar o comportamento de legenda inteligente da janela fontes de dados  
  
1.  Abra uma janela de comando clicando em **iniciar** e **executar**.  
  
2.  Tipo `regedit` no **executar** caixa de diálogo e clique em **Okey**.  
  
3.  Expanda o **HKEY_CURRENT_USER**, **Software*, **Microsoft**, **VisualStudio** nó.  
  
7.  Com o botão direito do **15.0** nó e criar um novo **chave** chamado `Data Designers`.  
  
8.  Com o botão direito do **Data Designers** nó e criar três novos valores de cadeia de caracteres:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. Clique com botão direito do **SmartCaptionExpression** valor e, em seguida, selecione **modificar**.  
  
12. Insira a expressão regular que você deseja o **fontes de dados** janela a ser usado.  
  
13. Clique com botão direito do **SmartCaptionReplacement** valor e, em seguida, selecione **modificar**.  
  
14. Insira a substituição de cadeia de caracteres formatada da maneira que você deseja exibir os padrões de correspondência em sua expressão regular.  
  
15. Clique com botão direito do **SmartCaptionSuffix** valor e, em seguida, selecione **modificar**.  
  
16. Insira qualquer caractere que você deseja exibir no final da legenda.  
  
    Na próxima vez que você arrasta itens do **fontes de dados** janela, os rótulos de legenda são criados usando os novos valores de registro fornecidos.  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>Para desativar o recurso de legenda inteligente  
  
1.  Abra uma janela de comando clicando em **iniciar** e **executar**.  
  
2.  Tipo `regedit` no **executar** caixa de diálogo e clique em **Okey**.  
  
3.  Expanda o **HKEY_CURRENT_USER**, **Software**, **Microsoft**, **VisualStudio** nó.  
  
7.  Com o botão direito do **15.0** nó e criar um novo **chave** chamado `Data Designers`.  
  
8.  Com o botão direito do **Data Designers** nó e criar três novos valores de cadeia de caracteres:

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. Clique com botão direito do **SmartCaptionExpression** item e selecione **modificar**.  
  
12. Digite `(.*)` para o valor. Isso fará a correspondência de cadeia de caracteres inteira.  
  
13. Clique com botão direito do **SmartCaptionReplacement** item e selecione **modificar**.  
  
14. Digite `$1` para o valor. Isso substitui a cadeia de caracteres com o valor correspondente, que é a cadeia de caracteres inteira, de modo que ela permanecerá inalterada.  
  
    Na próxima vez que você arrasta itens do **fontes de dados** janela, os rótulos de legenda são criados com legendas não modificadas.  
  
## <a name="see-also"></a>Consulte também  
[Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)