---
title: Creare un'applicazione .NET per Apache Spark in Windows
description: Informazioni su come creare l'applicazione .NET per Apache Spark in Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: how-to
ms.openlocfilehash: cb7154185fc9aa08bc447cb846798995301a6651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185752"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a>Scopri come creare l'applicazione .NET per Apache Spark in Windows

Questo articolo illustra come creare le applicazioni .NET for Apache Spark in Windows.

## <a name="prerequisites"></a>Prerequisites

Se si dispone già di tutti i prerequisiti seguenti, passare alle istruzioni di [compilazione.](#build)

  1. Scaricare e installare **[.NET Core SDK:](https://dotnet.microsoft.com/download/dotnet-core/2.1)** l'installazione dell'SDK aggiungerà la `dotnet` toolchain al percorso. .NET Core 2.1, 2.2 e 3.1 sono supportati.
  2. Installare **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (versione 16.3 o successiva). La versione Community è completamente gratuita. Quando si configura l'installazione, includere almeno questi componenti:
     * Sviluppo per desktop .NET
       * Tutti i componenti necessari
         * Strumenti di sviluppo per .NET Framework 4.6.1
     * Sviluppo multipiattaforma .NET Core
       * Tutti i componenti necessari
  3. Installare **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.
     - Selezionare la versione appropriata per il sistema operativo in uso. Ad esempio, *jdk-8u201-windows-x64.exe* per computer Windows x64.
     - Eseguire l'installazione utilizzando il programma `java` di installazione e verificare che sia possibile eseguire dalla riga di comando.
  4. Installare **[Apache Maven 3.6.0](https://maven.apache.org/download.cgi)**.
     - Scaricare [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.zip).
     - Estrarre i file in una directory locale. Ad esempio, "C:"bin" apache-maven-3.6.0\*.
     - Aggiungere Apache Maven alla [variabile di ambiente PATH](https://www.java.com/en/download/help/path.xml). Ad esempio, *C:.bin apache-maven-3.6.0.bin*.
     - Verificare di essere `mvn` stati eseguiti dalla riga di comando.
  5. Installare **[Apache Spark 2.3](https://spark.apache.org/downloads.html)**.
     - Scaricare [Apache Spark 2.3](https://spark.apache.org/downloads.html) ed estrarlo in una cartella locale (ad esempio, *C:\* [7-zip](https://www.7-zip.org/) (Le versioni di spark supportate sono 2.3.*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)
     - Aggiungere una [nuova variabile](https://www.java.com/en/download/help/path.xml) `SPARK_HOME`di ambiente . Ad esempio, spark-2.3.2-bin-hadoop2.7\*.

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\
       ```

     - Aggiungere Apache Spark alla [variabile di ambiente PATH](https://www.java.com/en/download/help/path.xml). Ad esempio, *C:.bin spark-2.3.2-bin-hadoop2.7.bin*.

       ```powershell
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```

     - Verificare di essere `spark-shell` stati eseguiti dalla riga di comando.
        Output della console di esempio:

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. Installare **[WinUtils](https://github.com/steveloughran/winutils)**.
     - Scaricare `winutils.exe` il file binario dal [repository WinUtils](https://github.com/steveloughran/winutils). È necessario selezionare la versione di Hadoop con cui è stata compilata la distribuzione Spark. Per exammple, utilizzare hadoop-2.7.1 per Spark 2.3.2.
     - Salvare `winutils.exe` il file binario in una directory di propria scelta. Ad esempio, *C:.*
     - Impostare `HADOOP_HOME` per riflettere la directory con winutils.exe (senza bin). Ad esempio, utilizzando la riga di comando:

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - Impostare la variabile `%HADOOP_HOME%\bin`di ambiente PATH in modo da includere . Ad esempio, utilizzando la riga di comando:

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

Assicurarsi di essere `dotnet`in `java` `mvn`grado `spark-shell` di eseguire , , , dalla riga di comando prima di passare alla sezione successiva. Senti che c'è un modo migliore? [Apri un problema](https://github.com/dotnet/spark/issues) e sentiti libero di contribuire.

> [!NOTE]
> Se sono state aggiornate variabili di ambiente, potrebbe essere necessaria una nuova istanza della riga di comando.

## <a name="build"></a>Compilare

Per il resto di questa guida, è necessario aver clonato il repository .NET per Apache Spark nel computer. È possibile scegliere qualsiasi posizione per il repository clonato. Ad esempio, spark di sè\*:

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a>Creare il livello delle estensioni .NET for Apache Spark Scala

Quando si invia un'applicazione .NET, .NET per Apache Spark dispone della logica necessaria scritta in Scala che informa Apache Spark come gestire le richieste (ad esempio, richiedere di creare una nuova sessione Spark, richiedere di trasferire i dati dal lato .NET al lato JVM e così via). Questa logica è disponibile in [.NET per Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).

Indipendentemente dal fatto che si utilizzi .NET Framework o .NET Core, sarà necessario compilare il livello di estensione di .NET per Apache Spark Scala:

```powershell
cd src\scala
mvn clean package
```

Dovresti vedere i file JAR creati per le versioni Spark supportate:

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a>Compilare .NET per le applicazioni di esempio SparkBuild the .NET for Spark sample applications

In questa sezione viene illustrato come compilare le applicazioni di [esempio](https://github.com/dotnet/spark/tree/master/examples) per .NET per Apache Spark. Questi passaggi consentono di comprendere il processo di compilazione generale per qualsiasi .NET per l'applicazione Spark.These steps will help in understanding the overall building process for any .NET for Spark application.

#### <a name="using-visual-studio-for-net-framework"></a>Utilizzo di Visual Studio per .NET Framework

  1. Aprire `src\csharp\Microsoft.Spark.sln` in Visual Studio `Microsoft.Spark.CSharp.Examples` e `examples` compilare il progetto nella cartella (questo a sua volta compilare anche il progetto di associazioni .NET). Se si desidera, è possibile scrivere `Microsoft.Spark.Examples` il proprio codice nel progetto (il 'input_file.json' in questo esempio è un file json con i dati con cui si desidera creare il frame di dati):
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     Una volta completata la compilazione, verranno visualizzati i file binari appropriati prodotti nella directory di output.
     Output della console di esempio:

      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```

#### <a name="using-net-core-cli-for-net-core"></a>Uso dell'interfaccia della riga di comando di .NET Core per .NET CoreUsing .NET Core CLI for .NET Core

> [!NOTE]
> Attualmente stiamo lavorando sull'automazione delle build di .NET Core per Spark .NET. Fino ad allora, apprezziamo la vostra pazienza nell'eseguire alcuni dei passaggi manualmente.

  1. Creare il worker:

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Output della console di esempio:

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```

  2. Compilare gli esempi:Build the samples:

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```

      Output della console di esempio:

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```

## <a name="run-the-net-for-spark-sample-applications"></a>Eseguire .NET per le applicazioni di esempio SparkRun the .NET for Spark sample applications

Una volta compilati gli esempi, `spark-submit` eseguirli avverrà indipendentemente dal fatto che la destinazione sia .NET Framework o .NET Core. Assicurarsi di aver seguito la sezione [dei prerequisiti](#prerequisites) e di aver installato Apache Spark.

  1. Impostare `DOTNET_WORKER_DIR` `PATH` la variabile di ambiente `Microsoft.Spark.Worker` o in modo da includere il percorso in cui è stato generato il file binario (ad esempio, *C:* *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish*

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. Aprire Powershell e passare alla directory in cui è stato generato il file binario dell'app (ad esempio, *C:* *C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish*

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. L'esecuzione dell'app segue la struttura di base:

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     Ecco alcuni esempi che puoi eseguire:

     - **[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessibile)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - **[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**

         ```powershell
         spark-submit.cmd
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
