---
title: Consulte as dependências entre os arquivos de origem do C++ e arquivos de cabeçalho
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d274241700dfdac393544f554f7025ea4d0bcb46
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263053"
---
# <a name="code-maps-for-c-projects"></a>Mapas de código para projetos do C++

Se você quiser criar mapas mais completos para projetos C++, defina a opção de compilador de informações de procura (**/FR**) nesses projetos. Do contrário, uma mensagem é exibida e solicita a definição dessa opção. Se você selecionar **Okey**, define a opção do mapa atual. Você pode optar por ocultar a mensagem para todos os mapas posteriores.

Quando você abre uma solução que contém projetos do Visual C++, pode demorar algum tempo para atualizar o banco de dados do IntelliSense. Durante esse tempo, você não poderá criar mapas de código para cabeçalho (*. h* ou `#include`) arquivos até que o banco de dados do IntelliSense conclui a atualização. É possível monitorar o andamento da atualização na barra de status do Visual Studio.

- Para ver as dependências entre todos os arquivos de origem e arquivos de cabeçalho em sua solução, selecione **arquitetura** > **gerar gráfico de arquivos de inclusão**.

   ![Gráfico de dependência para código nativo](../modeling/media/dependencygraphgeneral_nativecode.png)

- Para ver as dependências entre os arquivos abertos atualmente, os arquivos de origem relacionados e os arquivos de cabeçalho, abra o arquivo de origem ou o arquivo de cabeçalho. Abra o menu de atalho do arquivo em qualquer lugar dentro do arquivo. Escolha **gerar o gráfico de inclusão de arquivos**.

   ![Gráfico de dependência de primeiro nível para o arquivo. h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Solucionar problemas de mapas de código para código C e C++

Esses itens não são suportados para os códigos C e C++:

- Tipos de base não são exibidos em mapas que incluem a hierarquia pai.

- A maioria dos **Mostrar** itens de menu não estão disponíveis para o código C e C++.

Esses problemas podem ocorrer quando você criar mapas de código para código C e C++:

|**Problema**|**Causa possível**|**Resolução**|
|---------------|------------------------|--------------------|
|O mapa de código falha ao gerar.|Nenhum projeto na solução foi compilado com êxito.|Corrija os erros de compilação ocorrem e, em seguida, gerar o mapa.|
|O Visual Studio não responde ao tentar gerar um mapa de código do **arquitetura** menu.|O arquivo de banco de dados do programa (.pdb) pode estar corrompido.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Recompile a solução e, em seguida, tente novamente.|
|Determinadas configurações do banco de dados de navegação do IntelliSense estão desabilitadas.|Determinadas configurações do IntelliSense podem ser desabilitadas no Visual Studio **opções** caixa de diálogo.|Ative as configurações para habilitá-las.<br /><br /> Consulte [opções, Editor de texto, C/C++, avançado](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|A mensagem **métodos desconhecido** aparece em um nó de método.<br /><br /> Esse problema ocorre porque o nome do método não pode ser resolvido.|O arquivo binário não pode ter uma tabela de realocação de base.|Ativar o **/fixed:** opção de vinculador.|
||Talvez o arquivo de banco de dados do programa (.pdb) não tenha sido compilado.<br /><br /> Um arquivo .pdb armazena informações de depuração, como o tipo, o método e as informações do arquivo de origem.|Ativar o **/Debug** opção de vinculador.|
||Não é possível abrir ou encontrar o arquivo .pdb em locais esperados.|Verifique se o arquivo .pdb existe nos locais esperados.|
||As informações de depuração foram removidas do arquivo .pdb.|Se o **/PDBSTRIPPED** opção foi usada no vinculador, inclua o arquivo. PDB completo em vez disso.|
||O chamador não é uma função, e é uma conversão no arquivo binário ou um ponteiro na seção de dados.|Quando o chamador for uma conversão, tente usar `_declspec(dllimport)` para evitá-la.|

## <a name="see-also"></a>Consulte também

- [Mapear as dependências com mapas de código](../modeling/map-dependencies-across-your-solutions.md)