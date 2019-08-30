---
title: Distribuire un'applicazione .NET per Apache Spark in Databricks
description: Informazioni su come distribuire un'applicazione .NET per Apache Spark in Databricks.
ms.date: 05/17/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ca9e93a413622c84325ca9fc8bac17268b990c5a
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "69576968"
---
# <a name="deploy-a-net-for-apache-spark-application-to-databricks"></a><span data-ttu-id="cc5e2-103">Distribuire un'applicazione .NET per Apache Spark in Databricks</span><span class="sxs-lookup"><span data-stu-id="cc5e2-103">Deploy a .NET for Apache Spark application to Databricks</span></span>

<span data-ttu-id="cc5e2-104">Questa esercitazione illustra come distribuire un'applicazione .NET per Apache Spark in Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-104">This tutorial teaches how to deploy a .NET for Apache Spark application to Databricks.</span></span>

<span data-ttu-id="cc5e2-105">In questa esercitazione si imparerà a:</span><span class="sxs-lookup"><span data-stu-id="cc5e2-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="cc5e2-106">Preparare Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="cc5e2-106">Prepare Microsoft.Spark.Worker</span></span>
> * <span data-ttu-id="cc5e2-107">Pubblicare l'app Spark .NET</span><span class="sxs-lookup"><span data-stu-id="cc5e2-107">Publish your Spark .NET app</span></span>
> * <span data-ttu-id="cc5e2-108">Distribuire l'app in Databricks</span><span class="sxs-lookup"><span data-stu-id="cc5e2-108">Deploy your app to Databricks</span></span>
> * <span data-ttu-id="cc5e2-109">Eseguire l'app</span><span class="sxs-lookup"><span data-stu-id="cc5e2-109">Run your app</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc5e2-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="cc5e2-110">Prerequisites</span></span>

<span data-ttu-id="cc5e2-111">Prima di iniziare, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cc5e2-111">Before you start, do the following:</span></span>

