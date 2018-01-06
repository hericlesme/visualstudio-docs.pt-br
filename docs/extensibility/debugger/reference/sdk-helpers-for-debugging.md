---
title: "Auxiliares do SDK para depuração | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: "28"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b87756f52cb1506be30014331d63eec5d15beff4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sdk-helpers-for-debugging"></a>Auxiliares do SDK para depuração
Essas funções e as declarações são funções auxiliares global para implementar mecanismos de depuração, avaliadores de expressão e provedores de símbolo em C++.  
  
> [!NOTE]
>  Não há nenhum versões gerenciadas dessas funções e declarações neste momento.  
  
## <a name="overview"></a>Visão geral  
 Em ordem para mecanismos de depuração, avaliadores de expressão e provedores de símbolo a ser usado pelo Visual Studio, eles devem estar registrados. Isso é feito definindo subchaves do registro e entradas, também conhecidas como "métricas de configuração". As seguintes funções globais são projetadas para facilitar o processo de atualizar essas métricas. Consulte a seção sobre locais do registro para descobrir o layout de cada subchave do registro que é atualizado por essas funções.  
  
## <a name="general-metric-functions"></a>Funções de métrica geral  
 Essas são funções gerais usadas por mecanismos de depuração. Especializado funções para avaliadores de expressão e provedores de símbolo são detalhados posteriormente.  
  
### <a name="getmetric-method"></a>Método GetMetric  
 Recupera um valor de métrica do registro.  
  
```cpp  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszMachine|[in] Nome de uma máquina remota possivelmente cujo registro será gravado (`NULL` significa o computador local).|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico avaliador, exceções, etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser obtida. Isso corresponde a um nome de valor específico.|  
|pdwValue|[in] O local de armazenamento do valor de métrica. Há vários tipos de GetMetric que pode retornar um DWORD (como neste exemplo), um BSTR, um GUID ou uma matriz de GUIDs.|  
|pszAltRoot|[in] Uma raiz de registro alternativo a ser usado. Definido como `NULL` para usar o padrão.|  
  
### <a name="setmetric-method"></a>Método SetMetric  
 Define o valor da métrica especificado no registro.  
  
```cpp  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico avaliador, exceções, etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser obtida. Isso corresponde a um nome de valor específico.|  
|dwValue|[in] O local de armazenamento do valor de métrica. Há vários tipos de SetMetric que pode armazenar um DWORD (no exemplo), um BSTR, um GUID ou uma matriz de GUIDs.|  
|fUserSpecific|[in] TRUE se a métrica é específica do usuário e se ele deve ser escrito para o hive do usuário em vez do hive do computador local.|  
|pszAltRoot|[in] Uma raiz de registro alternativo a ser usado. Definido como `NULL` para usar o padrão.|  
  
### <a name="removemetric-method"></a>Método RemoveMetric  
 Remove a métrica especificada no registro.  
  
```cpp  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszType|[in] Um dos tipos de métrica.|  
|guidSection|[in] GUID de um mecanismo específico avaliador, exceções, etc. Especifica uma subseção em um tipo de métrica para um elemento específico.|  
|pszMetric|[in] A métrica a ser removido. Isso corresponde a um nome de valor específico.|  
|pszAltRoot|[in] Uma raiz de registro alternativo a ser usado. Definido como `NULL` para usar o padrão.|  
  
### <a name="enummetricsections-method"></a>Método EnumMetricSections  
 Enumera as várias seções de métrica no registro.  
  
```cpp  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|pszMachine|[in] Nome de uma máquina remota possivelmente cujo registro será gravado (`NULL` significa o computador local).|  
|pszType|[in] Um dos tipos de métrica.|  
|rgguidSections|[out no] Matriz pré-alocados de GUIDs devem ser preenchidos.|  
|pdwSize|[in] O número máximo de GUIDs que podem ser armazenados na `rgguidSections` matriz.|  
|pszAltRoot|[in] Uma raiz de registro alternativo a ser usado. Definido como `NULL` para usar o padrão.|  
  
