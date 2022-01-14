## Rackspace DNS v1 API provider for octoDNS

An [octoDNS](https://github.com/octodns/octodns/) provider that targets [Rackspace DNS](https://www.rackspace.com/library/what-is-dns).

### Installation

#### Command line

```
pip install octodns_rackspace
```

#### requirements.txt/setup.py

Pinning specific versions or SHAs is recommended to avoid unplanned upgrades.

##### Versions

```
# Start with the latest versions and don't just copy what's here
octodns==0.9.14
octodns_rackspace==0.0.1
```

##### SHAs

```
# Start with the latest/specific versions and don't just copy what's here
-e git+https://git@github.com/octodns/octodns.git@9da19749e28f68407a1c246dfdf65663cdc1c422#egg=octodns
-e git+https://git@github.com/octodns/octodns_rackspace.git@ec9661f8b335241ae4746eea467a8509205e6a30#egg=octodns_rackspace
```

### Configuration

```yaml
providers:
  rackspace:
    class: octodns_rackspace.RackspaceProvider
    # The the username to authenticate with (required)
    username: env/RACKSPACE_USERNAME
    # The api key that grants access for that user (required)
    api_key: env/RACKSPACE_API_KEY
```

### Support Information

#### Records

RackspaceProvider supports A, AAAA, ALIAS, CNAME, MX, NS, PTR, SPF, and TXT

#### Dynamic

RackspaceProvider does not support dynamic records.

### Development

See the [/script/](/script/) directory for some tools to help with the development process. They generally follow the [Script to rule them all](https://github.com/github/scripts-to-rule-them-all) pattern. Most useful is `./script/bootstrap` which will create a venv and install both the runtime and development related requirements. It will also hook up a pre-commit hook that covers most of what's run by CI.
