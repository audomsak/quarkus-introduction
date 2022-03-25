# Introduction To Quarkus

## Prerequisites

1. Docker
2. JDK 11+
3. GraalVM 21.3.0+
4. Maven
5. OpenShift Container Platform

## Demo Scenarios

### 1. Let Me Show You

Purpose

This demo aims to show you a comparison between Quarkus and Spring Boot applications how Quarkus is faster, smaller, and more lightweight (low memory consumptions) in JVM running mode.

<details>
<summary>Demo Steps</summary>

> **_Speaker Note_**
>
> You can quickly show the code of both projects before starting this demo.

1. Go to top level of this directory (`quarkus-introduction`).

2. Build and package both applications.

   _Spring Boot:_

   ```sh
   mvn clean install package -DskipTests -f let-me-show-you/spring-demo
   ```

   _Quarkus:_

   ```sh
   mvn clean install package -DskipTests -Dquarkus.package.type=uber-jar -f let-me-show-you/quarkus-demo
   ```

3. Compare the application artefacts size in the `target` dicrectory in each project. **Quarkus application should be smaller than Spring Boot**.

   _Spring Boot:_

   ```sh
   ls -lh let-me-show-you/spring-demo/target
   ...
   -rw-r--r--  1 dom  staff    17M Mar 24 23:53 spring-demo-0.0.1-SNAPSHOT.jar
   ...
   ```

   _Quarkus:_

   ```sh
   ls -lh let-me-show-you/quarkus-demo/target
   ...
   -rw-r--r--   1 dom  staff   156K Mar 25 00:29 quarkus-demo-1.0.0-SNAPSHOT-runner.jar
   ...
   ```

4. Run both applications in separate terminal windows.

   _Spring Boot:_

   ```sh
   java -jar let-me-show-you/spring-demo/target/spring-demo-0.0.1-SNAPSHOT.jar
   ```

   _Quarkus:_

   ```sh
   java -jar let-me-show-you/quarkus-demo/target/quarkus-demo-1.0.0-SNAPSHOT-runner.jar
   ```

   ![image](images/let-me-show-you-1.png)

5. Look for both application startup times in the logs to compare them. **Quarkus should be faster than Spring Boot.**

6. Run [jps](https://docs.oracle.com/en/java/javase/11/tools/jps.html) command in a new terminal window to get Java process ID of both applications.

   ```sh
   jps

   33045 spring-demo-0.0.1-SNAPSHOT.jar
   33053 quarkus-demo-1.0.0-SNAPSHOT-runner.jar
   ...
   ```

7. Use [jhsdb](https://docs.oracle.com/en/java/javase/11/tools/jhsdb.html) command to get heap information of both applications. Replace the `<PID>` with the process ID from `jps` command output above. Then look at `G1 Heap` section and the `used` attribute (See sample output below.) Then compare the value from both applications. **Quarkus appliation should use less memory than Spring Boot application.**

   **_Note._** Building Quarkus applicaiton using [fast-jar](https://quarkus.io/guides/maven-tooling#fast-jar) will cause the application consumes slightly less memory than the legacy jar and uber jar.

   _Command:_

   ```sh
   jhsdb jmap --heap --pid <PID>
   ```

   _Sample output:_

   ```sh
   Attaching to process ID 33053, please wait...
   Debugger attached successfully.
   Server compiler detected.
   JVM version is 11.0.13+7-jvmci-21.3-b05

   using thread-local object allocation.
   Garbage-First (G1) GC with 8 thread(s)

   Heap Configuration:
      MinHeapFreeRatio         = 40
      MaxHeapFreeRatio         = 70
      MaxHeapSize              = 8589934592 (8192.0MB)
      NewSize                  = 1363144 (1.2999954223632812MB)
      MaxNewSize               = 5152702464 (4914.0MB)
      OldSize                  = 5452592 (5.1999969482421875MB)
      NewRatio                 = 2
      SurvivorRatio            = 8
      MetaspaceSize            = 21807104 (20.796875MB)
      CompressedClassSpaceSize = 1073741824 (1024.0MB)
      MaxMetaspaceSize         = 17592186044415 MB
      G1HeapRegionSize         = 2097152 (2.0MB)

   Heap Usage:
   G1 Heap:
      regions  = 4096
      capacity = 8589934592 (8192.0MB)
      used     = 76087088 (72.56230163574219MB)
      free     = 8513847504 (8119.437698364258MB)
      0.885770283639431% used
   G1 Young Generation:
   Eden Space:
      regions  = 34
      capacity = 333447168 (318.0MB)
      used     = 71303168 (68.0MB)
      free     = 262144000 (250.0MB)
      21.38364779874214% used
   Survivor Space:
      regions  = 2
      capacity = 4194304 (4.0MB)
      used     = 4194304 (4.0MB)
      free     = 0 (0.0MB)
      100.0% used
   G1 Old Generation:
      regions  = 2
      capacity = 203423744 (194.0MB)
      used     = 589616 (0.5623016357421875MB)
      free     = 202834128 (193.4376983642578MB)
      0.2898462039908183% used
   ```

[↩ back to top](#1-let-me-show-you)
</details>

### 2. CLI Tooling

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#2-cli-tooling)
</details>

### 3. Dev UI

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#3-dev-ui)
</details>

### 4. Live Coding

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#4-live-coding)
</details>

### 5. Dev Services

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#5-dev-services)
</details>

### 6. Native Executable

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#6-native-executable)
</details>

### 7. Build Container Image

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#7-build-container-image)
</details>

### 8. Kubernetes Native

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#8-kubernetes-native)
</details>

### 9. Spring Boot On Quarkus

Purpose

<details>
<summary>Demo Steps</summary>

[↩ back to top](#9-spring-boot-on-quarkus)
</details>
