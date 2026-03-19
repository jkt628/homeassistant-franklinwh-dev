# Debug Home Assistant Core and FranklinWH integration with VSCode

## Setup

Configure the source.

```bash
bash setup
```

## Configuration

If required, run the following or edit into [configuration.yaml](core/config/configuration.yaml).

```bash
cat <<'EOF' >>core/config/configuration.yaml

sensor:
  - platform: franklin_wh
    username: $FRANKLINWH_USERNAME
    password: $FRANKLINWH_PASSWORD
    id: $FRANKLINWH_ID
EOF
```

## Launch VSCode

```bash
(code core >&/dev/null &)
```

[devcontainer]: https://code.visualstudio.com/docs/devcontainers/containers
When asked to relaunch in [devcontainer], choose __Reopen in Container__.
The container will take a good while to build but eventually you can launch a terminal with __Terminal / New Terminal__ and run

```bash
(cd config/deps/franklinwh-python && python -m pip install -e .)
```

Using the Command Palette _Ctrl|Cmd-Shift-P_ execute __Python: Restart Language Server__.

> [!NOTE]
> this is required after every rebuild!

## Debug

The [devcontainer] is configured to debug HA Core and these steps integrate FranklinWH properly so
breakpoints work as expected.

* in the left sidebar click the __Run and Debug__ icon.
* at the top click the __Run__ button to launch HA Core.
* wait for more packages to install.
* open <http://localhost:8123>.
* first time installations require __Create my smart home__.
