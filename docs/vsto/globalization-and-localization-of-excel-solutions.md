---
title: "Globalização e localização de soluções do Excel | Microsoft Docs"
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
helpviewer_keywords: globalization [Office development in Visual Studio], configuring
ms.assetid: c5fccd45-cb3a-441c-89bf-257e9faf4587
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ac0fc1ca0efe4134889d8bf5ac1d3ca9ae2551ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Globalização e localização de soluções do Excel
  Esta seção contém informações sobre considerações especiais para soluções do Microsoft Office Excel que serão executadas em computadores que têm configurações diferentes do inglês do Windows. A maioria dos aspectos de globalização e localização de soluções do Microsoft Office são os mesmos encontrados ao criar outros tipos de soluções usando o Visual Studio. Para obter informações gerais, consulte [Globalizing e Localizando aplicativos](/visualstudio/ide/globalizing-and-localizing-applications).  
  
 Por padrão, os controles de host no trabalho do Microsoft Office Excel corretamente em qualquer configuração regional do Windows, desde que todos os dados que são passados ou manipulado usando o código gerenciado é formatado usando formatação de texto para inglês (Estados Unidos). Em projetos direcionados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], esse comportamento é controlado pelo common language runtime (CLR).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="formatting-data-in-excel-with-various-regional-settings"></a>Formatação de dados no Excel com várias configurações regionais  
 Você deve formatar todos os dados com formatação de distinção de localidade, como datas e moeda, usando o formato de dados de inglês (Estados Unidos) (1033 ID de localidade) antes de passá-lo para o Microsoft Office Excel ou ler os dados do código em seu projeto do Office.  
  
 Por padrão, quando você desenvolver uma solução do Office no Visual Studio, o modelo de objeto do Excel espera a formatação de dados com a localidade 1033 ID (Isso também é chamado o modelo de objeto para a localidade 1033 ID de bloqueio). Visual Basic for Applications funciona de maneira que corresponde a esse comportamento. No entanto, você pode modificar esse comportamento em suas soluções do Office.  
  
### <a name="understanding-how-the-excel-object-model-always-expects-locale-id-1033"></a>Noções básicas sobre como o modelo de objeto do Excel sempre espera que a ID de localidade 1033  
 Por padrão, as soluções do Office que você cria usando o Visual Studio não são afetadas pelas configurações de localidade do usuário final e sempre se comportam como se a localidade é inglês (Estados Unidos). Por exemplo, se você obter ou definir o <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriedade no Excel, os dados deve ser formatada da maneira que a ID de localidade 1033 espera. Se você usar um formato de dados diferentes, você pode obter resultados inesperados.  
  
 Mesmo que você use o formato de inglês (Estados Unidos) de dados que são passados ou manipulados pelo código gerenciado, o Excel interpreta e exibe os dados corretamente de acordo com configuração de localidade do usuário final. Excel pode formatar os dados corretamente porque o código gerenciado passa o formato da localidade 1033 ID junto com os dados, o que indica que os dados estão em inglês (Estados Unidos) e, portanto, deve ser reformatado para coincidir com a configuração de localidade do usuário.  
  
 Por exemplo, se os usuários finais tenham suas opções regionais definidas para a localidade alemão (Alemanha), esperam que a data de 29 de junho de 2005 a ser formatada assim: 29.06.2005. No entanto, se sua solução passa a data para o Excel como uma cadeia de caracteres, você deve formatar a data de acordo com o formato inglês (Estados Unidos): 29/6/2005. Se a célula é formatada como uma célula de data, o Excel exibirá a data no formato alemão (Alemanha).  
  
### <a name="passing-other-locale-ids-to-the-excel-object-model"></a>Passando outras IDs de localidade para o modelo de objeto do Excel  
 O common language runtime (CLR) passa automaticamente localidade 1033 ID para todos os métodos e propriedades no modelo de objeto do Excel que aceitam dados sensíveis à localidade. Não é possível alterar esse comportamento automaticamente para todas as chamadas para o modelo de objeto. No entanto, você pode passar uma ID de localidade diferentes para um método específico usando <xref:System.Type.InvokeMember%2A> para chamar o método e passando a ID de localidade para o *cultura* parâmetro do método.  
  
