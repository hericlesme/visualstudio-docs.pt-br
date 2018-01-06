---
title: "Política de suporte para o Visual Basic 6.0 | Microsoft Docs"
ms.date: 08/28/2017
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs: VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload: paulyuk
ms.openlocfilehash: a8977aad735a115089685ed0032b3d358d8b89c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Política de suporte para o Visual Basic 6.0 no Windows


## <a name="executive-summary"></a>Resumo executivo

A equipe do Visual Basic tem o compromisso de compatibilidade "Simplesmente funciona" de aplicativos Visual Basic 6.0 os seguintes sistemas operacionais Windows: 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 incluindo R2
- Windows Server 2008, incluindo R2

Meta da equipe do Visual Basic é que os aplicativos do Visual Basic 6.0 continuam sendo executados em versões com suporte do Windows. Como detalhadas neste documento, o tempo de execução do Visual Basic 6.0 do núcleo terá suporte para o tempo de vida completo de versões com suporte do Windows, que é cinco anos de suporte básico, seguido por cinco anos de suporte estendido (http://support.microsoft.com/gp/lifepolicy). A barra de suporte será limitada a regressões sérias e problemas críticos de segurança para aplicativos existentes.

## <a name="technical-summary"></a>Resumo técnico

Visual Basic 6.0 é composta por esses produtos principais:
- Visual Basic 6.0 IDE (ambiente de desenvolvimento integrado).
- Tempo de execução do Visual Basic 6.0: bibliotecas de base e o mecanismo de execução usado para executar aplicativos do VB 6.0.
- Arquivos de estendido de tempo de execução do Visual Basic 6.0: selecionado arquivos OCX do controle ActiveX, bibliotecas e ferramentas com a mídia IDE e como uma versão online de envio.

## <a name="the-visual-basic-60-ide"></a>O Visual Basic IDE 6.0

Não há suporte para o IDE do Visual Basic 6.0 a partir de 8 de abril de 2008. Além disso, o Windows e o Visual Basic equipes testamos IDE do Visual Basic 6.0 no Windows Vista, Windows 7, Windows Server 2008, Windows 8 e Windows 8.1 para entender e reduzir (se apropriado) problemas de compatibilidade em versões de 32 bits do Windows (consulte o [Windows de 64 bits](#62-bit-windows) seção abaixo para obter mais informações sobre os sistemas de 64 bits). Este lançamento não altera a política de suporte para o IDE.

## <a name="the-visual-basic-60-runtime"></a>O tempo de execução do Visual Basic 6.0

O tempo de execução do Visual Basic 6.0 é definido como os arquivos binários compilados originalmente incluídos na lista de redistribuição para o Visual Basic 6.0. Esses arquivos foram marcados como distribuível na licença do Visual Basic 6.0 original. Esses arquivos são exemplos de biblioteca de tempo de execução do Visual Basic 6.0 (`msvbvm60.dll`), controles (ou seja, `msflxgrd.ocx`) junto com o tempo de execução de arquivos de suporte para outras áreas funcionais principais (ou seja, o MDAC).

O tempo de execução é dividido em três grupos:

- Suporte para arquivos de tempo de execução - envio no sistema operacional

   Arquivos de tempo de execução de chave Visual Basic 6.0, usados na maioria dos cenários de aplicativo, são fornecidos no e suporte para o tempo de vida de versões com suporte do Windows. Esse tempo de vida é cinco anos de suporte básico e cinco anos de suporte estendido do momento em que uma determinada versão do Windows é fornecido. Esses arquivos foram testados quanto à compatibilidade como parte de nosso teste de aplicativos do Visual Basic 6.0 em execução em versões do Windows. 

   > [!NOTE]
   > Todas as versões com suporte do Windows contém uma lista quase idêntica de arquivos e os requisitos de redistribuição para aplicativos que contêm esses arquivos devem ser praticamente idênticos. Uma diferença fundamental é que `TriEdit.dll` foi removido do Windows Vista e versões posteriores.

- Suporte para arquivos de tempo de execução –-estendido arquivos para distribuir com seu aplicativo

   Essa lista estendida consiste em controles de tecla, bibliotecas e ferramentas que são instaladas da mídia do IDE ou no site Microsoft.com para a máquina do desenvolvedor. Normalmente, o IDE VB6 instalado esses controles para a máquina de desenvolvedor, por padrão. O desenvolvedor deve redistribuir esses arquivos com o aplicativo. A versão com suporte dos arquivos está disponível online no Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- Arquivos de tempo de execução sem suporte

   Alguns arquivos que o está fora do mainstream suporte ou nunca foram incluídos como parte de redistribuição do tempo de execução (por exemplo, eles foram incluídos no `\Tools` pasta na mídia do IDE para dar suporte a aplicativos herdados de VB4/VB5, ou que estavam controles de terceiros). Não há suporte para esses arquivos no Windows. em vez disso, eles estão sujeitos a aplica qualquer contrato de suporte para a mídia que eles foram enviados com. Isso significa que nenhuma garantia em torno de manutenção e suporte. Em alguns casos, há suporte para versões posteriores dessas bibliotecas. Detalhes sobre a compatibilidade com versões anteriores ou migração de versões com suporte são fornecidos abaixo.

Para obter detalhes específicos sobre os arquivos incluídos em cada grupo de suporte, consulte o [definição de tempo de execução](#runtime-definition) seção abaixo.

## <a name="the-visual-basic-60-support-lifetime"></a>O tempo de vida de suporte do Visual Basic 6.0

Suporte a e/ou envio de binários de tempo de execução do Visual Basic 6.0 em versões do Windows não altera a política de suporte para o IDE do Visual Basic 6.0 ou o IDE do Visual Studio 6.0 como um todo. Os produtos tirado do suporte estendido em 8 de abril de 2008.

Detalhes do ciclo de vida de suporte de produtos da Microsoft podem ser encontrados em http://support.microsoft.com/gp/lifepolicy. Como parte desse ciclo de vida de suporte, a Microsoft continuará dar suporte ao tempo de execução do Visual Basic 6.0 versões com suporte do Windows para o tempo de vida do suporte desses sistemas operacionais. Por exemplo, isso significa que o tempo de execução do Visual Basic 6.0 terá suporte no Windows Server 2003 até junho de 2008 para o suporte base e de junho de 2013 para suporte estendido.
Para obter mais detalhes sobre o ciclo de vida de suporte ou para obter informações sobre opções adicionais de suporte, visite nossa página de suporte em http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>Windows de 64 bits

Arquivos de tempo de execução do Visual Basic 6.0 são de 32 bits. Esses arquivos fornecidos em 64 bits sistemas operacionais Windows referenciada na tabela a seguir. componentes e aplicativos de VB6 de 32 bits têm suporte no ambiente de emulação do WOW somente. componentes de 32 bits também devem ser hospedados em processos de aplicativos de 32 bits.

O IDE do Visual Basic 6.0 nunca foi oferecido em uma versão de 64 bits nativo, nem o IDE de 32 bits tem suporte no Windows de 64 bits. VB6 desenvolvimento no Windows de 64 bits ou qualquer arquitetura nativo que não seja de 32 bits não é e não terá suporte.

## <a name="windows-7"></a>Windows 7

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows 7 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows 7.

O tempo de execução do VB6 será enviado e terá suporte no Windows 7 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits.

## <a name="windows-81"></a>Windows 8.1

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows 8.1 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows 8.1.

O tempo de execução do VB6 será enviado e terá suporte no Windows 8.1 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte para Windows 8.1 como sendo o mesmo, assim como para o Windows 7.

## <a name="windows-10"></a>Windows 10

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows 10 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows 10.

O tempo de execução do VB6 será enviado e terá suporte no Windows 10 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte para Windows 10 como sendo o mesmo que para Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows Server 2008 foi lançado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows Server 2008.

O tempo de execução do VB6 será enviado e terá suporte no Windows Server 2008 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows Server 2008 R2 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows Server 2008 R2.

O tempo de execução do VB6 será enviado e terá suporte no Windows Server 2008 R2 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte do Windows Server 2008 R2 como sendo o mesmo, assim como para o Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows Server 2012 foi lançado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows Server 2012.

O tempo de execução do VB6 será enviado e terá suporte no Windows Server 2012 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte para o Windows Server 2012 como sendo o mesmo, assim como para o Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows Server 2012 R2 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows Server 2012 R2.

O tempo de execução do VB6 será enviado e terá suporte no Windows Server 2012 R2 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte do Windows Server 2012 R2 como sendo o mesmo, assim como para o Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

Desde o lançamento inicial desta declaração de suporte, o sistema operacional Windows Server 2016 foi liberado. Este documento foi atualizado para esclarecer o suporte da Microsoft para VB6 no Windows Server 2016.

O tempo de execução do VB6 será enviado e terá suporte no Windows Server 2016 para o tempo de vida do sistema operacional. Arquivos de tempo de execução do Visual Basic 6.0 continuam a ser 32 bits somente, e todos os componentes devem ser hospedados em processos de aplicativos de 32 bits. Os desenvolvedores podem pensar a história de suporte para o Windows Server 2016 como sendo o mesmo, assim como para o Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Versões de sistema operacional com suporte do Windows

Esta seção fornece informações adicionais sobre os sistemas operacionais que oferecem algum nível de suporte para VB6. 

|Sistema operacional Windows|VB6 Tempo de execução com suporte</br>Arquivos de envio no Windows têm suporte?|VB6 Suporte Rutime</br>Arquivos estendidos</br>para distribuir com seu aplicativo têm suporte?| IDE VB6 tem suporte?|
|---|---|---|---|
|Windows 10, todas as edições de 32 bits|Sim *|Sim *|Não|
|Windows 10, todas as edições de 64 bits (WOW)|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows 8.1, todas as edições de 32 bits|Sim *|Sim *|Não|
| Windows 8.1, todas as edições de 64 bits (WOW)|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows 7, todas as edições de 32 bits|Sim *|Sim *|Não|
|Windows 7, todas as edições de 64 bits (WOW)|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows Server 2016, todas as edições de 64 bits (WOW)|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows Server 2012 R2, todas as edições de 64 bits (WOW)<br>Windows Server 2012, todas as edições de 64 bits (WOW)|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Sim* </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows Server 2008 R2 x64 todas as edições (WOW)</br>Windows Server 2008 x64 todas as edições (WOW)|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Sim * </br> aplicativos de 32 bits em execução em WOW somente|Não|
|Windows Server 2008, todas as edições de 32 bits|Sim *|Sim *|Não|


> [!NOTE]
> &#42;  Suporte de tempo de execução do VB6 é limitado pelo ciclo de vida de suporte do Windows.  Por exemplo, se o sistema operacional de destino está em suporte estendido, VB6 não pode ter um nível maior de suporte que suporte estendido.  O [folha de fatos do ciclo de vida de suporte do Windows](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) contém informações de ciclo de vida adicionais sobre versões atuais e anteriores do Windows.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Uso de tempo de execução do Visual Basic 6.0 em VBA e do Office

Visual Basic para aplicativos ou VBA, é uma tecnologia de distinta comumente usada para automação do aplicativo e macros dentro de outros aplicativos, geralmente dentro de aplicativos do Microsoft Office. VBA fornecida como parte do Office e, portanto, o suporte para VBA é controlado pela política de suporte do Office. No entanto, há situações em que o VBA é usado para chamar ou binários de tempo de execução do Visual Basic 6.0 e controles de host. Nessas situações, Visual Basic 6.0 tem suporte a arquivos de tempo de execução no sistema operacional e a lista de arquivos estendida também têm suporte quando usado dentro de um ambiente com suporte do VBA.

Para cenários de tempo de execução do VB6 com suporte no VBA, todos os itens a seguir devem ser verdadeiras:

- Ainda há suporte para a versão do sistema operacional do host de tempo de execução do VB.
- Ainda há suporte para a versão de host do Office para VBA.
- Ainda há suporte para os arquivos de tempo de execução em questão.

## <a name="visual-basic-script-vbscript"></a>Script do Visual Basic (VBScript)

VBScript está relacionado ao Visual Basic 6.0 e esta instrução de suporte. No entanto, o VBScript atualmente está enviando como parte do Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012 incluindo R2 e Windows Server 2016 de incluindo e é controlado pelo ciclo de vida de suporte do sistema operacional.

## <a name="third-party-components"></a>Componentes de terceiros

Microsoft é capaz de dar suporte aos componentes de terceiros, como controles ActiveX/OCX. Os clientes são incentivados a entrar em contato com o fornecedor do controle original para obter detalhes sobre o suporte para esses componentes.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Relatar problemas com aplicativos do VB 6.0 em execução no Windows

Desenvolvedores planejando usar o Visual Basic 6.0 com um dos sistemas operacionais Windows devem instalar o sistema operacional e iniciar o teste de compatibilidade de aplicativos usando testes de aceitação original do aplicativo.

Se você encontrar um problema com o aplicativo do Visual Basic 6.0 em execução em um dos sistemas operacionais Windows, siga seus canais de suporte normal para relatar o problema.

## <a name="supported-and-shipping-in-windows"></a>Com suporte e envio no Windows

| | | | |
|---|---|---|---|
|ATL.dll|         msadcor.dll|     msorcl32. dll|   OLE2. dll|
|Asycfilt|    Msadcs|      Msvbvm60|   Ole32|
|Comcat|      MSADDS|      Msvcirt|    Oleaut32.dll|
|COMPOBJ. dll|     msaddsr.dll|     Msvcrt|     Oleaut32.dll|
|DBNMPNTW.dll|    msader15.dll|    Msvcrt40.|   Oledb32|
|dcomcnfg.exe|    Msado15.dll|     Mtxdm|      oledb32r.dll|
|Dllhost.exe|     Msador15|    Mtxoci. dll|     oledlg.dll|
|Ds16gt.dll|      msadrh15.dll|    Odbc16gt.dll|   OLEPRO32|
|ds32gt.dll|      mscpxl32.dll|    Odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      Odbc32gt.dll|   Regsvr32.exe|
|hh.exe|          msdaenum.dll|    Odbcad32.exe|   rpcns4.dll|
|Hhctrl|      msdaer.dll|      ODBCCP32.cpl|   Rpcrt4.dll|
|Imagehlp.dll|    MSDAORA.dll|     ODBCCP32. dll|   Scrrun|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   Secur32.dll|
|itircl|      Msdaprst. dll|    odbccu32.dll|   simpdata.tlb|
|ITSS|        MSDAPS.dll|      odbcint.dll|    SQLOLEDB|
|Mfc40|       Msdasc|      odbcji32.dll|   Sqlsrv32.dll|
|Mfc42|       MSDASQL|     odbcjt32.dll|   Stdole2|
|mfc42enu.dll|    msdasqlr.dll|    Odbctrac|   stdole32.tlb|
|Msadce. dll|      msdatsrc.tlb|    oddbse32.dll|   Storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    VBAJET32|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|Msadco. dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Arquivos de tempo de execução com suporte para distribuir com seu aplicativo

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |MSstdfmt| 
|comct332.ocx |mscdrun.dll  |Msflxgrd  |msstkprp.dll| 
|Comctl32 |Mschrt20 |mshflxgd.ocx  |mswcrun.dll|  
|Comdlg32 |Mscomct2 |mshtmpgr.dll  |Mswinsck. ocx| 
|dbadapt.dll  |Mscomctl |MSINET.ocx    |picclp32.ocx| 
|dbgrid32. ocx |mscomm32.ocx |Msmapi32.ocx  |Richtx32. ocx| 
|dblist32.ocx |msdatgrd.ocx |Msmask32  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32. ocx| 
|msadodc.ocx  |msdatrep.ocx |MSRDO20. dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Sem suporte, mas com suporte e compatível com atualizações disponíveis

| | | | |
|---|---|---|---|
|Dao350|   Msexch35. dll| msjter35.dll| Msrepl35. dll|
|Mdac_typ.exe| MSEXCL35.dll| msjtor35.dll| Mstext35|
|MSChart.ocx|  msjet35|  msltus35.dll| Msxbse35|
|msdaerr.dll|  msjint35.dll| Mspdox35| odbctl32.dll|
|msdatl2.dll|  MSjt4jlt| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Arquivos de tempo de execução sem suporte

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  RDOCURS.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   Vbar332. dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  Rpcss.exe|     vsdbflex.srg|
|autprx32.dll| Olecnv32| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  Dbmssocn. dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tblinf32|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   TriEdit|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Binários de suporte de localização

Os seguintes binários são necessários para dar suporte a aplicativos do Visual Basic 6.0 em execução em versões localizadas do sistema operacional Windows. Eles têm suporte, mas não são fornecidos no Windows. Esses arquivos são necessários para ser enviada com a configuração do aplicativo.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Arquivos de tempo de execução com suporte para distribuir com seu aplicativo

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

