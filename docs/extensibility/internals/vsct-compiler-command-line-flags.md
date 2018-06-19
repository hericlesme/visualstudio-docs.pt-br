---
title: Sinalizadores de linha de comando do compilador VSCT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6e2e1045adb451c7f4dd06b888fca356d26b7ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139767"
---
# <a name="vsct-compiler-command-line-flags"></a>Sinalizadores de linha de comando do compilador VSCT
O compilador de tabela de comando do Visual Studio (VSCT) fornece opções de linha de comando para garantir uma compilação bem-sucedida dos arquivos. VSCT.  
  
## <a name="command-line-parameters"></a>Parâmetros de linha de comando  
 Para exibir a Ajuda do VSCT básica de um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** janela, navegue até o *caminho de instalação do SDK do Visual Studio*\VisualStudioIntegration\Tools\Bin\ pasta e digite:  
  
```  
vsct /?  
```  
  
 Isso retorna:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  Os caracteres a-(traço) e / (barra) são ambas as notação aceitos para indicar parâmetros de linha de comando.  
  
 Sinalizadores aceitáveis e o que significam são da seguinte maneira.  
  
|Alternar|Descrição|  
|------------|-----------------|  
|-D|Especifique quaisquer símbolos definidos adicionais.|  
|-I|Indica que caminhos que devem ser usados ao resolver referências de arquivo de inclusão adicionais.|  
|-L|Especifique o <xref:System.Globalization.CultureInfo> nome de cultura, como "en-US".|  
|-E|Emitir c# objetos no namespace especificado para os itens de comando, seguido por [C&#124;H&#124;N]:*filename*onde C = c#, H = cabeçalho de C++, N = namespace. O namespace é necessário para c#.|  
|-v|Saída detalhada.|  
  
 A opção -L Instrui o compilador para selecionar um grupo de cadeias de caracteres para gerar o arquivo binário .cto que corresponde à determinado <xref:System.Globalization.CultureInfo> nome de cultura. O nome de cultura especificado deve corresponder o atributo de idioma de um ou mais [cadeias de caracteres elemento](../../extensibility/strings-element.md) no arquivo. VSCT. Se um elemento de cadeias de caracteres não tem nenhum atributo de idioma, ela é herdada do que o contém [CommandTable elemento](../../extensibility/commandtable-element.md).  
  
 Um arquivo. VSCT pode ter vários elementos de cadeias de caracteres, e cada um pode ter um atributo de idioma diferente. Globalização é obtida executando o compilador VSCT várias vezes e alterando a opção -L para cada nome de cultura.  
  
 Se o nome de cultura dado pela opção -L não coincide com o atributo de idioma de qualquer elemento de cadeias de caracteres, o compilador tenta corresponder o idioma e não a região. Por exemplo, se "en-US" não podem ser encontrado, o compilador tentará "en" em vez disso. Caso de falha, ele tentará a cultura atual do sistema operacional. Caso de falha, ele irá compilar o primeiro elemento de cadeias de caracteres que encontrar.  
  
 A opção -E pode ser usada para emitir um arquivo de cabeçalho C-style que contém os símbolos que são usados pela tabela de comando ou de emissão de um arquivo em c# que contém objetos para os símbolos de comando.  
  
 -D e - opções têm a sintaxe dos sinalizadores pré-processador C Cl.exe que têm o mesmo nome. -D definições que têm o formato X = Y são usadas para a expansão de baseado em XML \<definidas > testa `Condition` atributos. -I incluir caminhos são usados para resolver \<Include >, \<Extern > e \<Bitmap > referências do arquivo. Para obter mais informações, consulte o [referência de esquema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 O compilador do VSCT também pode descompilar um arquivo binário compilado anteriormente. Para fazer isso, forneça um arquivo binário para o \<infile >.   Se o arquivo binário foi gerado pelo compilador do VSCT, ele terá seus símbolos já inseridos e produzirá uma saída com os nomes simbólicos em uma \<símbolos > seção da saída. Se o binário foi gerado pelo compilador CTC, a saída vai conter os GUIDs e identificações reais. Se o arquivo de *.ctsym produzido por versões atuais do Ctc.exe estiver na mesma pasta que o arquivo binário de entrada, os símbolos serão carregados do arquivo e usados para saída.  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de comando do Visual Studio (. Arquivos de VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referência de esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)