## <a name="expression-evaluator-functions"></a>Funções de avaliador de expressão  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetEEMetric|Recupera um valor de métrica do registro.|  
|SetEEMetric|Define o valor da métrica especificado no registro.|  
|RemoveEEMetric|Remove a métrica especificada no registro.|  
|GetEEMetricFile|Obtém um nome de arquivo da métrica especificada e o carrega, retornando o conteúdo do arquivo como uma cadeia de caracteres.|  
  
## <a name="exception-functions"></a>Funções de exceção  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera um valor de métrica do registro.|  
|SetExceptionMetric|Define o valor da métrica especificado no registro.|  
|RemoveExceptionMetric|Remove a métrica especificada no registro.|  
|RemoveAllExceptionMetrics|Remove todas as métricas de exceção do registro.|  
  
## <a name="symbol-provider-functions"></a>Funções de símbolo do provedor  
  
|Função|Descrição|  
|--------------|-----------------|  
|GetSPMetric|Recupera um valor de métrica do registro.|  
|SetSPMetric|Define o valor da métrica especificado no registro.|  
|RemoveSPMetric|Remove a métrica especificada no registro.|  
  
## <a name="enumeration-functions"></a>Funções de enumeração  
  
|Função|Descrição|  
|--------------|-----------------|  
|EnumMetricSections|Enumera todas as métricas para um tipo específico de métrica.|  
|EnumDebugEngine|Enumera os mecanismos de depuração registrado.|  
|EnumEEs|Enumera os avaliadores de expressão registrado.|  
|EnumExceptionMetrics|Enumera todas as métricas de exceção.|  
  
## <a name="metric-definitions"></a>Definições de métricas  
 Essas definições podem ser usadas para nomes de métrica predefinidos. Os nomes correspondem aos nomes de valor e estão todas definidas como cadeias de caracteres largos e várias chaves de registro: por exemplo, `extern LPCWSTR metrictypeEngine`.  
  
|Tipos predefinidos de métricos|Descrição: A chave base para...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Todas as métricas do mecanismo de depuração.|  
|metrictypePortSupplier|Todas as métricas de fornecedor de porta.|  
|metrictypeException|Todas as métricas de exceção.|  
|metricttypeEEExtension|Todas as extensões do avaliador de expressão.|  
  
