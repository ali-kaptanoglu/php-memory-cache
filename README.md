# php-memory-cache
php memory cache

##Apcu

$apcuAvailabe = function_exists('apcu_enabled') && apcu_enabled();

$bar = 'BAR';
apcu_add('foo', $bar);
echo apcu_fetch('foo');


##Apcu

