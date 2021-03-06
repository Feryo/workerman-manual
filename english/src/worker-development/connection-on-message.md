# onMessage
## Description:
```php
callback Connection::$onMessage
```


Is the same as ```$worker->onMessage```, but only for the current connection.


## Examples

```php
use Workerman\Worker;
require_once './Workerman/Autoloader.php';

$worker = new Worker('websocket://0.0.0.0:8484');
$worker->onConnect = function($connection)
{
    $connection->onMessage = function($connection, $data)
    {
        var_dump($data);
        $connection->send('receive success');
    };
};

// Run all workers
Worker::runAll();
```

Is the same as

```php
use Workerman\Worker;
require_once './Workerman/Autoloader.php';

$worker = new Worker('websocket://0.0.0.0:8484');
$worker->onMessage = function($connection, $data)
{
    var_dump($data);
    $connection->send('receive success');
};

// Run all workers
Worker::runAll();
```
