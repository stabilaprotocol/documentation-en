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

### RocksDB vs LevelDB

You can refer to:

- [RocksDB vs LevelDB(en)](https://github.com/stabilaprotocol/documentation/blob/master/STB/Rocksdb_vs_Leveldb.md)
- [RocksDB vs LevelDB(zh-cn)](https://github.com/stabilaprotocol/documentation/blob/master/STB_CN/Rocksdb_vs_Leveldb.md)
