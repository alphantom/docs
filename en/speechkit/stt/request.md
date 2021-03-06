# API method description

Converts speech from an audio file into text.

## HTTP request {#http_request}

```
POST https://stt.api.cloud.yandex.net/speech/v1/stt:recognize
```

Use the `"Transfer-Encoding: chunked"` header for data streaming.

## Query parameters {#query_params}

| Parameter | Description |
| ----- | ----- |
| `lang` | The language for speech recognition.<br/>Acceptable values:<ul><li>`ru-RU` (default) — Russian.</li><li>`en-US` — English.</li><li>`tr-TR` — Turkish.</li></ul> |
| `topic` | The language model to be used for recognition.<br/>The closer the model is matched, the better the recognition result. You can only specify one model per request.<br/>[Acceptable values](../stt/index.md#model) depend on the selected language. Default parameter value: `general`. |
| `profanityFilter` | This parameter controls the profanity filter in recognized speech.<br>Acceptable values:<ul><li>`false` (default) — Profanity is not excluded from recognition results.</li><li>`true` — Profanity is excluded from recognition results.</li></ul> |
| `format` | The format of the submitted audio.<br/>Acceptable values:<ul><li>`lpcm` — Audio file in the [LPCM](https://en.wikipedia.org/wiki/Pulse-code_modulation) format with no WAV header. Audio characteristics:<ul><li>Sampling — 8, 16, or 48 kHz, depending on the `sampleRateHertz` parameter value.</li><li>Bit depth — 16-bit.</li><li>Byte order — Reversed (little-endian).</li><li>Audio data is stored as signed integers.</li></ul></li><li>`oggopus` (default) — Data is encoded using the OPUS audio codec and compressed using the OGG container format ([OggOpus](https://wiki.xiph.org/OggOpus)).</li></ul> |
| `sampleRateHertz` | The sampling frequency of the submitted audio.<br/>Used if `format` is set to `lpcm`. Acceptable values:<ul><li>`48000` (default) — Sampling rate of 48 kHz.</li><li>`16000` — Sampling rate of 16 kHz.</li><li>`8000` — Sampling rate of 8 kHz.</li></ul> |
| `folderId` | Required parameter.<br/>ID of your folder.<br/>For this API method, `folderId` is passed in the Query parameters rather than the request body.<br/>For more information about how to find the folder ID, see the section [Authorization in the API](../concepts/auth.md). |

## Parameters in the request body {#body_params}

The request body must pass the binary content of an audio file that meets the following requirements:

1. Maximum size: 1 MB
1. Maximum duration: 1 minute.
1. Number of audio channels: 1.

## Response {#response}

The response contains a recognition hypothesis.

The recognition hypothesis is what the recognition system assumes has been said.

The recognized text is processed before it is sent back: numbers are converted to digits, certain punctuation marks (such as hyphens) are added, and so on. The converted text is the final recognition result that is sent in the response body.

The response is returned in JSON format.

```json
{
  "result": <recognition hypothesis>
}
```

## Examples {#examples}

To use the SpeechKit API for speech recognition in Russian, send a small audio fragment (for example, [speech.ogg](https://download.cdn.yandex.net/from/yandex.ru/tech/ru/speechkit/cloud/doc/guide/files/speech.ogg)) via a POST request.

### Sample request {#request_examples}

---

**[!TAB POST request]**

```httpget
POST /speech/v1/stt:recognize?topic=general&lang=ru-RU&folderId={folder ID} HTTP/1.1
Host: stt.api.cloud.yandex.net
Authorization: Bearer <IAM-TOKEN>

... (binary content of an audio file)
```

**[!TAB cURL]**

```httpget
$ export FOLDER_ID=b1gvmob95yysaplct532
$ export IAM_TOKEN=CggaATEVAgA...
$ curl -X POST \
     -H "Authorization: Bearer ${IAM_TOKEN}" \
     -H "Transfer-Encoding: chunked" \
     --data-binary "@speech.ogg" \
     "https://stt.api.cloud.yandex.net/speech/v1/stt:recognize?topic=general&folderId=${FOLDER_ID}"
```

**[!TAB Python]**

```python
import urllib.request
import json

FOLDER_ID = "b1gvmob95yysaplct532" # ID of the folder
IAM_TOKEN = "CggaATEVAgA..." # IAM token

with open("speech.ogg", "rb") as f:
    data = f.read()

params = "&".join([
    "topic=general",
    "folderId=%s" % FOLDER_ID,
    "lang=ru-RU"
])

url = urllib.request.Request("https://stt.api.cloud.yandex.net/speech/v1/stt:recognize?%s" % params, data=data)
url.add_header("Authorization", "Bearer %s" % IAM_TOKEN)

responseData = urllib.request.urlopen(url).read().decode('UTF-8')
decodedData = json.loads(responseData)

if decodedData.get("error_code") is None:
    print(decodedData.get("result"))
```

**[!TAB PHP]**

```php
<?php

$token = 'CggaATEVAgA...'; # IAM token
$folderId = "b1gvmob95yysaplct532"; # ID of the folder
$audioFileName = "speech.ogg";

$file = fopen($audioFileName, 'rb');

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, "https://stt.api.cloud.yandex.net/speech/v1/stt:recognize?lang=ru-RU&folderId=${folderId}&format=oggopus");
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Authorization: Bearer ' . $token, 'Transfer-Encoding: chunked'));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true);
curl_setopt($ch, CURLOPT_BINARYTRANSFER, true);

curl_setopt($ch, CURLOPT_INFILE, $file);
curl_setopt($ch, CURLOPT_INFILESIZE, filesize($audioFileName));
$res = curl_exec($ch);
curl_close($ch);
$decodedResponse = json_decode($res, true);
if (isset($decodedResponse["result"])) {
    echo $decodedResponse["result"];
} else {
    echo "Error code: " . $decodedResponse["error_code"] . "\r\n";
    echo "Error message: " . $decodedResponse["error_message"] . "\r\n";
}

fclose($file);
```

---

### Sample response {#response_examples}

```
HTTP/1.1 200 OK
YaCloud-Billing-Units: 15
{
  "result": "your number is 212-85-06"
}
```

