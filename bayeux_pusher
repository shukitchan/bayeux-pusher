#!/home/y/bin/php
<?php
if(count($argv) != 4)
{
 echo "Usage: bayeux_pusher.php <url> <channel> <msg>\n";
 exit(0);
}
//$url = 'http://server/bayeux';
//$channel = '/test/channel1';
//$msg = 'test'.time();
$url = $argv[1];
$channel = $argv[2];
$msg = $argv[3];

$header = array('Content-type: application/json');

$handshake = "{\"channel\":\"/meta/handshake\", \"minimumVersion\":\"0.9\", \"ve
rsion\":\"1.0\", \"supportedConnectionTypes\": [\"long-polling\"]}";

$curl = curl_init();
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $handshake );
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, $header);
$handshake_result =  curl_exec($curl);

echo 'HANDSHAKE RESULT:'.$handshake_result."\n";

$result = json_decode($handshake_result, true);
$clientId = $result[0]['clientId'];


$connect = "{\"channel\":\"/meta/connect\", \"clientId\":\"".$clientId."\", \"co
nnectionType\":\"long-polling\"}";
$curl = curl_init();
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $connect );
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, $header);
$connect_result =  curl_exec($curl);

echo 'CONNECT RESULT:'.$connect_result."\n";

$channel = "[{\"channel\":\"".$channel."\",\"data\":\"".$msg."\",\"id\":\"1321\"
,\"clientId\":\"".$clientId."\"}]";

$curl = curl_init();
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $channel );
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, $header);
$channel_result =  curl_exec($curl);

echo 'CHANNEL RESULT:'.$channel_result."\n";

$disconnect = "{\"channel\":\"/meta/disconnect\", \"clientId\":\"".$clientId."\"
}";

$curl = curl_init();
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $disconnect );
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_HTTPHEADER, $header);
$disconnect_result = curl_exec($curl);

echo 'DISCONNECT RESULT:'.$disconnect_result."\n";
?>