|Propriedades do mecanismo de depuração|Descrição|  
|-----------------------------|-----------------|  
|metricAddressBP|Definido como zero para indicar o suporte para pontos de interrupção de endereço.|  
|metricAlwaysLoadLocal|Definido como zero para sempre carregar o mecanismo de depuração localmente.|  
|metricLoadInDebuggeeSession|NÃO USADO|  
|metricLoadedByDebuggee|Definido como zero para indicar que o mecanismo de depuração sempre será carregado com o ou o programa que está sendo depurado.|  
|metricAttach|Definido como zero para indicar o suporte para conexão com os programas existentes.|  
|metricCallStackBP|Definido como zero para indicar o suporte para pontos de interrupção de pilha de chamada.|  
|metricConditionalBP|Definido como zero para indicar o suporte para a configuração de pontos de interrupção condicionais.|  
|metricDataBP|Definido como zero para indicar o suporte para a configuração de pontos de interrupção em alterações nos dados.|  
|metricDisassembly|Definido como zero para indicar o suporte para a produção de uma listagem de desmontagem.|  
|metricDumpWriting|Definido como zero para indicar o suporte para gravação (o despejo de memória para um dispositivo de saída) de despejo.|  
|metricENC|Definido como zero para indicar o suporte para editar e continuar. **Observação:** um mecanismo de depuração personalizado nunca deve definir isso ou sempre deve configurá-la como 0.|  
|metricExceptions|Definido como zero para indicar o suporte para exceções.|  
|metricFunctionBP|Definido como zero para indicar o suporte para pontos de interrupção nomeados (pontos de interrupção falhar quando um determinado nome de função é chamado).|  
|metricHitCountBP|Definido como zero para indicar o suporte para a configuração de pontos de interrupção "ocorrências de ponto" (pontos de interrupção que são disparados somente depois que está sendo atingido um determinado número de vezes).|  
|metricJITDebug|Definido como zero para indicar o suporte de depuração just-in-time (o depurador é iniciado quando ocorre uma exceção em um processo em execução).|  
|metricMemory|NÃO USADO|  
|metricPortSupplier|Defina isso para o CLSID do fornecedor porta se um for implementado.|  
|metricRegisters|NÃO USADO|  
|metricSetNextStatement|Definido como zero para indicar o suporte para definir a próxima instrução (que ignora a execução de instruções intermediárias).|  
|metricSuspendThread|Definido como zero para indicar o suporte para suspender a execução do thread.|  
|metricWarnIfNoSymbols|Definido como zero para indicar que o usuário será notificado se não houver nenhum símbolo.|  
|metricProgramProvider|Defina o CLSID do provedor do programa.|  
|metricAlwaysLoadProgramProviderLocal|Defina como diferente de zero para indicar que o provedor do programa deve ser sempre carregado localmente.|  
|metricEngineCanWatchProcess|Defina como diferente de zero para indicar que o mecanismo de depuração observará para processar eventos em vez do provedor do programa.|  
|metricRemoteDebugging|Defina como diferente de zero para indicar o suporte para depuração remota.|  
|metricEncUseNativeBuilder|Defina como diferente de zero para indicar que o editar e continuar Manager devem usar encbuild.dll do mecanismo de depuração para compilar para editar e continuar. **Observação:** um mecanismo de depuração personalizado nunca deve definir isso ou sempre deve configurá-la como 0.|  
|metricLoadUnderWOW64|Defina como diferente de zero para indicar que o mecanismo de depuração deve ser carregado no processo depurado sob o WOW ao depurar um processo de 64 bits. Caso contrário, o mecanismo de depuração será carregado no processo do Visual Studio (que é executado no WOW64).|  
|metricLoadProgramProviderUnderWOW64|Defina como diferente de zero para indicar que o provedor do programa deve ser carregado no processo de depuração ao depurar um processo de 64 bits em WOW; Caso contrário, ele será carregado no processo do Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Defina como diferente de zero para indicar que o processo deve ser interrompida se uma exceção sem tratamento é gerada em limites de código gerenciado/não gerenciado.|  
|metricAutoSelectPriority|Defina a prioridade para a seleção automática do mecanismo de depuração (maior valores é igual a prioridade mais alta).|  
|metricAutoSelectIncompatibleList|Chave do registro que contém entradas que especificam os GUIDs para mecanismos de depuração a ser ignorado na seleção automática. Essas entradas são um número (0, 1, 2 e assim por diante) com um GUID, expressado como uma cadeia de caracteres.|  
|metricIncompatibleList|Chave do registro que contém entradas que especificam os GUIDs para mecanismos de depuração que são incompatíveis com o mecanismo de depuração.|  
|metricDisableJITOptimization|Defina como diferente de zero para indicar que as otimizações de just-in-time (para código gerenciado) devem ser desabilitadas durante a depuração.|  
  
|Propriedades do avaliador de expressão|Descrição|  
|-------------------------------------|-----------------|  
|metricEngine|Isso mantém o número de mecanismos de depuração que suportam o avaliador da expressão especificada.|  
|metricPreloadModules|Defina como diferente de zero para indicar que módulos devem ser pré-carregados quando um avaliador de expressão é iniciado em um programa.|  
|metricThisObjectName|Defina como o nome do objeto "this".|  
  
|Propriedades de extensão do avaliador de expressão|Descrição|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Nome da dll que oferece suporte a essa extensão.|  
|metricExtensionRegistersSupported|Lista de registros com suporte.|  
|metricExtensionRegistersEntryPoint|Ponto de entrada para acessar registros.|  
|metricExtensionTypesSupported|Lista de tipos com suporte.|  
|metricExtensionTypesEntryPoint|Ponto de entrada para acessar tipos.|  
  
|Propriedades da porta de fornecedor|Descrição|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|O CLSID do seletor de porta (uma caixa de diálogo, o usuário pode usar para selecionar as portas e adicionar as portas a serem usadas para depuração).|  
|metricDisallowUserEnteredPorts|Diferente de zero se as portas de entrada do usuário não podem ser adicionadas para o fornecedor de porta (Isso faz com que a caixa de diálogo Seletor de porta essencialmente somente leitura).|  
|metricPidBase|A ID de processo base usada pelo fornecedor de porta ao alocar identificadores de processo.|  
  
