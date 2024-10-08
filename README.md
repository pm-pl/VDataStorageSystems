# VDataStorageSystems
- Store data in the form of arrays, update, quickly retrieve data, and store optimally securely in multiple storage formats in PocketMine-PMMP 5.

# Features
- Store batch data and update it, retrieve data quickly.
- Store data securely even when the server shuts down unexpectedly or sudden server stop.
- Reduce the need for continuous data storage and continuous queries in `database` and local file formats such as `yml`.
- Supports a variety of formats such as: `.properties, .js, .json, .yml, .yaml, .sl, .txt, .list, .enum, mysql, sqlite`
- Allow data to be queried only once to minimize over-querying!

# Notes
- Data can be lost if you are the one who actively closes the console window or the server using the X button of the console interface. (Does not include your use of the `/stop` command on the console)
- To be safe and secure the best server closure, do something that closes in a valid manner such as the `/stop` command.
- The data stored in virion is unstructured and array-style data in php.

# FQA
- What if I want to edit the data from this virion manually? - You just need to download this software and edit it [VDataStorageSystemsWebsite](https://github.com/VennDev/VDataStorageSystemsWebsite)

# Virion Required
- [LibVapmPMMP](https://github.com/VennDev/LibVapmPMMP)
- [VapmDatabasePMMP](https://github.com/VennDev/VapmDatabasePMMP)
- [VErrorHandler](https://github.com/VennDev/VErrorHandler)

# Example plugins
- [PluginExample](https://github.com/VennDev/TestVDataStorageSystems)

# Example some methods
```php
...
use VDataStorageSystems;

self::setPeriodTask(10 * 60); // Save all data every 10 minutes

// Create a storage with the name "test.yml" and type "YAML"
self::createStorage(
    name: $this->getDataFolder() . "test.yml",
    type: TypeDataStorage::TYPE_YAML
);
self::getStorage($this->getDataFolder() . "test.yml")->set("test", "test");

// Create a storage with the name "test.db" and type "SQLITE"
self::createStorage(
    name: "testSQLITE",
    type: TypeDataStorage::TYPE_SQLITE,
    database: new SQLite($this->getDataFolder() . "test.db")
);
self::getStorage("testSQLITE")->set("test", ["testAC", "testB"]);
// This is an example of how to use the Async class to get data from the database
new Async(function () {
    $data = Async::await(self::getStorage("testSQLITE")->get("test"));
    var_dump($data);
});

// Create a storage with the name "test" and type "MYSQL"
self::createStorage(
    name: "testMYSQL",
    type: TypeDataStorage::TYPE_MYSQL,
    database: new MySQL(
        host: "localhost",
        username: "root",
        password: "",
        databaseName: "testg",
        port: 3306
    )
);
self::getStorage("testMYSQL")->set("test", ["testAC", "testB"]);
// This is an example of how to use the Async class to get data from the database
new Async(function () {
    $data = Async::await(self::getStorage("testMYSQL")->get("test"));
    var_dump($data);
});
```

# Credits
- Author: [VennDev](https://github.com/VennDev)
- Paypal: pnam5005@gmail.com
