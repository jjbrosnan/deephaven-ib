## Launch pip-installed Deephaven with a local installation (No Docker)

> **_NOTE:_**  Deephaven pip install is not yet supported on all architectures.  This launch should work on Linux (AMD64 and ARM64) and Windows WSL.  It is not yet supported on Windows without WSL or Mac.  For these architectures, you should use the Docker installation.  As soon as Deephaven supports these architectures for pip, [deephaven-ib](https://github.com/deephaven-examples/deephaven-ib) will work.

The pip-installed Deephaven uses a light-weight Deephaven installation that is installed using pip.  In this case,
the pip-installed Deephaven system is installed directly on your local system, without Docker.

It is possible to use [deephaven-ib](https://github.com/deephaven-examples/deephaven-ib) without docker, but this is a 
new feature and has not been well tested.  To do this:
1) Launch [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).
2) Accept incoming connections to [IB Trader Workstation (TWS)](https://www.interactivebrokers.com/en/trading/tws.php).  (May not be required for all sessions.)
![](https://github.com/deephaven-examples/deephaven-ib/blob/main/docs/assets/allow-connections.png)
3) Install `ibapi`:
    ```bash
    # pip installed version of ibapi is too old.  You must download and install a more recent version.
    export IB_VERSION=1016.01
    curl -o ./api.zip "https://interactivebrokers.github.io/downloads/twsapi_macunix.${IB_VERSION}.zip"
    unzip api.zip
    cd ./IBJts/source/pythonclient
    python3 setup.py install
    ```
4) Install [deephaven-ib](https://github.com/deephaven-examples/deephaven-ib):
    ```bash
    pip3 install --upgrade pip setuptools wheel
    pip3 install deephaven-ib
    ```
5) Install Java 11 and set the appropriate `JAVA_HOME` environment variable.    
6) Launch the system (Option 1):
    ```bash
    # Set jvm_args to the desired JVM memory for Deephaven
    python3 -i -c "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    ```
7) Launch the system and execute a custom script (Option 2):
    ```bash
    # your_script.py must begin with: "from deephaven_server import Server; _server = Server(port=10000, jvm_args=['-Xmx4g']); _server.start()"
    # Set jvm_args to the desired JVM memory for Deephaven
    python3 -i /data/your_script.py
    ```
8) Launch the [Deephaven IDE](https://github.com/deephaven/deephaven-core/blob/main/README.md#run-deephaven-ide) by navigating to [http://localhost:10000/ide/](http://localhost:10000/ide/) in a browser.
9) Use `host=localhost` for the hostname in the examples