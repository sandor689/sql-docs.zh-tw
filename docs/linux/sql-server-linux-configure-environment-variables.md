---
title: 使用環境變數來設定 SQL Server 設定 |Microsoft 文件
description: 本文說明如何使用環境變數來在 Linux 上設定 SQL Server 2017 的特定設定。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: ea8eaf28f33a07d446768c8d4d770bf4727ce48b
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2018
ms.locfileid: "39085370"
---
# <a name="configure-sql-server-settings-with-environment-variables-on-linux"></a>使用 Linux 上的環境變數來設定 SQL Server 設定

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

若要設定 SQL Server 2017 Linux 上，您可以使用數個不同的環境變數。 兩個案例中使用這些變數：

- 若要設定與初始設定`mssql-conf setup`命令。
- 若要設定的新[在 Docker 中的 SQL Server 容器](quickstart-install-connect-docker.md)。

> [!TIP]
> 如果您需要設定 SQL Server，這些安裝案例之後，請參閱[在 Linux 上使用 mssql-conf 工具的 設定 SQL Server](sql-server-linux-configure-mssql-conf.md)。

## <a name="environment-variables"></a>環境變數

| 環境變數 | 描述 |
|-----|-----|
| **ACCEPT_EULA** | 接受 SQL Server 授權合約，當設定為任何值 (例如，' Y')。 |
| **MSSQL_SA_PASSWORD** | 設定 SA 使用者密碼。 |
| **MSSQL_PID** | 設定 SQL Server 版本或產品金鑰。 可能的值包括： </br></br>**Evaluation**</br>**開發人員**</br>**Express**</br>**Web**</br>**Standard**</br>**企業**</br>**產品金鑰**</br></br>如果指定的產品金鑰，它必須是 # # #-# # #-# # #-# # #-# # #，此處的 '#' 是數字或字母的形式。|
| **MSSQL_LCID** | 設定要用於 SQL Server 的語言識別碼。 例如 1036年為法文。 |
| **MSSQL_COLLATION** | 設定 SQL Server 的預設定序。 這會覆寫定序的語言識別碼 (LCID) 的預設的對應。 |
| **MSSQL_MEMORY_LIMIT_MB** | 設定 SQL Server 可以使用的記憶體 （以 mb 為單位） 的最大數量。 根據預設，它會是總實體記憶體的 80%。 |
| **MSSQL_TCP_PORT** | 設定 （預設值 1433年） 的 SQL Server 會接聽的 TCP 連接埠。 |
| **MSSQL_IP_ADDRESS** | 設定 IP 位址。 目前的 IP 位址必須是 IPv4 樣式 (0.0.0.0)。 |
| **MSSQL_BACKUP_DIR** | 設定預設備份目錄位置。 |
| **MSSQL_DATA_DIR** | 變更的目錄會建立新的 SQL Server 資料庫資料檔案 (.mdf)。 |
| **MSSQL_LOG_DIR** | 變更建立新的 SQL Server 資料庫記錄檔 (.ldf) 檔案所在的目錄。 |
| **MSSQL_DUMP_DIR** | 變更其中 SQL Server 會存入記憶體傾印和其他疑難排解的檔案預設的目錄。 |
| **MSSQL_ENABLE_HADR** | 啟用可用性群組。 例如，'1' 已啟用，而 '0' 會停用 |
| **MSSQL_AGENT_ENABLED** | 啟用 SQL Server 代理程式。 例如，啟用 'true' 和 'false' 的已停用。 根據預設，代理程式已停用。  |
| **MSSQL_MASTER_DATA_FILE** | 設定 master 資料庫資料檔案的位置。 |
| **MSSQL_MASTER_LOG_FILE** | 設定 master 資料庫記錄檔的位置。 |
| **MSSQL_ERROR_LOG_FILE** | 設定錯誤記錄檔的位置。 |


## <a name="example-initial-setup"></a>範例： 初始設定

這個範例會執行`mssql-conf setup`設定環境變數。 指定下列環境變數：

- **ACCEPT_EULA**接受使用者授權合約。
- **MSSSQL_PID**指定免費授權開發人員版本的 SQL Server 非生產環境中使用。
- **MSSQL_SA_PASSWORD**設定強式密碼。
- **MSSQL_TCP_PORT**設定 SQL Server 接聽 1234年的 TCP 連接埠。

```bash
sudo ACCEPT_EULA='Y' MSSQL_PID='Developer' MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' MSSQL_TCP_PORT=1234 /opt/mssql/bin/mssql-conf setup
```

## <a name="example-docker"></a>範例： Docker

此範例中的 docker 命令會使用下列環境變數，建立新的 SQL Server 2017 容器：

- **ACCEPT_EULA**接受使用者授權合約。
- **MSSSQL_PID**指定免費授權開發人員版本的 SQL Server 非生產環境中使用。
- **MSSQL_SA_PASSWORD**設定強式密碼。
- **MSSQL_TCP_PORT**設定 SQL Server 接聽 1234年的 TCP 連接埠。 這表示，而不是對應連接埠 1433 （預設值） 的主機連接埠，自訂的 TCP 連接埠必須與對應`-p 1234:1234`在此範例中的命令。

如果您在 Linux/macOS 上執行 Docker，請以單引號中使用下列語法：

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID='Developer' -e MSSQL_SA_PASSWORD='<YourStrong!Passw0rd>' -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

如果您在 Windows 上執行 Docker，請使用下列語法使用雙引號括住：

```bash
docker run -e ACCEPT_EULA=Y -e MSSQL_PID="Developer" -e MSSQL_SA_PASSWORD="<YourStrong!Passw0rd>" -e MSSQL_TCP_PORT=1234 -p 1234:1234 -d microsoft/mssql-server-linux:2017-latest
```

> [!NOTE]
> 在容器中執行生產版本的程序將有些微差異。 如需詳細資訊，請參閱[執行生產容器映像](sql-server-linux-configure-docker.md#production)。

## <a name="next-steps"></a>後續步驟

如需此處未列出其他 SQL Server 設定，請參閱[在 Linux 上使用 mssql-conf 工具的 設定 SQL Server](sql-server-linux-configure-mssql-conf.md)。

如需有關如何安裝和執行在 Linux 上的 SQL Server 的詳細資訊，請參閱 < [Linux 上安裝 SQL Server](sql-server-linux-setup.md)。