## <a name="localizing-document-text"></a>Localizando o texto do documento  
 O documento, modelo ou pasta de trabalho em seu projeto provavelmente inclui texto estático, o que deve ser localizados separadamente do assembly e outros recursos gerenciados. Uma maneira simples de fazer isso é fazer uma cópia do documento e traduzir o texto usando o Microsoft Office Word ou o Microsoft Office Excel. Esse processo funciona mesmo que você não faça nenhuma alteração no código, porque qualquer número de documentos pode ser vinculado ao mesmo assembly.  
  
 Você ainda deve verificar se que qualquer parte do código que interage com o texto do documento continua corresponder ao idioma do texto e que indicadores, intervalos nomeados, e outros campos de exibição acomodar qualquer reformatação do documento do Office que era necessário ajuste de comprimento diferente de gramática e texto. Para modelos de documento que contêm relativamente pequeno texto, você talvez queira armazenar o texto em arquivos de recurso e, em seguida, carregar o texto em tempo de execução.  
  
### <a name="text-direction"></a>Direção do texto  
 No Excel, você pode definir uma propriedade da planilha para processar o texto da direita para esquerda. Hospedar controles ou qualquer controle que possui um `RightToLeft` propriedade, que são colocados automaticamente no designer de corresponder a essas configurações em tempo de execução. O Word não tem uma configuração de documento de texto bidirecional (você apenas alterar o alinhamento de texto), para que os controles não podem ser mapeados para essa configuração. Em vez disso, você deve definir o alinhamento do texto para cada controle. É possível escrever código para percorrer a todos os controles e forçá-los para processar o texto da direita para esquerda.  
  
### <a name="changing-culture"></a>Alteração de cultura  
 O código de personalização de nível de documento normalmente compartilha o thread de interface do usuário principal do Excel, para que as alterações feitas para a cultura do thread afeta tudo que está em execução no thread; a alteração não está restrita a sua personalização.  
  
 Controles de formulários do Windows são inicializados antes que o nível de aplicativo suplementos do VSTO são iniciados pelo aplicativo host. Nessas situações, a cultura deve ser alterada antes de configurar os controles de interface do usuário.  
  
