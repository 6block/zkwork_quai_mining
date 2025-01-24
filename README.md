# ZKWROK_QUAI_MINING
 * pool_address=quai.asia.zk.work:13333


## Mining Tutorial
**Recommend Miner**
  * quai_gpu_miner: https://github.com/dominant-strategies/quai-gpu-miner/releases
  * SRBMiner: https://github.com/doktor83/SRBMiner-Multi/releases


## quai_gpu_miner

- Version: [v0.4.1+](https://github.com/dominant-strategies/quai-gpu-miner/releases)

**On Ubuntu**

1. Get a ZKWORK_API_TOKEN on [ZK.WROK](https://v2.zk.work/).
2. Download quai gpu miner: https://github.com/dominant-strategies/quai-gpu-miner/releases.
3. Create a script: `vi quai_mining.sh`.
    ```shell
    #!/bin/bash

    ./quai-gpu-miner -U --HWMON 1 -P stratum://<ZKWORK_API_TOKEN>.<CUSTOM_NAME>:x@quai.asia.zk.work:13333
    ```
5. Update your ZKWORK_API_TOKEN in `quai_mining.sh` and set CUSTOM_NAME for mining server.
6. Start mining with `sudo chmod +x quai_mining.sh && nohup ./quai_mining.sh >> mining.log 2>&1 &`.
7. Check mining log with `tail -f mining.log`.

**On HiveOS**

1. Choose your download url for your gpu.
  * DOWNLOAD_URL for Nvidia: https://github.com/dominant-strategies/quai-gpu-miner/releases/download/v0.4.1/quai-gpu-miner-nvidia-v0.4.1.tar.gz
  * DOWNLOAD_URL for AMD: https://github.com/dominant-strategies/quai-gpu-miner/releases/download/v0.4.1/quai-gpu-miner-amd-v0.4.1.tar.gz
2. Get a ZKWORK_API_TOKEN on [ZK.WROK](https://v2.zk.work/) as QUAI wallet address.
3. Add New Flight Sheet with config as follows.

Configuration:
- Installation URL: DOWNLOAD_URL
- Hash algorithm: progpow
- Wallet and worker template: %WAL%
- Extra config arguments: -U --HWMON 1 -P stratum://%WAL%.%WORKER_NAME%:x@quai.asia.zk.work:13333

3. Start Flight Sheet

### SRBMiner

- Version: [v2.7.5+](https://github.com/doktor83/SRBMiner-Multi/releases)

**On Ubuntu**

1. Get a ZKWORK_API_TOKEN on [ZK.WROK](https://v2.zk.work/).
2. Download quai gpu miner: https://github.com/doktor83/SRBMiner-Multi/releases.
3. Create a script: `vi quai_mining.sh`.
    ```shell
    export GPU_MAX_HEAP_SIZE=100
    export GPU_MAX_USE_SYNC_OBJECTS=1
    export GPU_SINGLE_ALLOC_PERCENT=100
    export GPU_MAX_ALLOC_PERCENT=100
    export GPU_MAX_SINGLE_ALLOC_PERCENT=100
    export GPU_ENABLE_LARGE_ALLOCATION=100
    export GPU_MAX_WORKGROUP_SIZE=1024
    #!/bin/sh
    reset

    ./SRBMiner-MULTI --disable-cpu --algorithm progpow_quai --pool quai.asia.zk.work:13333 --wallet <ZKWORK_API_TOKEN>.<CUSTOM_NAME>
    ```
4. Update your QUAI ZKWORK_API_TOKEN in `quai_mining.sh` and set CUSTOM_NAME for mining server.
5. Start mining with `sudo chmod +x quai_mining.sh && nohup ./quai_mining.sh >> mining.log 2>&1 &`.
6. Check mining log with `tail -f mining.log`.

**On HiveOS**

1. Choose your download url for your gpu.
  * DOWNLOAD_URL: https://github.com/doktor83/SRBMiner-Multi/releases/download/2.7.5/srbminer_custom-2.7.5.tar.gz

2. Get a ZKWORK_API_TOKEN on [ZK.WROK](https://v2.zk.work/) as QUAI wallet address.
3. Add New Flight Sheet with config as follows.

Configuration:
- Installation URL: DOWNLOAD_URL
- Hash algorithm: progpow_quai
- Wallet and worker template: %WAL%
- Extra config arguments: --algorithm progpow_quai --disable-cpu --pool quai.asia.zk.work:13333 --wallet %WAL%.%WORKER_NAME% --password x

3. Start Flight Sheet

