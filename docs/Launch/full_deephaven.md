## Launch the full Deephaven system

> **_NOTE:_**  Deephaven does not yet have published Docker images for all architectures.  This launch should work on Linux (AMD64 and ARM64), Mac (Intel), and Windows WSL.  It is not yet supported on Windows without WSL or Mac (M1 and M2). In these cases, the `full_web_1` Docker image will exit.  This can be seen using `docker ps` or `docker compose ps`.  For these architectures, you will need to build Deephaven Docker images locally.  See [Build and launch from source](https://deephaven.io/core/docs/how-to-guides/launch-build/).


The full Deephaven system contains the most full-featured IDE.  Running the full Deephaven system launches multiple Docker
containers, so it has the most overhead.

See [docker/full](../../docker/full/) for more details.

1) Launch [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).
2) Accept incoming connections to [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).  (May not be required for all sessions.)
![](https://github.com/deephaven-examples/deephaven-ib/blob/main/docs/assets/allow-connections.png)
3) Launch the system:
    ```bash
    cd ./docker/full/
    ./run_system.sh
    ```
4) Copy your data and scripts into `./data/`
5) Launch the [Deephaven IDE](https://github.com/deephaven/deephaven-core/blob/main/README.md#run-deephaven-ide) by navigating to [http://localhost:10000/ide/](http://localhost:10000/ide/) in a browser.