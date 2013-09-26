php-sdk
=======
PHP SDK for communication with the inSided REST API. 
Using the PHP SDK
=======
Example for getting a specific thread. (the getResult function returns by default array if FALSE given als first param, json will be returned).
 ```
<?php
require_once '../inSidedApi.php';

$apiKey    = 'insert_api_key';
$apiSecret = 'insert_api_secret';

$insided = new inSidedApi($apiKey, $apiSecret);

try {
  $insided->api('thread', 132);

  print_r($insided->getResult());
} catch (inSidedApiException $e) {
  error_log($e->getMessage());
}
?>
 ```
Example for getting all threads
 ```
<?php
require_once '../inSidedApi.php';

$apiKey    = 'insert_api_key';
$apiSecret = 'insert_api_secret';

$insided = new inSidedApi($apiKey, $apiSecret);

try {
  $insided->api('thread');

  print_r($insided->getResult());
} catch (inSidedApiException $e) {
  error_log($e->getMessage());
}
?>
```
Example with filtering, sorting and limiting.
 ```
<?php
require_once '../inSidedApi.php';

$apiKey    = 'insert_api_key';
$apiSecret = 'insert_api_secret';

$insided = new inSidedApi($apiKey, $apiSecret);

try {
  $insided->api('thread')
    ->filter(array(
      'prefixid' => 'beantwoord',
      'forumid'  => 6,
    ))
    ->orderBy('dateline', 'DESC')
    ->limit(5, 1)
    ->execute();

    print_r(
      $insided->getResult()
    );
} catch (inSidedApiException $e) {
  error_log($e->getMessage());
}
?>
 ```
