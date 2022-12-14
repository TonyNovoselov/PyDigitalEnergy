PyDigitalEnergy is a Python package that allows for simple access to Digital Energy virtualization management platform API.

## Installation

PyDigitalEnergy is supported on Python 3.7+. The recommended way to install is via [pip](https://pypi.python.org/pypi/pip).

```python
pip install pydigitalenergy
```

For instructions on installing Python and pip see “The Hitchhiker’s Guide to Python” [Installation Guides](https://docs.python-guide.org/en/latest/starting/installation/).

## Structure overview

Since **Digital Energy** is a virtualization management platform. Here you can see high-level structure:

```bash
└── Grid (Data Center) 		# Logical entity that defines the set of resources
  └── Grid Node(CLuster) 	# Logical grouping of hosts
    └── Stack (Host) 		# Also known as hypervisors, are the physical servers
      └── Compute (Virtual Machine)
```


## Quickstart

Assuming you already have a credentials you can instantiate an instance of DigitalEnergyAPI like so:

```python
from pydigitalenergy import DigitalEnergyApi

api = DigitalEnergyApi(
    hostname = 'Digital Energy host',
    client_id = 'Your identifier',
    client_secret = 'Your secret key'
)
```

With the `api` instance you can then interact with Digital Energy. Below you can find couple of examples.

**Computes/Virtual machines**

In computing, a virtual machine (VM) is the virtualization/emulation of a computer system.

```python
# Get list of computes
computes = api.cloudbroker.computes.list()

# Or you can use more convenient alias
vms = api.cloudbroker.virtual_machines.list()

# To get one particular instance you should use .get() method
# For example with ID = 42
vm = api.cloudbroker.virtual_machines.get(42)
```

**Stacks/Hosts**

Hosts, also known as hypervisors, are the physical servers on which virtual machines run

```python
# Get list of stacks
stacks = api.cloudbroker.stacks.list()

# Or you can use more convenient alias
hosts = api.cloudbroker.hosts.list()

# To get one particular instance you should use .get() method
# For example with ID = 4
host = api.cloudbroker.hosts.get(4)
```

**Nodes/Clusters**

A cluster is a logical grouping of hosts that share the same storage domains and have the same type of CPU

```python
# Get list of nodes
nodes = api.cloudbroker.nodes.list()

# Or you can use more convenient alias
clusters = api.cloudbroker.clusters.list()

# To get one particular instance you should use .get() method
# For example with ID = 10
cluster = api.cloudbroker.clusters.get(10)
```

**Grids/Data centers**

A data center is a logical entity that defines the set of resources used in a specific environment

```python
# Get list of stacks
grids = api.cloudbroker.grid.list()

# Or you can use more convenient alias
dcs = api.cloudbroker.data_centers.list()

# To get one particular instance you should use .get() method
# For example with ID = 1
host = api.cloudbroker.data_centers.get(1)
```


## List of available methods

You can find more methods in detailed [documentation](#).