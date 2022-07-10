# php-memory-cache
php memory cache

##Apcu

$apcuAvailabe = function_exists('apcu_enabled') && apcu_enabled();

$bar = 'BAR';
apcu_add('foo', $bar);
echo apcu_fetch('foo');


##Shmop
Shmop is an easy to use set of functions that allows PHP to read, write, create and delete Unix shared memory segments.


$shm_id = shmop_open(0xff3, "c", 0644, 100);
if (!$shm_id) {
    echo "Couldn't create shared memory segment\n";
}

// Get shared memory block's size
$shm_size = shmop_size($shm_id);
echo "SHM Block Size: " . $shm_size . " has been created.\n";

// Lets write a test string into shared memory
$shm_bytes_written = shmop_write($shm_id, "my shared memory block", 0);
if ($shm_bytes_written != strlen("my shared memory block")) {
    echo "Couldn't write the entire length of data\n";
}

// Now lets read the string back
$my_string = shmop_read($shm_id, 0, $shm_size);
if (!$my_string) {
    echo "Couldn't read from shared memory block\n";
}
echo "The data inside shared memory was: " . $my_string . "\n";

//Now lets delete the block and close the shared memory segment
if (!shmop_delete($shm_id)) {
    echo "Couldn't mark shared memory block for deletion.";
}
shmop_close($shm_id);

##A fast read-only memory mapped hash-table for PHP

  $data = array(
        'key1' => 'value1',
        'key2' => 'value2',
        // ...
  );
  chdb_create('data.chdb', $data);


Then at run-time, the keys stored in the file can be read by:
  $chdb = new chdb('data.chdb');
  $value1 = $chdb->get('key1');
  $value2 = $chdb->get('key2');