|Tipos de armazenamento de SP predefinidas|Descrição|  
|-------------------------------|-----------------|  
|storetypeFile|Os símbolos são armazenados em um arquivo separado.|  
|storetypeMetadata|Os símbolos são armazenados como metadados em um assembly.|  
  
|Outras propriedades|Descrição|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Defina isso para mostrar código nonuser diferente de zero.|  
|metricJustMyCodeStepping|Defina como diferente de zero para indicar que a revisão pode ocorrer apenas no código do usuário.|  
|metricCLSID|CLSID para um objeto de um tipo específico de métrica.|  
|metricName|Nome amigável de um objeto de um tipo específico de métrica.|  
|metricLanguage|Nome do idioma.|  
  
## <a name="registry-locations"></a>Locais do registro  
 As métricas são lidas de e gravadas especificamente no registro, o `VisualStudio` subchave.  
  
> [!NOTE]
>  Na maioria das vezes, as métricas serão gravadas para a chave HKEY_LOCAL_MACHINE. No entanto, às vezes, HKEY_CURRENT_USER será a chave de destino. Dbgmetric.lib trata as duas chaves. Ao obter uma métrica, ele procura HKEY_CURRENT_USER primeiro e, em seguida, HKEY_LOCAL_MACHINE. Quando ele é definir uma métrica, um parâmetro especifica qual chave de nível superior para usar.  
  
 *[chave do Registro]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[raiz versão]*\  
  
 *[raiz métrica]*\  
  
 *[tipo de métrica]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[chave do Registro]*|`HKEY_CURRENT_USER` ou `HKEY_LOCAL_MACHINE`.|  
|*[raiz versão]*|A versão do Visual Studio (por exemplo, `7.0`, `7.1`, ou `8.0`). No entanto, essa raiz também pode ser modificado usando o **/rootsuffix** alternar para **devenv.exe**. VSIP, esse modificador normalmente é **Exp**, portanto, a raiz de versão deve ser, por exemplo, 8.0Exp.|  
|*[raiz métrica]*|Isso é `AD7Metrics` ou `AD7Metrics(Debug)`, dependendo se a versão de depuração de dbgmetric.lib é usada. **Observação:** se ou não dbgmetric.lib for usada, essa convenção de nomenclatura deverão ser seguida para se houver diferenças entre debug e release versões que devem ser refletidas no registro.|  
|*[tipo de métrica]*|O tipo de métrica a ser gravado: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, etc. Eles são definidos como dbgmetric.h como `metricTypeXXXX`, onde `XXXX` é o nome de tipo específico.|  
|*[métrica]*|O nome de uma entrada a ser atribuído um valor para definir a métrica. A organização real das métricas depende do tipo de métrica.|  
|*[valor de métrica]*|O valor atribuído à métrica. O tipo que de valor deve ter (string), número, etc. depende a métrica.|  
  
> [!NOTE]
>  Todos os GUIDs são armazenados no formato de `{GUID}`. Por exemplo, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Mecanismos de depuração  
 A seguir está a organização das métricas de mecanismos de depuração no registro. `Engine`é o nome do tipo de métrica para um mecanismo de depuração e corresponde ao *[tipo de métrica]* na subárvore de registro acima.  
  
 `Engine`\  
  
 *[mecanismo guid]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `PortSupplier`\  
  
 `0` = *[guid do fornecedor de porta]*  
  
 `1` = *[guid do fornecedor de porta]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[mecanismo guid]*|O GUID do mecanismo de depuração.|  
|*[classe guid]*|O GUID da classe que implementa esse mecanismo de depuração.|  
|*[guid do fornecedor de porta]*|O GUID do fornecedor de porta, se houver. Vários mecanismos de depuração usam o fornecedor de porta padrão e, portanto, não especificam seu próprio fornecedor. Nesse caso, a subchave `PortSupplier` estará ausente.|  
  
