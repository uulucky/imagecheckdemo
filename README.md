# php-demo

```php
$data=base64_encode(file_get_contents('demo.jpg'));
$token = '你自己的token';
$taskid = 'ad201710';
$res = cur_post('http://api.noperfect.cn/api/task', array('token' => $token,'taskid' => $taskid, 'data' => $data));
var_dump(json_decode($res,true));

function cur_post($url,$post_data){
    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL, $url);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
    curl_setopt($ch, CURLOPT_TIMEOUT,30);
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_POSTFIELDS, $post_data);
    $output = curl_exec($ch);
    curl_close($ch);
    return $output;
}

```

# curl-demo

```
curl -d'token=你自己的token&taskid=ad201710&data=图片二进制数据的base64编码' 'http://api.noperfect.cn/api/task'
```

# Python-demo

```Python
#!/usr/bin/env python
#-*- coding: utf-8 -*-

import requests
import json
import base64

with open('/path/to/file', 'r') as f:
    data = f.read()
payload = {'token': '你自己的token', 'taskid': 'ad201710','data':base64.b64encode(data)}
r = requests.post("http://api.noperfect.cn/api/task", data=payload)
print(json.dumps(r.text))

```

## License

MIT