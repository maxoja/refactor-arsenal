Some groups of functionalities that need some shared variable and initialisation can be encapsulated within a static class and used widely across project. There's actually no static class in python but there's classes with one or more static methods which are typically called as static classes.

One of decent usecases for static class/method is database operations as they all need one same client object and need to be init at starting point.

```
# this class is mock and not functional
class DatabaseManager:
    HOST_ADDRESS = configs.host
    client = None
    
    @staticmethod
    def init():
        MongoClient(DatabaseManager.HOST_ADDRESS)
        
    @staticmethod
    def add_record(newRecord:dict):
        client.create(newRecord)
```
