---
title: Descrição do modelo do diretório (. Arquivos Vsdir) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14ea2e0bcc11324e6529c70c04c11874ec4a3399
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133982"
---
# <a name="template-directory-description-vsdir-files"></a>Descrição do modelo do diretório (. Arquivos de Vsdir)
Um arquivo de descrição de pasta do modelo (.vsdir) é um arquivo de texto que permite que o ambiente de desenvolvimento integrado (IDE) para exibir pastas, arquivos. vsz do assistente e os arquivos de modelo que estão associados ao seu projeto em caixas de diálogo. O conteúdo inclui um registro por arquivo ou pasta. Todos os arquivos .vsdir em um local de referência são mesclados, embora .vsdir apenas um arquivo geralmente é fornecido para descrever as várias pastas, assistentes ou arquivos de modelo.  
  
 Pastas (subpastas), arquivos que são referenciadas no arquivo .vsdir e o próprio arquivo .vsdir estão localizadas no mesmo diretório. Quando o IDE executa um assistente ou exibe uma pasta ou arquivo de **novo projeto** ou **Adicionar Novo Item** caixas de diálogo, o IDE examina o diretório que contém os arquivos executados para determinar se é um arquivo .vsdir presente. Se um arquivo .vsdir for encontrado, o IDE lê-lo para determinar se ele contém uma entrada para o arquivo ou pasta exibida ou executada. Se uma entrada for encontrada, o IDE usa as informações na exibição do conteúdo ou da execução do assistente.  
  
 O exemplo de código a seguir é do arquivo SourceFiles.vsdir no \<EnvSDK > \BscPrj\BscPrj\BscPrjProjectItems\Source_Files chave de registro:  
  
```  
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127  
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124  
```  
  
 Nesse caso, os dois registros estão em um arquivo. Uma nova linha (caractere de retorno de carro) separa cada registro. Cada linha representa um tipo de arquivo diferente. Um pipe (&#124;) caractere que separa os campos em cada registro. Um único diretório pode conter vários arquivos .vsdir com nomes de arquivo diferentes, ou você pode ter um arquivo de .vsdir para cada tipo de arquivo.  
  
## <a name="fields"></a>Campos  
 A tabela a seguir lista os campos especificados para cada registro.  
  
|Campo|Descrição|  
|-----------|-----------------|  
|Nome de caminho relativo (RelPathName)|O nome do arquivo. vsz, modelo ou pasta, como HeaderFile.h ou MyWizard.vsz. Este campo também pode ser um nome usado para representar uma pasta.|  
|{clsidPackage}|O GUID do VSPackage que permite o acesso às cadeias de caracteres localizadas, como LocalizedName, descrição, IconResourceId e SuggestedBaseName, em recursos de biblioteca (DLL) de vínculo dinâmico do VSPackage satélite. IconResourceId se aplica se DLLPath não for fornecido. **Observação:** esse campo é opcional, a menos que um ou mais dos campos anteriores é um identificador de recurso. Este campo é normalmente em branco para .vsdir arquivos que correspondem aos assistentes de terceiros que não localizar o texto.|  
|LocalizedName|O nome localizado do arquivo de modelo ou assistente. Este campo pode ser uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". Esse nome é exibido no **Adicionar Novo Item** caixa de diálogo. **Observação:** se LocalizedName é um identificador de recurso, {clsidPackage} é necessária.|  
|SortPriority|Um inteiro que representa a prioridade relativa desse arquivo de modelo ou o assistente. Por exemplo, se este item tem um valor de 1, esse item é exibido ao lado de outros itens com um valor de 1 e à frente de todos os itens com um valor de classificação 2 ou maior.<br /><br /> Prioridade de classificação é relativo aos itens no mesmo diretório. Pode haver mais de um arquivo de .vsdir no mesmo diretório. Nesse caso, os itens de todos os *.* vsdir arquivos nesse diretório são mesclados. Itens com a mesma prioridade são listados em ordem lexicográfica maiusculas e minúsculas do nome exibido. O `_wcsicmp` função é usada para ordenar os itens.<br /><br /> Itens não descritos no .vsdir arquivos incluem um número de prioridade maior do que o número de prioridade mais alto listado nos arquivos .vsdir. O resultado é que esses itens estão no final da lista exibida, independentemente de seu nome.|  
|Descrição|A descrição localizada do arquivo de modelo ou assistente. Este campo pode ser uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". Essa cadeia de caracteres aparece no **novo projeto** ou **Adicionar Novo Item** caixa de diálogo quando o item é selecionado.|  
|DLLPath ou {clsidPackage}|Usado para carregar um ícone para o assistente ou um arquivo de modelo. O ícone é carregado como um recurso fora de um arquivo. dll ou .exe usando o IconResourceId. Esse arquivo. dll ou .exe pode ser identificado usando um caminho completo ou usando um GUID de um VSPackage. A implementação da DLL do VSPackage é usada para carregar o ícone (não o DLL satélite).|  
|IconResourceId|O identificador de recurso na implementação de DLL ou VSPackage DLL que determina o ícone a ser exibido.|  
|Sinalizadores (<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>)|Usado para habilitar ou desabilitar o **nome** e **local** campos de **Adicionar Novo Item** caixa de diálogo. O valor de **sinalizadores** campo é o equivalente decimal da combinação de sinalizadores de bit necessário.<br /><br /> Quando um usuário seleciona um item no **novo** guia, o projeto determina se o campo de nome e o campo de local são mostrados quando o **Adicionar Novo Item** caixa de diálogo é exibida pela primeira vez. Um item, por meio de um arquivo de .vsdir, pode controlar somente se os campos estão habilitados versus desabilitado quando o item é selecionado.|  
|SuggestedBaseName|Representa o nome padrão para o arquivo, o assistente ou o modelo. Este campo é uma cadeia de caracteres ou um identificador de recurso do formulário "#ResID". O IDE usa esse valor para fornecer um nome padrão para o item. Esse valor base é acrescentado com um valor inteiro para tornar o nome exclusivo, como MyFile21.asp.<br /><br /> Na lista anterior, descrição, DLLPath, IconResourceId, sinalizadores e SuggestedBaseNumber aplicam-se somente a arquivos de modelo e o assistente. Esses campos não se aplicam às pastas. Esse fato é ilustrado no código no arquivo de BscPrjProjectItems o \<EnvSDK > chave de registro \BscPrj\BscPrj\BscPrjProjectItems. Este arquivo contém três registros (uma para cada pasta) com quatro campos para cada registro: RelPathName, {clsidPackage} LocalizedName e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120`|  
  
 Quando você cria um arquivo do assistente, você também deve considerar os problemas a seguir.  
  
-   Qualquer campo não é necessário para o qual não há nenhum dado significativo deve conter um 0 (zero) como um espaço reservado.  
  
-   Se nenhum nome localizado for fornecido, o nome de caminho relativo é usado no arquivo de assistente.  
  
-   DLLPath substitui clsidPackage para a localização do ícone.  
  
-   Se nenhum ícone for definida, o IDE substitui o ícone padrão para um arquivo que tem a extensão.  
  
-   Se nenhum nome de base sugerido for fornecido, 'Project' será usado.  
  
-   Se você excluir os arquivos. vsz, pastas ou arquivos de modelo, você também deve remover os registros associados do arquivo .vsdir.  
  
## <a name="see-also"></a>Consulte também  
 [Assistentes](../../extensibility/internals/wizards.md)   
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)