* <span data-ttu-id="cc5e2-112">Scaricare l'[interfaccia della riga di comando di Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-112">Download the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>
* <span data-ttu-id="cc5e2-113">Scaricare [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-113">Download [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to your local machine.</span></span> <span data-ttu-id="cc5e2-114">Si tratta di uno script helper che verrà usato in seguito per copiare i file dipendenti di .NET per Apache Spark nei nodi di lavoro del cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-114">This is a helper script that you use later to copy .NET for Apache Spark dependent files into your Spark cluster's worker nodes.</span></span>

## <a name="prepare-worker-dependencies"></a><span data-ttu-id="cc5e2-115">Preparare le dipendenze dei nodi di lavoro</span><span class="sxs-lookup"><span data-stu-id="cc5e2-115">Prepare worker dependencies</span></span>

<span data-ttu-id="cc5e2-116">**Microsoft. Spark.Worker** è un componente back-end che risiede nei singoli nodi di lavoro del cluster Spark.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-116">**Microsoft.Spark.Worker** is a back-end component that lives on the individual worker nodes of your Spark cluster.</span></span> <span data-ttu-id="cc5e2-117">Quando si vuole eseguire una funzione definita dall'utente C#, Spark deve comprendere come avviare CLR .NET per eseguire la funzione definita dall'utente.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-117">When you want to execute a C# UDF (user-defined function), Spark needs to understand how to launch the .NET CLR to execute the UDF.</span></span> <span data-ttu-id="cc5e2-118">**Microsoft. Spark.Worker** offre una raccolta di classi per Spark che consentono di abilitare questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-118">**Microsoft.Spark.Worker** provides a collection of classes to Spark that enable this functionality.</span></span>

1. <span data-ttu-id="cc5e2-119">Selezionare una versione netcoreapp Linux di [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) da distribuire nel cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-119">Select a [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) Linux netcoreapp release to be deployed on your cluster.</span></span>

   <span data-ttu-id="cc5e2-120">Ad esempio, se si vuole usare `.NET for Apache Spark v0.1.0` con `netcoreapp2.1`, scaricare [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-120">For example, if you want `.NET for Apache Spark v0.1.0` using `netcoreapp2.1`, you'd download [Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz](https://github.com/dotnet/spark/releases/download/v0.1.0/Microsoft.Spark.Worker.netcoreapp2.1.linux-x64-0.1.0.tar.gz).</span></span>

2. <span data-ttu-id="cc5e2-121">Caricare `Microsoft.Spark.Worker.<release>.tar.gz` e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) in un file system distribuito (ad esempio, DBFS) a cui può accedere il cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-121">Upload `Microsoft.Spark.Worker.<release>.tar.gz` and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh) to a distributed file system (for example, DBFS) that your cluster has access to.</span></span>

## <a name="prepare-your-net-for-apache-spark-app"></a><span data-ttu-id="cc5e2-122">Preparare .NET per l'app Apache Spark</span><span class="sxs-lookup"><span data-stu-id="cc5e2-122">Prepare your .NET for Apache Spark app</span></span>

1. <span data-ttu-id="cc5e2-123">Per creare l'app, seguire l'esercitazione [Introduzione](get-started.md).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-123">Follow the [Get Started](get-started.md) tutorial to build your app.</span></span>

2. <span data-ttu-id="cc5e2-124">Pubblicare l'app Spark .NET come indipendente.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-124">Publish your Spark .NET app as self-contained.</span></span>

   <span data-ttu-id="cc5e2-125">In Linux è possibile eseguire il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-125">You can run the following command on Linux.</span></span>

   ```bash
   dotnet publish -c Release -f netcoreapp2.1 -r ubuntu.16.04-x64
   ```

3. <span data-ttu-id="cc5e2-126">Produrre `<your app>.zip` per i file pubblicati.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-126">Produce `<your app>.zip` for the published files.</span></span>

   <span data-ttu-id="cc5e2-127">In Linux è possibile eseguire il comando seguente con `zip`.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-127">You can run the following command on Linux using `zip`.</span></span>

   ```bash
   zip -r <your app>.zip .
   ```

4. <span data-ttu-id="cc5e2-128">Caricare il file seguente in un file system distribuito (ad esempio, DBFS) a cui può accedere il cluster:</span><span class="sxs-lookup"><span data-stu-id="cc5e2-128">Upload the following to a distributed file system (for example, DBFS) that your cluster has access to:</span></span>

   * <span data-ttu-id="cc5e2-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: Questo file jar è incluso nel pacchetto NuGet [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) e viene posizionato nella directory di output di compilazione dell'app.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-129">`microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar`: This jar is included as part of the [Microsoft.Spark](https://www.nuget.org/packages/Microsoft.Spark/) NuGet package and is colocated in your app's build output directory.</span></span>
   * `<your app>.zip`
   * <span data-ttu-id="cc5e2-130">I file (come i file di dipendenza o i dati comuni accessibili a ogni ruolo di lavoro) o gli assembly (ad esempio le DLL che contengono funzioni definite dall'utente o librerie da cui dipende l'app), vengono inseriti nella directory di lavoro di ogni executor.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-130">Files (like dependency files or common data accessible to every worker) or assemblies (like DLLs that contain your user-defined functions or libraries that your app depends on) to be placed in the working directory of each executor.</span></span>

## <a name="deploy-to-databricks"></a><span data-ttu-id="cc5e2-131">Distribuire in Databricks</span><span class="sxs-lookup"><span data-stu-id="cc5e2-131">Deploy to Databricks</span></span>

<span data-ttu-id="cc5e2-132">[Databricks](https://databricks.com) è una piattaforma che offre funzionalità di elaborazione di Big Data basate sul cloud con Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-132">[Databricks](https://databricks.com) is a platform that provides cloud-based big data processing using Apache Spark.</span></span>

> [!Note] 
> <span data-ttu-id="cc5e2-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) e [AWS Databricks](https://databricks.com/aws) sono basati su Linux.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-133">[Azure Databricks](https://azure.microsoft.com/services/databricks/) and [AWS Databricks](https://databricks.com/aws) are Linux-based.</span></span> <span data-ttu-id="cc5e2-134">Per questo motivo, se si è interessati a distribuire l'app in Databricks, assicurarsi che l'app sia compatibile con .NET Standard e che venga usato il [compilatore .NET Core](https://dotnet.microsoft.com/download) per compilare l'app.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-134">Therefore, if you are interested in deploying your app to Databricks, make sure your app is .NET Standard compatible and that you use [.NET Core compiler](https://dotnet.microsoft.com/download) to compile your app.</span></span>

<span data-ttu-id="cc5e2-135">Databricks consente di inviare app .NET per Apache Spark a un cluster attivo esistente o di creare un nuovo cluster ogni volta che viene avviato un processo.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-135">Databricks allows you to submit .NET for Apache Spark apps to an existing active cluster or create a new cluster every time you launch a job.</span></span> <span data-ttu-id="cc5e2-136">A questo scopo, è necessario installare **Microsoft.Spark.Worker** prima di inviare un'app.NET per Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-136">This requires the **Microsoft.Spark.Worker** to be installed before you submit a .NET for Apache Spark app.</span></span>

### <a name="deploy-microsoftsparkworker"></a><span data-ttu-id="cc5e2-137">Distribuire Microsoft.Spark.Worker</span><span class="sxs-lookup"><span data-stu-id="cc5e2-137">Deploy Microsoft.Spark.Worker</span></span>

<span data-ttu-id="cc5e2-138">Questo passaggio è necessario solo una volta per un cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-138">This step is only required once for a cluster.</span></span>

1. <span data-ttu-id="cc5e2-139">Scaricare [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) e [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-139">Download [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) and [install-worker.sh](https://github.com/dotnet/spark/blob/master/deployment/install-worker.sh
) onto your local machine.</span></span>

2. <span data-ttu-id="cc5e2-140">Modificare **db-init.sh** in modo che punti alla versione di **Microsoft.Spark.Worker** che si vuole scaricare e installare nel cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-140">Modify **db-init.sh** to point to the **Microsoft.Spark.Worker** release you want to download and install on your cluster.</span></span>

3. <span data-ttu-id="cc5e2-141">Installare l'[interfaccia della riga di comando di Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-141">Install the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html).</span></span>

4. <span data-ttu-id="cc5e2-142">[Configurare i dettagli dell'autenticazione](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) per l'interfaccia della riga di comando di Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-142">[Setup authentication](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html#set-up-authentication) details for the Databricks CLI.</span></span>

5. <span data-ttu-id="cc5e2-143">Caricare i file nel cluster Databricks con il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="cc5e2-143">Upload the files to your Databricks cluster using the following command:</span></span>

   ```bash
   cd <path-to-db-init-and-install-worker>
   databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
   databricks fs cp install-worker.sh dbfs:/spark-dotnet/install-worker.sh
   ```

6. <span data-ttu-id="cc5e2-144">Passare all'area di lavoro di Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-144">Go to your Databricks workspace.</span></span> <span data-ttu-id="cc5e2-145">Selezionare **Clusters** (Cluster) dal menu a sinistra e quindi selezionare **Create Cluster** (Crea cluster).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-145">Select **Clusters** from the left-side menu, and then select **Create Cluster**.</span></span>

7. <span data-ttu-id="cc5e2-146">Dopo aver configurato il cluster in modo appropriato, **impostare lo script** di inizializzazione e creare il cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-146">After configuring the cluster appropriately, set the **Init Script** and create the cluster.</span></span>

   ![Immagine dell'azione script](./media/databricks-deployment/deployment-databricks-init-script.png)

## <a name="run-your-app"></a><span data-ttu-id="cc5e2-148">Eseguire l'app</span><span class="sxs-lookup"><span data-stu-id="cc5e2-148">Run your app</span></span> 

<span data-ttu-id="cc5e2-149">È possibile usare `set JAR` o `spark-submit` per inviare il processo a Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-149">You can use `set JAR` or `spark-submit` to submit your job to Databricks.</span></span>

### <a name="use-set-jar"></a><span data-ttu-id="cc5e2-150">Usare Set JAR (Imposta JAR)</span><span class="sxs-lookup"><span data-stu-id="cc5e2-150">Use Set JAR</span></span>

<span data-ttu-id="cc5e2-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) (Imposta JAR) consente di inviare un processo a un cluster attivo esistente.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-151">[Set JAR](https://docs.databricks.com/user-guide/jobs.html#create-a-job) allows you to submit a job to an existing active cluster.</span></span>

#### <a name="one-time-setup"></a><span data-ttu-id="cc5e2-152">Installazione singola</span><span class="sxs-lookup"><span data-stu-id="cc5e2-152">One-time setup</span></span>

1. <span data-ttu-id="cc5e2-153">Passare al cluster Databricks e selezionare **Jobs** (Processi) dal menu a sinistra.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-153">Go to your Databricks cluster and select **Jobs** from the left-side menu.</span></span> <span data-ttu-id="cc5e2-154">Selezionare quindi **Set JAR** (Imposta JAR).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-154">Then select **Set JAR**.</span></span>

2. <span data-ttu-id="cc5e2-155">Caricare il file `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` appropriato.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-155">Upload the appropriate `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar` file.</span></span>

3. <span data-ttu-id="cc5e2-156">Impostare i parametri in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-156">Set the parameters appropriately.</span></span>

   ```
   Main Class: org.apache.spark.deploy.DotnetRunner
   Arguments /dbfs/apps/<your-app-name>.zip <your-app-main-class>
   ```
 
4. <span data-ttu-id="cc5e2-157">Configurare il **cluster** in modo che punti al cluster esistente per cui è stato creato lo **script** di inizializzazione nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-157">Configure the **Cluster** to point to the existing cluster you created the **Init Script** for in the previous section.</span></span>

#### <a name="publish-and-run-your-app"></a><span data-ttu-id="cc5e2-158">Pubblicare ed eseguire l'app</span><span class="sxs-lookup"><span data-stu-id="cc5e2-158">Publish and run your app</span></span>

1. <span data-ttu-id="cc5e2-159">Usare l'[interfaccia della riga di comando di Databricks](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) per caricare l'applicazione nel cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-159">Use the [Databricks CLI](https://docs.databricks.com/user-guide/dev-tools/databricks-cli.html) to upload your application to your Databricks cluster.</span></span>

      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
      ```

2. <span data-ttu-id="cc5e2-160">Questo passaggio è necessario solo se gli assembly dell'app, ad esempio le DLL che contengono funzioni definite dall'utente e le relative dipendenze, devono essere posizionati nella directory di lavoro di ogni **Microsoft.Spark.Worker**.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-160">This step is only required if your app assemblies (for example, DLLs that contain user-defined functions along with their dependencies) need to be placed in the working directory of each **Microsoft.Spark.Worker**.</span></span>

   - <span data-ttu-id="cc5e2-161">Caricare gli assembly dell'applicazione nel cluster Databricks</span><span class="sxs-lookup"><span data-stu-id="cc5e2-161">Upload your application assemblies to your Databricks cluster</span></span>
      
      ```bash
      cd <path-to-your-app-publish-directory>
      databricks fs cp <assembly>.dll dbfs:/apps/dependencies
      ```

   - <span data-ttu-id="cc5e2-162">Rimuovere il commento e modificare la sezione relativa alle dipendenze dell'app in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) per puntare al percorso delle dipendenze dell'app ed eseguire il caricamento nel cluster Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-162">Uncomment and modify the app dependencies section in [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) to point to your app dependencies path and upload to your Databricks cluster.</span></span>
   
      ```bash
      cd <path-to-db-init-and-install-worker>
      databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
      ```
   
   - <span data-ttu-id="cc5e2-163">Riavviare il cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-163">Restart your cluster.</span></span>

3. <span data-ttu-id="cc5e2-164">Passare al cluster Databricks nell'area di lavoro di Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-164">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="cc5e2-165">In **Jobs** (Processi) selezionare il processo e quindi selezionare **Run Now** (Esegui adesso) per eseguire il processo.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-165">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

### <a name="use-spark-submit"></a><span data-ttu-id="cc5e2-166">Usare spark-submit</span><span class="sxs-lookup"><span data-stu-id="cc5e2-166">Use spark-submit</span></span>

<span data-ttu-id="cc5e2-167">Il comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) consente di inviare un processo a un nuovo cluster.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-167">The [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) command allows you to submit a job to a new cluster.</span></span>

1. <span data-ttu-id="cc5e2-168">[Creare un processo](https://docs.databricks.com/user-guide/jobs.html) e selezionare **Configure spark-submit** (Configura spark-submit).</span><span class="sxs-lookup"><span data-stu-id="cc5e2-168">[Create a Job](https://docs.databricks.com/user-guide/jobs.html) and select **Configure spark-submit**.</span></span>

2. <span data-ttu-id="cc5e2-169">Configurare `spark-submit` con i parametri seguenti:</span><span class="sxs-lookup"><span data-stu-id="cc5e2-169">Configure `spark-submit` with the following parameters:</span></span>

      ```bash
      ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
      ```

3. <span data-ttu-id="cc5e2-170">Passare al cluster Databricks nell'area di lavoro di Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-170">Go to your Databricks cluster in your Databricks workspace.</span></span> <span data-ttu-id="cc5e2-171">In **Jobs** (Processi) selezionare il processo e quindi selezionare **Run Now** (Esegui adesso) per eseguire il processo.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-171">Under **Jobs**, select your job and then select **Run Now** to run your job.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cc5e2-172">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="cc5e2-172">Next steps</span></span>

<span data-ttu-id="cc5e2-173">In questa esercitazione è stata distribuita un'applicazione .NET per Apache Spark in Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-173">In this tutorial, you deployed your .NET for Apache Spark application to Databricks.</span></span> <span data-ttu-id="cc5e2-174">Per altre informazioni su Databricks, passare alla documentazione di Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="cc5e2-174">To learn more about Databricks, continue to the Azure Databricks Documentation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cc5e2-175">Documentazione di Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="cc5e2-175">Azure Databricks Documentation</span></span>](https://docs.microsoft.com/azure/azure-databricks/)