## <a name="installing-the-language-packs"></a>Instalando os pacotes de idiomas  
 Se você tiver configurações diferentes do inglês do Windows, você pode instalar o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pacotes de idiomas para ver [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] mensagens no mesmo idioma do Windows. Se todos os usuários finais executar suas soluções com configurações diferentes do inglês do Windows, eles devem ter o pacote de idioma correto para ver mensagens de tempo de execução no mesmo idioma, como Windows. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pacotes de idiomas estão disponíveis a [Microsoft Download Center](http://www.microsoft.com/downloads).  
  
 Além disso, os pacotes de idioma redistribuível do .NET Framework são necessários para mensagens de ClickOnce. Os pacotes de idiomas do .NET Framework estão disponíveis a partir de [Microsoft Download Center](http://www.microsoft.com/downloads).  
  
## <a name="regional-settings-and-excel-com-calls"></a>As configurações regionais e chamadas do Excel COM  
 Sempre que um cliente gerenciado chama um método em um objeto COM, e ele precisa transmitir informações específicas de cultura, ele faz isso usando o <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (local) que corresponde a localidade do thread atual. Por padrão, a localidade do thread atual é herdada das configurações regionais do usuário. No entanto, quando você faz uma chamada para o modelo de objeto do Excel em uma solução do Excel criada usando as ferramentas de desenvolvimento do Office no Visual Studio, o formato de dados de inglês (Estados Unidos) (1033 ID de localidade) é passado para o modelo de objeto do Excel automaticamente. Você deve formatar todos os dados com formatação de distinção de localidade, como datas e moeda, usando o formato de dados do inglês (Estados Unidos) antes de passá-lo para o Microsoft Office Excel ou ler os dados do seu código de projeto.  
  
## <a name="considerations-for-storing-data"></a>Considerações para o armazenamento de dados  
 Para garantir que os dados corretamente interpretados e exibidos, você também deve considerar que podem ocorrer problemas quando um aplicativo está armazenando dados, como fórmulas de planilha do Excel, em literais de cadeia de caracteres (embutidos) em vez de em objetos fortemente tipados. Você deve usar dados formatados supondo que um estilo de cultura invariável ou inglês (Estados Unidos) (valor LCID 1033).  
  
### <a name="applications-that-use-string-literals"></a>Aplicativos que usam literais de cadeia de caracteres  
 Os valores possíveis que podem ser embutidos incluem literais de data que são gravados no formato inglês (Estados Unidos) e fórmulas de planilha do Excel que contêm nomes de função localizadas. Outra possibilidade pode ser uma cadeia de caracteres codificada que contém um número, como "1.000"; em algumas culturas, isso é interpretado como mil, mas em outras culturas, ela representa um ponto de zero. Cálculos e comparações executadas em um formato incorreto podem resultar em dados incorretos.  
  
 O Excel interpreta cadeias de acordo com o LCID que é transmitido com a cadeia de caracteres. Isso pode ser um problema se o formato da cadeia de caracteres não corresponde ao LCID que é passado. Soluções do Excel criadas usando as ferramentas de desenvolvimento do Office no Visual Studio usam o LCID 1033 (en-US) ao passar todos os dados. O Excel exibe os dados de acordo com as configurações regionais e idiomas de interface de usuário do Excel. Visual Basic for Applications (VBA) também funciona dessa maneira. cadeias de caracteres são formatadas como en-US e VBA quase sempre passa 0 (neutralidade de idioma) como o LCID. Por exemplo, o código VBA a seguir exibe um valor formatado corretamente para 12 de maio de 2004, conforme a configuração de localidade do usuário atual:  
  
```  
'VBA  
Application.ActiveCell.Value2 = "05/12/04"  
```  
  
 O mesmo código, quando usado em uma solução criada usando as ferramentas de desenvolvimento do Office no Visual Studio e passados para o Excel interoperabilidade COM, produz os mesmos resultados quando a data é formatada em estilo de en-US.  
  
 Por exemplo:  
  
 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]  
  
 Você deve trabalhar com dados fortemente tipada em vez de literais de cadeia de caracteres sempre que possível. Por exemplo, em vez de armazenar uma data em uma cadeia de caracteres literal, armazená-lo como um <xref:System.Double>, convertê-lo para um <xref:System.DateTime> objeto para manipulação.  
  
 O exemplo de código a seguir usa uma data em que um usuário insere na célula A5, armazena-o como um <xref:System.Double>, em seguida, converte-o para um <xref:System.DateTime> objeto para exibição na célula A7. A7 da célula deve ser formatada para exibir uma data.  
  
 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]  
  
### <a name="excel-worksheet-functions"></a>Funções de planilha do Excel  
 Nomes de função de planilha são convertidos internamente para a maioria das versões de idioma do Excel. No entanto, devido a problemas de interoperabilidade COM e de idioma potencial é altamente recomendável que você use nomes de função apenas em inglês no seu código.  
  
### <a name="applications-that-use-external-data"></a>Aplicativos que usam dados externos  
 Qualquer código que é aberta ou caso contrário usa dados externos, como arquivos que incluem valores separados por vírgula (arquivos CSV) exportados de um sistema herdado, também poderão ser afetado se esses arquivos são exportados usando qualquer formato além de en-US. Acesso de banco de dados não pode ser afetado porque todos os valores devem estar no formato binário, a menos que o banco de dados armazena datas como cadeias de caracteres ou executa operações que não usam o formato binário. Além disso, se você construir consultas SQL que usam dados do Excel, você precisará garantir que estejam no formato de en-US, dependendo da função que você usar.  
  
## <a name="see-also"></a>Consulte também  
 [Como: destinar a Interface de usuário multilíngue do Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Projetando e criando soluções do Office](../vsto/designing-and-creating-office-solutions.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  