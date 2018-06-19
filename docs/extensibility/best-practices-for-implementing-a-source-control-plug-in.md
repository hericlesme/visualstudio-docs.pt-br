---
title: Práticas recomendadas para implementar um plug-in de controle de origem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5e9972b28d435f5cba360b2328ecdd6d18eb52e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106042"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Práticas recomendadas para implementar um plug-in de controle de origem
Os seguintes detalhes técnicos podem ajudá-lo a implementar com segurança um plug-in de controle de origem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemas de gerenciamento de memória  
 Na maioria dos casos, o ambiente de desenvolvimento integrado (IDE), que é o chamador, libera e aloca memória. O plug-in de controle de origem retorna cadeias de caracteres e outros itens em buffers alocada pelo chamador. Exceções serão indicadas nas descrições de funções específicas em que eles ocorrem.  
  
## <a name="arrays-of-file-names"></a>Matrizes de nomes de arquivo  
 Quando uma matriz de arquivos for passada, ela não é passada como uma matriz de contígua de nomes de arquivo. Ele é passado como uma matriz de ponteiros para nomes de arquivo. Por exemplo, no [SccGet](../extensibility/sccget-function.md), os nomes de arquivo são transmitidos pelo `lpFileNames` parâmetro, onde `lpFileNames` é, na verdade, um ponteiro para um `char **`. `lpFileNames`[0] é um ponteiro para o nome, `lpFileNames`[1] é um ponteiro para o nome do segundo e assim por diante.  
  
## <a name="large-model"></a>Modelos grandes  
 Todos os ponteiros são de 32 bits, mesmo em sistemas operacionais de 16 bits.  
  
## <a name="fully-qualified-paths"></a>Caminhos totalmente qualificados  
 Onde os nomes de arquivos ou diretórios são especificados como argumentos, eles devem ser caminhos totalmente qualificados ou caminhos UNC, sem as barras invertidas finais. É responsabilidade do controle de origem de plug-in para converter esses caminhos relativos se isto é um requisito do sistema de controle de origem subjacente.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique um caminho totalmente qualificado para a DLL registrada  
 O IDE não carrega DLLs de caminhos relativos (por exemplo,.\NewProvider.dll). Especifique um caminho completo da DLL (por exemplo, C:\Providers\NewProvider.dll). Esse requisito reforça a segurança do IDE, impedindo que o carregamento do controle de origem não autorizado ou representado DLLs.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificar se há um plug-in de VSSCI existente quando você instalar o plug-in de controle de origem  
 Um usuário que planeja instalar o plug-in de controle de origem talvez já tenha um fonte controle existente plug-in instalado no computador. O programa de instalação (instalação) para o plug-in que você criar deve determinar se há valores existentes para as chaves do Registro relevantes. Se essas chaves já estiverem definidas, o programa de instalação deve pedir ao usuário se deseja registrar o plug-in como plug-in de controle de origem padrão e substituir aquele que já está instalado.  
  
## <a name="error-result-codes-and-reporting"></a>Códigos de resultado de erro e a emissão de relatórios  
 O `SCC_OK` retornam o código para uma função de controle do código-fonte indica que a operação teve êxito para todos os arquivos. Se a operação falhar, ele deve retornar o último código de erro.  
  
 A regra para emissão de relatórios é que, se ocorrer um erro no IDE, o IDE é responsável por relatá-las. Se ocorrer um erro no sistema de controle de origem, o plug-in de controle de origem é responsável por relatá-las. Por exemplo, "não há arquivos selecionados no momento" seriam relatado pelo IDE, enquanto "Este arquivo já foi extraído" seria relatado pelo plug-in.  
  
## <a name="the-context-structure"></a>A estrutura de contexto  
 Durante a chamada para o [SccInitialize](../extensibility/sccinitialize-function.md), a chamador passa o `ppvContext` parâmetro, que é um identificador não inicializado para um nulo. O plug-in de controle de origem pode ignorar esse parâmetro ou pode alocar uma estrutura de qualquer tipo e colocar um ponteiro para a estrutura no passado ponteiro. O IDE não compreende essa estrutura, mas ele passa um ponteiro para esta estrutura em todas as outras chamadas de plug-in. Isso fornece informações de cache de contexto importantes para o plug-in que ele pode usar para manter informações de estado global que persiste nas chamadas de função sem usar variáveis globais. O plug-in é responsável pela liberação de estrutura em uma chamada para o [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Se os conjuntos de plug-in de `SCC_CAP_REENTRANT` bit no [SccInitialize](../extensibility/sccinitialize-function.md) (especificamente, no `lpSccCaps` parâmetro), várias estruturas de contexto são usadas para controlar todos os projetos que estão abertos.  
  
## <a name="bitflags-and-other-command-options"></a>Os sinalizadores de bit e outras opções de comando  
 Para cada comando, como o [SccGet](../extensibility/sccget-function.md), o IDE pode especificar várias opções que alteram o comportamento do comando.  
  
 A API dá suporte para a configuração de determinadas opções pelo IDE por meio de `fOptions` parâmetro. Essas opções são descritas em [os sinalizadores de bit usados por comandos específicos](../extensibility/bitflags-used-by-specific-commands.md) junto com os comandos que afetam a eles. Em geral, estas são opções para os quais o usuário não será avisado.  
  
 Opções de configuração mais configurável pelo usuário não estão definidas dessa maneira, porque eles variam amplamente entre plug-ins de controle de origem. Portanto, o mecanismo recomendado é um **avançado** botão. Por exemplo, no **obter** caixa de diálogo, o IDE exibe apenas as informações que ele entenda, mas ela também exibe um **avançado** botão se o plug-in tem opções para este comando. Quando o usuário clica o **avançado** botão, o IDE chama o [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) para habilitar o plug-in para solicitar ao usuário para obter informações, como os sinalizadores de bit ou um valor de data/hora de controle de origem. O plug-in retorna essas informações em uma estrutura que é passada durante a `SccGet` comando.  
  
## <a name="see-also"></a>Consulte também  
 [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)   
 [Criar um plug-in de controle do código-fonte](../extensibility/internals/creating-a-source-control-plug-in.md)