# <a name="updating-an-existing-application-for-msbuild-15"></a>Atualizando um aplicativo existente para o MSBuild 15

Em versões do MSBuild anteriores à 15.0, o MSBuild era carregado do GAC (cache de assembly global) e extensões do MSBuild eram instaladas no registro. Isso garantia que todos os aplicativos usassem a mesma versão do MSBuild e tivessem acesso aos mesmos conjuntos de ferramentas, mas impedia instalações lado a lado de diferentes versões do Visual Studio.

Para dar suporte a uma instalação mais rápida, menor e lado a lado, o Visual Studio 2017 não coloca mais o MSBuild no GAC ou modifica o registro. Infelizmente, isso significa que aplicativos que desejam usar a API do MSBuild para avaliar ou criar projetos não podem contar implicitamente com a instalação do Visual Studio.

## <a name="using-msbuild-from-visual-studio"></a>Usando o MSBuild para Visual Studio

Para garantir que builds programáticos de seu aplicativo correspondam àqueles feitos no Visual Studio ou no MSBuild.exe, carregue assemblies do MSBuild do Visual Studio e use os SDKs disponíveis dentro do Visual Studio. O pacote NuGet Microsoft.Build.Locator simplifica isso.

## <a name="using-microsoftbuildlocator"></a>Usando Microsoft.Build.Locator

Se redistribuir `Microsoft.Build.Locator.dll` com seu aplicativo, você não precisará distribuir outros assemblies do MSBuild.

Atualizar um projeto para usar o MSBuild 15 e a API de localizador requer algumas alterações no seu projeto, descritas abaixo. Para ver um exemplo das alterações necessárias para atualizar um projeto, consulte [As confirmações feitas em um projeto de exemplo no repositório do MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Alterar as referências do MSBuild

Para garantir que o MSBuild seja carregado de um local central, você não poderá distribuir seus assemblies com seu aplicativo.

O mecanismo para alterar o projeto para evitar carregar MSBuild de locais centrais depende de como você referencia o MSBuild.

#### <a name="using-nuget-packages-preferred"></a>Usando pacotes NuGet (preferencial)

Essas instruções pressupõem que você esteja usando [`PackageReference`referências de NuGet de estilo](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files).

Altere os arquivos de projeto para fazer referência a assemblies de MSBuild de seus pacotes NuGet. Especifique `ExcludeAssets=runtime` para informar o NuGet que os assemblies são necessários somente no tempo de criação e não devem ser copiados para o diretório de saída.

As versões principal e secundária dos pacotes do MSBuild devem ser menores ou iguais à versão mínima do Visual Studio a que você deseja dar suporte. Se quiser dar suporte a qualquer versão do Visual Studio 2017, faça referência à versão do pacote `15.1.548`.

Por exemplo, você pode usar este XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="using-extension-assemblies"></a>Usando assemblies de extensão

Se não puder usar pacotes NuGet, você poderá referenciar assemblies do MSBuild distribuídos com o Visual Studio. Se você referenciar o MSBuild diretamente, certifique-se de que ele não seja copiado para o diretório de saída definindo `Copy Local` como `False`. No arquivo de projeto, isso seria semelhante ao seguinte:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Redirecionamentos de associação

Referenciar o pacote do Microsoft.Build.Locator garante automaticamente que o aplicativo use os redirecionamentos de associação necessários de todas as versões de assemblies do MSBuild para a versão `15.1.0.0`.

### <a name="ensure-output-clean"></a>Garantir uma saída limpa

Crie o projeto e inspecione e verifique se não há nenhum assembly `Microsoft.Build.*.dll` (diferente de `Microsoft.Build.Locator.dll`, adicionado na próxima etapa) no diretório de saída.

### <a name="add-package-reference"></a>Adicionar referência de pacote

Adicione uma referência de pacote NuGet para [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Registre a instância antes de chamar o MSBuild

Adicione uma chamada à API do localizador antes de chamar qualquer método que usa o MSBuild.

A maneira mais simples de fazer isso é adicionar uma chamada para

```c#
MSBuildLocator.RegisterDefaults();
```

no código de inicialização do aplicativo.

Se quiser ter um controle mais refinado sobre o carregamento do MSBuild, você poderá selecionar um resultado de `MSBuildLocator.QueryVisualStudioInstances()` para passar para `MSBuildLocator.RegisterInstance()` manualmente, mas geralmente isso não é necessário.
