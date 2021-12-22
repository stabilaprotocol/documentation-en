# The Database

## Use RocksDB

### Configuration

Use RocksDB as the data storage engine, need to set `db.engine` to "ROCKSDB".

![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/db_engine.png)

Note: RocksDB only supports `db.version=2`, yet does not supports `db.version=1`

The optimization parameters RocksDB support:

![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/rocksdb_tuning_parameters.png)

### Use RocksDB's data backup function

Choose RocksDB to be the data storage engine, you can use its data backup function while running

![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/db_backup.png)

Note: FullNode can use data backup function.
