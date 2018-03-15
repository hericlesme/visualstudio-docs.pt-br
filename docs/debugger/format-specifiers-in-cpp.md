---
title: Formatar especificadores no depurador (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b7efb90e6f2a2489fffb890c664393252021e6f
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Especificadores de formato em C++ no depurador do Visual Studio
Você pode alterar o formato no qual um valor é exibido no **inspecionar** janela usando especificadores de formato.  
  
 Você também pode usar os especificadores de formato no **imediato** janela, o **comando** janela, na [pontos de rastreamento](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e até mesmo no windows de origem. Se você pausar em uma expressão nessas janelas, o resultado é exibido em um DataTip. A exibição de DataTip reflete o especificador de formato.  
  
> [!NOTE]
>  Quando o depurador nativo do Visual Studio é alterado para um novo mecanismo de depuração, alguns especificadores de formato novos foram adicionados e alguns antigos foram removidos. O depurador mais antigo ainda é usado quando você fizer a interoperabilidade (misto nativo e gerenciado) de depuração com C + + CLI. As seções a seguir neste tópico mostram os especificadores de formato para cada mecanismo de depuração.
>   
>  -   [Especificadores de formato](#BKMK_Visual_Studio_2012_format_specifiers) descreve os especificadores de formato em que o novo mecanismo de depuração.  
> -   [Especificadores de formato para depuração interop com C + + CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) descreve os especificadores de formato no mecanismo de depuração mais antigo.  
  
## <a name="using-format-specifiers"></a>Usando especificadores de formato  
 Se você tiver o seguinte código:  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Adicionar o `my_var1` variável para o **inspecionar** janela (durante a depuração, **Depurar > Windows > Observação > inspecionar 1**) e, em seguida, defina a exibição em hexadecimal (no **Assista**janela, a variável e selecione **exibição Hexadecimal**). Agora, a janela Inspeção mostra que ele contém o valor 0x0065. Para ver esse valor, expresso como um caractere em vez de um número inteiro, na coluna Nome, após o nome da variável, adicione o especificador de formato de caractere **, c**. O **valor** coluna agora aparece **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Especificadores de formato  
 As tabelas a seguir mostram os especificadores de formato que você pode usar no Visual Studio. Não há suporte para especificadores em negrito para depuração interop com C + + CLI.  
  
|Especificador|Formatar|Valor original de inspeção|Valor exibido|  
|---------------|------------|--------------------------|---------------------|  
|d|inteiro decimal|0x00000066|102|  
|o|inteiro octal não assinado|0x00000066|000000000146|  
|x<br /><br /> **h**|inteiro hexadecimal|102|0xcccccccc|  
|X<br /><br /> **H**|inteiro hexadecimal|102|0xCCCCCCCC|  
|c|caractere único|0x0065, c|101 'e'|  
|s|Const char * de cadeia de caracteres|\<local > "Olá, mundo"|"hello world"|  
|**sb**|Const char * cadeia de caracteres (sem aspas)|\<local > "Olá, mundo"|Olá, mundo|  
|s8|Cadeia de caracteres UTF-8|\<local > "Este é um â˜• de xícara de café UTF-8"|"Este é um ☕ de xícara de café UTF-8"|
|**s8b**|Cadeia de caracteres UTF-8 (sem aspas)|\<local > "Olá, mundo"|Olá, mundo|  
|su|Cadeia de caracteres Unicode (codificação UTF-16)|\<local > L "hello world"|L "hello world"<br /><br /> U "hello world"|  
|sub|Cadeia de caracteres Unicode (codificação UTF-16) (sem aspas)|\<local > L "hello world"|Olá, mundo|  
|bstr|Cadeia de caracteres BSTR|\<local > L "hello world"|L "hello world"|  
|env|Bloco de ambiente (cadeia de caracteres nula duplo encerrado)|\<location> L"=::=::\\\\"|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Cadeia de caracteres UTF-32|\<local > U "hello world"|U "hello world"|  
|**s32b**|Cadeia de caracteres UTF-32 (sem aspas)|\<local > U "hello world"|Olá, mundo|  
|**en**|enum|Saturday(6)|Sábado|  
|**hv**|Tipo de ponteiro - indica que o valor do ponteiro sendo inspecionado é o resultado da alocação de heap de uma matriz, por exemplo, `new int[3]`.|\<local > {\<primeiro membro >}|\<local > {\<primeiro membro >, \<segundo membro >,...}|  
|**na**|Suprime o endereço de memória de um ponteiro para um objeto.|\<local >, {membro = valor...}|{membro = valor...}|  
|**nd**|Exibe apenas as informações de classe base, ignorando as classes derivadas|`(Shape*) square` inclui a classe base e derivadas informações de classe|Exibe somente informações de classe de base|  
|hr|Código de erro HRESULT ou Win32. (O depurador agora decodifica HRESULTs automaticamente. Portanto, esse especificador não é necessário nesses casos.|S_OK|S_OK|  
|wc|Sinalizador de classe de janela|0x0010|WC_DEFAULTCHAR|  
|wm|Números de mensagens do Windows|16|WM_CLOSE|  
|!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\<personalizado representação >|4|  
  
> [!NOTE]
>  Quando o **hv** especificador de formato estiver presente, o depurador tenta determinar o comprimento do buffer e exibir o número apropriado de elementos. Como nem sempre é possível para o depurador encontrar o tamanho do buffer exata de uma matriz, você deve usar um especificador de tamanho `(pBuffer,[bufferSize])` sempre que possível. O **hv** especificador de formato é destinado a cenários de onde o tamanho do buffer não está disponível  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Especificadores de tamanho para ponteiros como matrizes  
 Se você tiver um ponteiro para um objeto que queira exibir como uma matriz, pode usar um inteiro ou uma expressão para especificar o número de elementos da matriz:  
  
|Especificador|Formatar|Valor original de inspeção|Valor exibido|  
|---------------|------------|---------------------------|---------------------|  
|n|Decimal ou **hexadecimal** inteiro|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Exibe `pBuffer` como uma matriz de elementos de 32.|  
|**[exp]**|Uma expressão C++ válida que é avaliada como um inteiro.|pBuffer,[bufferSize]|Exibe pBuffer como uma matriz de `bufferSize` elementos.|  
|**expand(n)**|Uma expressão válida de C++ que é avaliada como um número inteiro|pBuffer, expand(2)|Exibe o terceiro elemento de  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Especificadores de formato para depuração interop com C + + CLI  
 Especificadores em **negrito** só há suporte para depuração nativa e C + + código.  
  
|Especificador|Formatar|Valor original de inspeção|Valor exibido|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|inteiro decimal assinado|0xF000F065|-268373915|  
|**u**|inteiro decimal não assinado|0x0065|101|  
|o|inteiro octal não assinado|0xF065|0170145|  
|x,X|Inteiro hexadecimal|61541|0x0000f065|  
|**l, h**|prefixo longo ou curto para: d, i, u, o, x, X|00406042|0x0c22|  
|**f**|ponto flutuante assinado|(3./2.), f|1.500000|  
|**e**|notação científica assinada|(3.0/2.0)|1.500000e+000|  
|**g**|ponto flutuante assinado ou notação científica assinada, o que for menor|(3.0/2.0)|1.5|  
|c|caractere único|\<location>|101 'e'|  
|s|Const char *|\<location>|"hello world"|  
|su|wchar_t const *<br /><br /> char16_t const\*|\<location>|L "hello world"|  
|sub|wchar_t const *<br /><br /> char16_t const\*|\<location>|Olá, mundo|  
|s8|Const char *|\<location>|"hello world"|  
|hr|Código de erro HRESULT ou Win32. (O depurador agora decodifica HRESULTs automaticamente. Portanto, esse especificador não é necessário nesses casos.|S_OK|S_OK|  
|wc|Sinalizador de classe do Windows.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Números de mensagens do Windows|0x0010|WM_CLOSE|  
|!|formato bruto, ignorando qualquer personalização de exibições de tipo de dados|\<personalizado representação >|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Formatar locais da memória especificadores em depuração interop com C + + CLI  
 A tabela a seguir contém os símbolos de formatação usados para locais de memória. Você pode usar um especificador de local da memória com qualquer valor ou expressão que seja avaliada como um local.  
  
|Símbolo|Formatar|Valor original de inspeção|Valor exibido|  
|------------|------------|--------------------------|---------------------|  
|**ma**|Caracteres ASCII na base 64|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 bytes em hexadecimal, seguidos caracteres ASCII na base 16|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 bytes em hexadecimal, seguidos caracteres ASCII na base 16|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 palavras|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 palavra duplas|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 palavras quádruplas|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|Caracteres de 2 bytes (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Especificador de tamanho para ponteiros como matrizes em depuração interop com C + + CLI  
 Se você tiver um ponteiro para um objeto que você deseja exibir como uma matriz, pode usar um inteiro para especificar o número de elementos da matriz:  
  
|Especificador|Formatar|Expressão|Valor exibido|  
|---------------|------------|----------------|---------------------|  
|n|Inteiro decimal|pBuffer[32]|Exibe `pBuffer` como uma matriz de elementos de 32.|
