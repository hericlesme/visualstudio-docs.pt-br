## <a name="install-the-connected-environment-cli"></a>Instalar a CLI do Connected Environment
O Connected Environment requer uma configuração mínima do computador local. A maior parte da configuração do ambiente de desenvolvimento é armazenada na nuvem e pode ser compartilhada com outros usuários.

### <a name="install-on-mac"></a>Instalar no Mac
Baixe e instale a CLI do Connected Environment:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Instalar no Windows
1. Instale o [Git para Windows](https://git-scm.com/downloads), selecionando as opções de instalação padrão. 
1. Baixe **kubectl.exe** [neste link](https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/windows/amd64/kubectl.exe) e **salve-o** em um local em seu caminho.
1. Baixe e execute o [Instalador da CLI do Connected Environment](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Instalar no Linux
Em breve...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Obter a depuração do Kubernetes para o VS Code
Embora seja possível usar a CLI do Connected Environment como uma ferramenta autônoma, os recursos avançados, como a depuração do Kubernetes, estão disponíveis para desenvolvedores do .NET Core e do Node.js que usam o VS Code.

1. Se você não tiver o [VS Code](https://code.visualstudio.com/Download), instale-o.
1. Baixe a [extensão do VS Connected Environment](https://aka.ms/get-vsce-code).
1. Instale a extensão: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.0.vsix
```
