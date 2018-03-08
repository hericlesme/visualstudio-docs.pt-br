---
ms.technology: vs-ai-tools
ms.openlocfilehash: b941d0ba55c540de4bda1cb0f9c4ed18ceab524f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procurar no armazenamento para carregar dados ou baixar modelos e logs

É possível procurar em todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o upload de dados ou download de modelos e logs. Ou, se desejar acessar os logs e as saídas de trabalho para um trabalho específico, será possível fazer isso também no navegador do trabalho

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para acessar todos os dados no computador remoto ou no compartilhamento de arquivos
1. Abra o **Gerenciador de Servidores**
2. Expanda o computador remoto ou o contexto de computação do IA do Lote
3. Clique com botão direito do mouse em **Armazenamento** e, em seguida, clique em **Procurar**

    ![storage](media\manage-storage\browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acessar os dados específicos do trabalho no computador remoto ou no compartilhamento de arquivos
1. Abra o [Histórico de Trabalhos](job-details.md)
2. Selecionar o trabalho
3. Clique em **Pasta de Trabalho** ou clique em StdOut / Stderr para acesso rápido a esses importantes arquivos de log

    ![storage](media\manage-storage\job-workingfolder.png)
