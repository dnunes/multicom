multicom
========
### Your own swarm of intercommunicating processes!

Ever had a big project full of independent modules that you wish you could run and update separately but still communicate between them with great ease and blazingly fast? Well, me too.

**Multicom** is a fully-tested no-nonsense package to make sure your design decisions are based on project needs, not yours. It will keep your modules stable and easily testable while still providing seamless internal communication.

**Multicom** was designed with no compromise on features:

* **Blazingly fast**: it communicates using the dnode library ...;

* **No extra configuration needed**: this package follows the idea of _convention over configuration_, so it keeps the required environment files to a minimum and there is nothing to thinker with before start using it;
* **Never out of sync**: when loading the environment configuration file, it checks the schema for *missing AND for extra keys*, alerting you when you are missing some key in your config or in your schema file;
* **Auto load the right config file**: you can set the root path of the project in the environment config file and it will load automatically.


## <a id="installation">Installation</a>
The simplest way to install this package is using [npm](http://www.npmjs.com/):
```bash
$ npm i -S multicom
```

You can also manually download the [latest release](https://github.com/dnunes/multicom/zipball/master) from [our project page](http://dnunes.com/multicom/) or any release from [our GitHub repository](https://github.com/dnunes/multicom/) on the [releases page](https://github.com/dnunes/multicom/releases/).


## <a id="quickstart">Quick Start Guide</a>

There are just four steps needed to start using this package:

1. Create a folder named `envs` on your project's root;
2. Create a [`config.schema`](#sampleschema) file with your schema;
3. Create a [`ENVNAME.json`](#sampleenv) file for each environment with its specific configuration (where `ENVNAME` is whatever name you wish to use);
4. Load the package. It is ready to read your config.

In your code:

```javascript
const AutoEnvConfig = require('autoenvconfig');

let isValuePresent = AutoEnvConfig.has('deep.key.supported'));
if (isValuePresent) {
  let valueFromConfig = AutoEnvConfig.get('deep.key.supported'));
  console.log(valueFromConfig); //"myValue"
}
```


## <a id="methods">Methods</a>

All the methods can be called in a specific instance (from a `AutoEnvConfig.load` call) or in the [_magic instance_](#magicload). You can save a reference for the [_magic instance_](#magicload) using a `AutoEnvConfig.load()` call and call methods on this instance as well and it will work exactly the same as calling the methods directly on the package.

### <a id="magicmethods">Magic Methods</a>

- <a id="mautoload">`AutoEnvConfig.load([<envName>])`</a>
This method will return a new instance of `AutoEnvConfig` class (actually, prototype). If you ommit the `<envName>` parameter, it will try to [_magic load_](#magicload) it. If you pass the `<envName>` parameter, it will just return the config for the specified env. It returns false if it cannot find an environment config.

- <a id="mautoget">`AutoEnvConfig.get(<key>[, <defaultValueIfNotPresent>])`</a>
This method will return the value of `<key>` in the [_magic instance_](#magicload). If `key` is not present in the [_magic instance_](#magicload), it will either return `<defaultValueIfNotPresent>` or throw an error if there the default value parameter was committed.

- <a id="mautohas">`AutoEnvConfig.has(<key>)`</a>
This method will return boolean `true` if the `<key>` is present in the [_magic instance_](#magicload) or boolean `false` if not.

- <a id="mautoset">`AutoEnvConfig.set(<key>, <value>)`</a>
This method will replace the contents of `<key>` for the [_magic instance_](#magicload) with `<value>`;


### <a id="instancemethods">Instance Methods</a>

- <a id="minsload">`<Instance>.load([<envName>])`</a>
This method will return a new instance of `AutoEnvConfig` class (actually, prototype). If you ommit the `<envName>` parameter, it will try to [_magic load_](#magicload) it. If you pass the `<envName>` parameter, it will just return the config for the specified env. It returns false if it cannot find an environment config.

- <a id="minsget">`<Instance>.get(<key>[, <defaultValueIfNotPresent>])`</a>
This method will return the value of `<key>` in the `<Instance>` object. If `<key>` is not present in the `<Instance>` object, it will either return `<defaultValueIfNotPresent>` or throw an error if there the default value parameter was committed.

-  <a id="minshas">`<Instance>.has(<key>)`</a>
This method will return boolean `true` if the `<key>` is present in the `<Instance>` object or boolean `false` if not.

- <a id="minsset">`<Instance>.set(<key>, <value>)`</a>
This method will replace the  contents of `<key>` for the `<Instance>` object with `<value>`;


## <a id="releaseh">Release History</a>

* [0.0.1](https://github.com/dnunes/autoenvconfig/releases/tag/v0.0.1) Initial release.


## <a id="credits">Credits</a>

Created and maintained (with much ♡) by [diego nunes](http://dnunes.com)

Donations with Bitcoin to _1PQyeHqusUj3SuTmw6DPqWSHptVHkYZ33R_:

![1PQyeHqusUj3SuTmw6DPqWSHptVHkYZ33R](http://chart.apis.google.com/chart?cht=qr&chs=200x200&chl=bitcoin:1PQyeHqusUj3SuTmw6DPqWSHptVHkYZ33R)
