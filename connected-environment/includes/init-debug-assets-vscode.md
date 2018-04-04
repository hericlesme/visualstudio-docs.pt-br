## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Inicializar ativos de depuração com a extensão do VS Code
Primeiro, precisamos configurar nosso projeto de código para que o VS Code possa se comunicar com o ambiente de desenvolvimento no Azure. A extensão do VS Code para Connected Environment fornece um comando auxiliar para definir a configuração de depuração. 

Abra a **Paleta de Comandos** (usando o menu **Exibição | Paleta de Comandos**) e use o preenchimento automático para digitar e selecionar este comando: `Connected Environment: Create configuration files for connected development`. 

A configuração de depuração para Connected Environment é adicionada na pasta `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **IMPORTANTE**: devido a um bug, feche e abra novamente o VS Code antes de continuar.