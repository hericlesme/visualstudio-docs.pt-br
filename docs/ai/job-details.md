---
---
# <a name="view-recent-job-performance-and-details"></a>Exibir detalhes e desempenho do trabalho recentes
Depois que os trabalhos forem enviados, será possível exibir a lista de trabalhos para ver seus status, duração e mais.

1. No **Gerenciador de Servidores**, expanda o contexto de computação específico 
1. Clique duas vezes em **Trabalhos**
1. Você verá a lista de trabalhos enviados para esse contexto de computação. 
1. Selecionar um **trabalho** específico na lista para exibir detalhes

![monitorar trabalhos](media\job-details\monitor-jobs.png)

> O histórico de trabalhos enviado para VMs Linux é armazenado na VM no diretório /tmp. Portanto, sempre que ela for reinicializada, o histórico de trabalhos será limpo. Para obter um registro permanente do seu histórico de trabalhos, configure sua VM como um contexto de computação no Azure Machine Learning. Em seguida, envie um trabalho para o Azure Machine Learning (selecionando sua VM como o contexto de computação)