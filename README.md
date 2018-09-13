# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

* [`wireguard`](#wireguard): Wireguard class manages wireguard - an open-source software application
and protocol that implements virtual private network techniques to create
secure point-to-point connections in routed or bridged configurations.
* [`wireguard::config`](#wireguardconfig): Class configures files and directories for wireguard
* [`wireguard::install`](#wireguardinstall): Class installs wireguard packages and sets yum repository
* [`wireguard::params`](#wireguardparams): Class that contains OS specific parameters for other classes

**Defined types**

* [`wireguard::interface`](#wireguardinterface): Defines wireguard tunnel interfaces

## Classes

### wireguard

Wireguard class manages wireguard - an open-source software application
and protocol that implements virtual private network techniques to create
secure point-to-point connections in routed or bridged configurations.

* **See also**
https://www.wireguard.com/

#### Parameters

The following parameters are available in the `wireguard` class.

##### `package_name`

Data type: `Variant[Array, String]`

Name the package(s) that installs wireguard

Default value: $::wireguard::params::package_name

##### `repo_url`

Data type: `String`

URL of wireguard repo

Default value: $::wireguard::params::repo_url

##### `manage_repo`

Data type: `Boolean`

Should class manage yum repo

Default value: $::wireguard::params::manage_repo

##### `manage_package`

Data type: `Boolean`

Should class install package(s)

Default value: $::wireguard::params::manage_package

##### `package_ensure`

Data type: `Variant[Boolean, Enum['installed','latest','present']]`

Set state of the package

Default value: 'installed'

##### `config_dir`

Data type: `Stdlib::Absolutepath`

Path to wireguard configuration files

Default value: $::wireguard::params::config_dir

##### `interfaces`

Data type: `Optional[Hash]`

Define wireguard interfaces

Default value: {}

### wireguard::config

Class configures files and directories for wireguard

#### Parameters

The following parameters are available in the `wireguard::config` class.

##### `config_dir`

Data type: `Stdlib::Absolutepath`

Path to wireguard configuration files

### wireguard::install

Class installs wireguard packages and sets yum repository

#### Parameters

The following parameters are available in the `wireguard::install` class.

##### `package_name`

Data type: `Variant[Array, String]`

Name the package(s) that installs wireguard

##### `repo_url`

Data type: `String`

URL of wireguard repo

##### `manage_repo`

Data type: `Boolean`

Should class manage yum repo

##### `manage_package`

Data type: `Boolean`

Should class install package(s)

##### `package_ensure`

Data type: `Variant[Boolean, Enum['installed','latest','present']]`

Set state of the package

### wireguard::params

Class that contains OS specific parameters for other classes

## Defined types

### wireguard::interface

Defines wireguard tunnel interfaces

#### Parameters

The following parameters are available in the `wireguard::interface` defined type.

##### `address`

Data type: `Variant[Array,String]`

List of IP (v4 or v6) addresses (optionally with CIDR masks) to
be assigned to the interface.

##### `private_key`

Data type: `String`

Private key for data encryption

##### `listen_port`

Data type: `Integer[1,65535]`

The port to listen

##### `ensure`

Data type: `Enum['present','absent']`

State of the interface

Default value: 'present'

##### `peers`

Data type: `Optional[Array[Struct[
    {
      'PublicKey'  => String,
      'AllowedIPs' => Optional[String],
    }
  ]]]`

List of peers for wireguard interface

Default value: []

##### `saveconfig`

Data type: `Boolean`

save current state of the interface upon shutdown

Default value: `true`

##### `config_dir`

Data type: `Stdlib::Absolutepath`

Path to wireguard configuration files

Default value: '/etc/wireguard'

