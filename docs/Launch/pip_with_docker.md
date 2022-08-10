## Launch pip-installed Deephaven with Docker

The pip-installed Deephaven uses a light-weight Deephaven installation that is installed using pip.  In this case,
the pip-installed Deephaven system is installed in a Docker container.

1) Launch [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).
2) Accept incoming connections to [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).  (May not be required for all sessions.)
![](https://github.com/deephaven-examples/deephaven-ib/blob/main/docs/assets/allow-connections.png)
3) Create a directory for your data and scripts
    ```bash
    mkdir data
    ```
4) Launch the system (Option 1):
    * On Mac:
    ```bash
    git clone git@github.com:deephaven-examples/deephaven-ib.git
    cd deephaven-ib/docker/dev/build.sh
    # Set jvm_args to the desired JVM memory for Deephaven
    docker run -it -v data:/data -p 10000:10000 deephaven-examples/deephaven-ib:dev python3 -i -c "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    ```
    * On other platforms:
    ```bash
    # Set jvm_args to the desired JVM memory for Deephaven
    docker run -it -v data:/data -p 10000:10000 ghcr.io/deephaven-examples/deephaven-ib python3 -i -c "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    ```
5) Launch the system and execute a custom script (Option 2):
    * On Mac:
    ```bash
    git clone git@github.com:deephaven-examples/deephaven-ib.git
    cd deephaven-ib/docker/dev/build.sh
    # your_script.py must begin with: "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    # Set jvm_args to the desired JVM memory for Deephaven
    cp path/to/your_script.py data/your_script.py
    docker run -it -v data:/data -p 10000:10000 deephaven-examples/deephaven-ib:dev python3 -i /data/your_script.py
    ```
    * On other platforms:
    ```bash
    # your_script.py must begin with: "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    # Set jvm_args to the desired JVM memory for Deephaven
    cp path/to/your_script.py data/your_script.py
    docker run -it -v data:/data -p 10000:10000 ghcr.io/deephaven-examples/deephaven-ib python3 -i /data/your_script.py
    ```
7) Launch the [Deephaven IDE](https://github.com/deephaven/deephaven-core/blob/main/README.md#run-deephaven-ide) by navigating to [http://localhost:10000/ide/](http://localhost:10000/ide/) in a browser.