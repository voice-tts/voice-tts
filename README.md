<!-- Logo -->
<p align="center">
    <a href="https://rapidapi.com/velut/api/voice-text-to-speech">
        <img width="128" src="assets/logo.png?raw=true" alt="Logo">
    </a>
</p>

# Voice Text to Speech API

A simple text to speech API with 50+ voices [**available on RapidAPI**](https://rapidapi.com/velut/api/voice-text-to-speech).

## API Endpoints

### POST `/read`

Send a `POST` request to the `/read` endpoint with a JSON object containing the text to read, for example:

```json
{ "text": "Hello world!" }
```

You will receive a response with a JSON object containing
the audio output encoded in [**Base64**](https://en.wikipedia.org/wiki/Base64).
To play the audio file, you first need to decode the Base64 string; this operation is supported by most programming languages.

#### Request Body

You must send a **JSON object** to the `/read` endpoint shaped like this:

```json
{
  "text": "Hello world!",
  "voice": "std-en-US-01",
  "format": "mp3"
}
```

Property `text` is **required** and its length must be between 1 and 3000 characters for users on paid plans and between 1 and 500 characters for users on the free plan.

Property `voice` is optional and must contain one of the [**available voice IDs**](#available-voices); the default value is `std-en-US-01`.

Property `format` is optional and must contain one of the [**available audio formats**](#available-formats); the default value is `mp3`.

#### Successful Response

On a successful request, you will receive an [**HTTP 200 OK**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) response with a JSON object shaped like this:

```json
{
  "meta": {
    "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
    "credits": 12
  },
  "data": {
    "text": "Hello world!",
    "voice": "std-en-US-01",
    "format": "mp3",
    "audio": "SGVsbG8gd29ybGQgYXVkaW8gZXhhbXBsZQ=="
  }
}
```

Property `meta.request_id` contains a unique ID identifying a specific request; this can be used for support tickets.

Property `meta.credits` contains the number of credits consumed for this request.

Properties `data.text`, `data.voice` and `data.format` contain the values submitted in the request.

Property `data.audio` contains the audio bytes encoded in [**Base64**](https://en.wikipedia.org/wiki/Base64).

#### Unsuccessful Response

On an unsuccessful request, you will receive an [**HTTP 400 Bad Request**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400) response with a JSON object shaped like this:

```json
{
  "meta": {
    "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
    "credits": 0
  },
  "error": {
    "type": "invalid_speech_request",
    "message": "Expected a valid speech request, encountered the listed issues",
    "issues": [
      "`text` property is required and must contain at least 1 character"
    ]
  }
}
```

Property `meta.request_id` contains a unique ID identifying a specific request; this can be used for support tickets.

Property `meta.credits` contains the number of credits consumed for this request.

Property `error.type` contains the error type identifier. See the [**Error Types**](#error-types) section.

Property `error.message` contains a human readable error message.

Property `error.issues` contains a (possibly empty) list of human readable messages to help you fix the error.

#### Service Unavailable Response

When the speech service is unavailable, you will receive an [**HTTP 503 Service Unavailable**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/503) response with a JSON object shaped like this:

```json
{
  "meta": {
    "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
    "credits": 0
  },
  "error": {
    "type": "speech_service_unavailable",
    "message": "Failed to process speech request, try again later",
    "issues": []
  }
}
```

## Available Voices

The following table describes the available voices.
Use a value from the **Voice ID** column in your requests.

<table>
  <thead>
    <tr>
      <th>Voice ID</th>
      <th>Language Code</th>
      <th>Language Name</th>
      <th>Gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code>std-ar-BH-01</code>
      </td>
      <td>ar-BH</td>
      <td>Arabic (Bahrain)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-cy-GB-01</code>
      </td>
      <td>cy-GB</td>
      <td>Welsh (UK)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-da-DK-01</code>
      </td>
      <td>da-DK</td>
      <td>Danish (Denmark)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-da-DK-02</code>
      </td>
      <td>da-DK</td>
      <td>Danish (Denmark)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-de-DE-01</code>
      </td>
      <td>de-DE</td>
      <td>German (Germany)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-de-DE-02</code>
      </td>
      <td>de-DE</td>
      <td>German (Germany)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-de-DE-03</code>
      </td>
      <td>de-DE</td>
      <td>German (Germany)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-AU-01</code>
      </td>
      <td>en-AU</td>
      <td>English (Australia)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-AU-02</code>
      </td>
      <td>en-AU</td>
      <td>English (Australia)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-en-GB-01</code>
      </td>
      <td>en-GB</td>
      <td>English (UK)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-GB-02</code>
      </td>
      <td>en-GB</td>
      <td>English (UK)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-en-GB-03</code>
      </td>
      <td>en-GB</td>
      <td>English (UK)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-GB-04</code>
      </td>
      <td>en-GB</td>
      <td>English (Wales)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-en-IN-01</code>
      </td>
      <td>en-IN</td>
      <td>English (India)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-IN-02</code>
      </td>
      <td>en-IN</td>
      <td>English (India)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-01</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-02</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-03</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-04</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-05</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-en-US-06</code>
      </td>
      <td>en-US</td>
      <td>English (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-es-ES-01</code>
      </td>
      <td>es-ES</td>
      <td>Spanish (Spain)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-es-ES-02</code>
      </td>
      <td>es-ES</td>
      <td>Spanish (Spain)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-es-ES-03</code>
      </td>
      <td>es-ES</td>
      <td>Spanish (Spain)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-es-MX-01</code>
      </td>
      <td>es-MX</td>
      <td>Spanish (Mexico)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-es-US-01</code>
      </td>
      <td>es-US</td>
      <td>Spanish (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-es-US-02</code>
      </td>
      <td>es-US</td>
      <td>Spanish (USA)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-es-US-03</code>
      </td>
      <td>es-US</td>
      <td>Spanish (USA)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-fr-CA-01</code>
      </td>
      <td>fr-CA</td>
      <td>French (Canada)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-fr-FR-01</code>
      </td>
      <td>fr-FR</td>
      <td>French (France)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-fr-FR-02</code>
      </td>
      <td>fr-FR</td>
      <td>French (France)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-fr-FR-03</code>
      </td>
      <td>fr-FR</td>
      <td>French (France)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-hi-IN-01</code>
      </td>
      <td>hi-IN</td>
      <td>Hindi (India)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-is-IS-01</code>
      </td>
      <td>is-IS</td>
      <td>Icelandic (Iceland)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-is-IS-02</code>
      </td>
      <td>is-IS</td>
      <td>Icelandic (Iceland)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-it-IT-01</code>
      </td>
      <td>it-IT</td>
      <td>Italian (Italy)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-it-IT-02</code>
      </td>
      <td>it-IT</td>
      <td>Italian (Italy)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-it-IT-03</code>
      </td>
      <td>it-IT</td>
      <td>Italian (Italy)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-ja-JP-01</code>
      </td>
      <td>ja-JP</td>
      <td>Japanese (Japan)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-ja-JP-02</code>
      </td>
      <td>ja-JP</td>
      <td>Japanese (Japan)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-ko-KR-01</code>
      </td>
      <td>ko-KR</td>
      <td>Korean (Korea)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-nb-NO-01</code>
      </td>
      <td>nb-NO</td>
      <td>Norwegian (Norway)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-nl-NL-01</code>
      </td>
      <td>nl-NL</td>
      <td>Dutch (Netherlands)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-nl-NL-02</code>
      </td>
      <td>nl-NL</td>
      <td>Dutch (Netherlands)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-pl-PL-01</code>
      </td>
      <td>pl-PL</td>
      <td>Polish (Poland)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-pl-PL-02</code>
      </td>
      <td>pl-PL</td>
      <td>Polish (Poland)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-pl-PL-03</code>
      </td>
      <td>pl-PL</td>
      <td>Polish (Poland)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-pl-PL-04</code>
      </td>
      <td>pl-PL</td>
      <td>Polish (Poland)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-pt-BR-01</code>
      </td>
      <td>pt-BR</td>
      <td>Portuguese (Brazil)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-pt-BR-02</code>
      </td>
      <td>pt-BR</td>
      <td>Portuguese (Brazil)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-pt-BR-03</code>
      </td>
      <td>pt-BR</td>
      <td>Portuguese (Brazil)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-pt-PT-01</code>
      </td>
      <td>pt-PT</td>
      <td>Portuguese (Portugal)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-pt-PT-02</code>
      </td>
      <td>pt-PT</td>
      <td>Portuguese (Portugal)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-ro-RO-01</code>
      </td>
      <td>ro-RO</td>
      <td>Romanian (Romania)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-ru-RU-01</code>
      </td>
      <td>ru-RU</td>
      <td>Russian (Russia)</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>std-ru-RU-02</code>
      </td>
      <td>ru-RU</td>
      <td>Russian (Russia)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-sv-SE-01</code>
      </td>
      <td>sv-SE</td>
      <td>Swedish (Sweden)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-tr-TR-01</code>
      </td>
      <td>tr-TR</td>
      <td>Turkish (Turkey)</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>std-zh-CN-01</code>
      </td>
      <td>zh-CN</td>
      <td>Chinese (Mandarin)</td>
      <td>Female</td>
    </tr>
  </tbody>
</table>

## Available Formats

The following table describes the available audio formats.
Use a value from the **Format ID** column in your requests.

<table>
  <thead>
    <tr>
      <th>Format ID</th>
      <th>Format Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code>mp3</code>
      </td>
      <td>MP3</td>
    </tr>
    <tr>
      <td>
        <code>ogg_vorbis</code>
      </td>
      <td>Ogg Vorbis</td>
    </tr>
  </tbody>
</table>

## Error Types

The following table describes the possible error types.

<table>
  <thead>
    <tr>
      <th>Error Type</th>
      <th>Error Cause</th>
      <th>Error Solution</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <code>invalid_json_body</code>
      </td>
      <td>
        The payload sent in the request is not a valid JSON object or does not conform to the expected object schema (for example, properties with the wrong name or type).
      </td>
      <td>
        Check the request payload and make sure it follows the expected JSON object schema.
      </td>
    </tr>
    <tr>
      <td>
        <code>invalid_speech_request</code>
      </td>
      <td>
        The payload sent in the request conforms to the expected schema but some property values are invalid (for example, invalid voice IDs or text exceeding length limits).
      </td>
      <td>
        Check the list of issues sent in the error response and update the request values accordingly.
      </td>
    </tr>
    <tr>
      <td>
        <code>speech_service_unavailable</code>
      </td>
      <td>
        The API speech service is currently unavailable and requests cannot be processed.
      </td>
      <td>
        Wait some time and try submitting the request again.
      </td>
    </tr>
  </tbody>
</table>
