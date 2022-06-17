## Clearout Instant Email Verification PHP API V1

Instant verification API can be seamlessly integrated into your signup or onboarding process with just a single request. Use this API to verify Email Address without going through queue.

### POST
```
https://api.clearout.io/v2/email_verify/instant
```

### PHP
```php
<?php
$curl = curl_init();
curl_setopt_array($curl, array(
  CURLOPT_URL => 'https://api.clearout.io/v2/email_verify/instant',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => '{"email": "us@clearout.io"}',
  CURLOPT_HTTPHEADER => array(
    "Content-Type: application/json",
    "Authorization: REPLACE_WITH_YOUR_API_TOKEN"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  $response = json_decode($response, true);
  echo "Email address: " . $response['data']['email_address'] . "\n";
  echo "Status: " . $response['data']['status'] . "\n";
}

?>
```

#### Header
| **Field**         | **Type**          | **Description**                              |
| :-------------    | :-------------:   | :-----                                       |
| Content-Type      | String            | Default value: application/json              |
| Authorization     | String            | Default value: REPLACE_WITH_YOUR_API_TOKEN   |

#### Parameter
| **Field**           | **Type**          | **Description**                                                        |
| :-------------      | :-------------:   | :-----                                                                 |
| email               | String            | An email address to verify                                             |
| timeout `optional`  | Number            | Request wait time (in milliseconds), Maximum allowed wait time should not exceed **180,000 milliseconds** Default value: 130,000|   
