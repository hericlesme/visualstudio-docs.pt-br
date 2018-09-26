---
ms.technology: vs-ai-tools
ms.openlocfilehash: d52ed79b28794a3bc1532822e0eb75b6277314b2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280695"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procurar no armazenamento para carregar dados ou baixar modelos e logs

É possível procurar em todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o upload de dados ou download de modelos e logs. Ou, se desejar acessar os logs e as saídas de trabalho de um trabalho específico, você poderá fazer isso também no navegador do trabalho.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para acessar todos os dados no computador remoto ou no compartilhamento de arquivos
1. Abra o **Gerenciador de Servidores**.
2. Expanda o computador remoto ou o contexto de computação do IA do Lote.
3. Clique com o botão direito do mouse em **Armazenamento** e, em seguida, clique em **Procurar**.

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acessar dados específicos do trabalho no computador remoto ou no compartilhamento de arquivos
1. Abra o [Histórico de Trabalhos](job-details.md)
2. Selecione o trabalho.
3. Clique em **Pasta de Trabalho** ou clique em **StdOut / Stderr** para acesso rápido a esses importantes arquivos de log.

    ![storage](media\manage-storage\job-workingfolder.png)