### <a name="port-suppliers"></a>Fornecedores de porta  
 A seguir está a organização das métricas de fornecedor de porta no registro. `PortSupplier`é o nome do tipo de métrica para um fornecedor de porta e corresponde ao *[tipo de métrica]*.  
  
 `PortSupplier`\  
  
 *[guid do fornecedor de porta]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do fornecedor de porta]*|O GUID do fornecedor de porta|  
|*[classe guid]*|O GUID da classe que implementa este fornecedor de porta|  
  
### <a name="symbol-providers"></a>Provedores de símbolo  
 A seguir está a organização das métricas de fornecedor de símbolo no registro. `SymbolProvider`é o nome do tipo de métrica para o provedor de símbolo e corresponde à *[tipo de métrica]*.  
  
 `SymbolProvider`\  
  
 *[guid do provedor de símbolo]*\  
  
 `file`\  
  
 `CLSID` = *[classe guid]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `metadata`\  
  
 `CLSID` = *[classe guid]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do provedor de símbolo]*|O GUID do provedor de símbolo|  
|*[classe guid]*|O GUID da classe que implementa este provedor de símbolo|  
  
### <a name="expression-evaluators"></a>Avaliadores de expressão  
 A seguir está a organização das métricas de avaliador de expressão no registro. `ExpressionEvaluator`é o nome do tipo de métrica para o avaliador de expressão e corresponde ao *[tipo de métrica]*.  
  
> [!NOTE]
>  O tipo de métrica para `ExpressionEvaluator` não está definido em dbgmetric.h, como presume-se que todas as alterações de métrica para avaliadores de expressão irá por meio das funções de métrica de avaliador de expressão apropriada (o layout do `ExpressionEvaluator` subchave é um pouco complicada, então os detalhes estão ocultos em dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[guid do idioma]*\  
  
 *[guid do fornecedor]*\  
  
 `CLSID` = *[classe guid]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 `Engine`\  
  
 `0` = *[guid do mecanismo de depuração]*  
  
 `1` = *[guid do mecanismo de depuração]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do idioma]*|O GUID de um idioma|  
|*[guid do fornecedor]*|O GUID de um fornecedor|  
|*[classe guid]*|O GUID da classe que implementa a avaliador de expressão|  
|*[guid do mecanismo de depuração]*|O GUID de um mecanismo de depuração que este avaliador de expressão funciona com|  
  
### <a name="expression-evaluator-extensions"></a>Extensões do avaliador de expressão  
 A seguir está a organização das métricas de extensão do avaliador de expressão no registro. `EEExtensions`é o nome de tipo de métrica para a expressão de extensões do avaliador e corresponde ao *[tipo de métrica]*.  
  
 `EEExtensions`\  
  
 *[extensão guid]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[extensão guid]*|O GUID de uma extensão do avaliador de expressão|  
  
### <a name="exceptions"></a>Exceções  
 A seguir está a organização das métricas de exceções no registro. `Exception`é o nome do tipo de métrica para as exceções e corresponde à *[tipo de métrica]*.  
  
 `Exception`\  
  
 *[guid do mecanismo de depuração]*\  
  
 *[tipos de exceção]*\  
  
 *[exceção]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
 *[exceção]*\  
  
 *[métrica] = [valor de métrica]*  
  
 *[métrica] = [valor de métrica]*  
  
|Espaço reservado|Descrição|  
|-----------------|-----------------|  
|*[guid do mecanismo de depuração]*|O GUID de um mecanismo de depuração que dá suporte a exceções.|  
|*[tipos de exceção]*|Um título geral para a subchave identifica a classe de exceções que podem ser tratados. Os nomes comuns são **exceções C++**, **Win32 exceções**, **exceções do Common Language Runtime**, e **verificações de tempo de execução nativo**. Esses nomes também são usados para identificar uma determinada classe de exceção para o usuário.|  
|*[exceção]*|Um nome para uma exceção: por exemplo, **com_error** ou **Control-Break**. Esses nomes também são usados para identificar uma exceção em particular para o usuário.|  
  
## <a name="requirements"></a>Requisitos  
 Esses arquivos estão localizados no [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] diretório de instalação do SDK (por padrão, *[unidade]*\Program Files\Microsoft SDK do Visual Studio 2010\\).  
  
 Cabeçalho: includes\dbgmetric.h  
  
 Biblioteca: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)