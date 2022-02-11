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
{ "text": "Hello world" }
```

You will receive a response with a JSON object containing
the audio output encoded in [**Base64**](https://en.wikipedia.org/wiki/Base64).
To play the audio file, you first need to decode the Base64 string; this operation is supported by most programming languages.


#### Request Body

You must send a **JSON object** to the `/read` endpoint shaped like this:

```json
{
  "text": "Hello world",
  "voice": "en-US-01",
  "format": "mp3"
}
```

Property `text` is **required** and its length must be between 1 and 3000 characters for users on paid plans and between 1 and 500 characters for users on the free plan.

Property `voice` is optional and must contain one of the [**available voice IDs**](#available-voices); the default value is `en-US-01`.

Property `format` is optional and must contain one of the [**available audio formats**](#available-formats); the default value is `mp3`.

#### Successful Response

On a successful request, you will receive an [**HTTP 200 OK**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) response with a JSON object shaped like this:

```json
{
  "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
  "data": {
    "text": "Hello world",
    "voice": "en-US-01",
    "format": "mp3",
    "audio": "SGVsbG8gd29ybGQgYXVkaW8gZXhhbXBsZQ==",
    "characters": 11
  }
}
```

Property `request_id` contains a unique ID identifying a specific request; this can be used for support tickets.

Properties `data.text`, `data.voice` and `data.format` contain the values submitted in the request.

Property `data.audio` contains the audio bytes encoded in [**Base64**](https://en.wikipedia.org/wiki/Base64).

Property `data.characters` contains the number of characters billed to your account.

#### Unsuccessful Response

On an unsuccessful request, you will receive an [**HTTP 400 Bad Request**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/400) response with a JSON object shaped like this:

```json
{
  "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
  "error": {
    "type": "invalid_speech_request",
    "message": "Expected a valid speech request, encountered the listed issues",
    "issues": [
      "`text` property is required and must contain at least 1 character"
    ]
  }
}
```

Property `request_id` contains a unique ID identifying a specific request; this can be used for support tickets.

Property `error.type` contains the error type identifier. See the [**Error Types**](#error-types) section.

Property `error.message` contains a human readable error message.

Property `error.issues` contains a (possibly empty) list of human readable messages to help you fix the error.

#### Service Unavailable Response

When the speech service is unavailable, you will receive an [**HTTP 503 Service Unavailable**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/503) response with a JSON object shaped like this:

```json
{
  "request_id": "24fLk8lojIhL1083eH4skD6XujJ",
  "error": {
    "type": "speech_service_unavailable",
    "message": "Failed to process speech request, try again later",
    "issues": []
  }
}
```

## Available Voices

The following table describes the available voices.

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
        <code>arb-01</code>
      </td>
      <td>arb</td>
      <td>Arabic</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>cmn-CN-01</code>
      </td>
      <td>cmn-CN</td>
      <td>Chinese Mandarin</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>cy-GB-01</code>
      </td>
      <td>cy-GB</td>
      <td>Welsh</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>da-DK-01</code>
      </td>
      <td>da-DK</td>
      <td>Danish</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>da-DK-02</code>
      </td>
      <td>da-DK</td>
      <td>Danish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>de-DE-01</code>
      </td>
      <td>de-DE</td>
      <td>German</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>de-DE-02</code>
      </td>
      <td>de-DE</td>
      <td>German</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>de-DE-03</code>
      </td>
      <td>de-DE</td>
      <td>German</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-AU-01</code>
      </td>
      <td>en-AU</td>
      <td>Australian English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-AU-02</code>
      </td>
      <td>en-AU</td>
      <td>Australian English</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>en-GB-01</code>
      </td>
      <td>en-GB</td>
      <td>British English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-GB-02</code>
      </td>
      <td>en-GB</td>
      <td>British English</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>en-GB-03</code>
      </td>
      <td>en-GB</td>
      <td>British English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-GB-WLS-01</code>
      </td>
      <td>en-GB-WLS</td>
      <td>Welsh English</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>en-IN-01</code>
      </td>
      <td>en-IN</td>
      <td>Indian English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-IN-02</code>
      </td>
      <td>en-IN</td>
      <td>Indian English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-US-01</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-US-02</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>en-US-03</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-US-04</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>en-US-05</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>en-US-06</code>
      </td>
      <td>en-US</td>
      <td>US English</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>es-ES-01</code>
      </td>
      <td>es-ES</td>
      <td>Castilian Spanish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>es-ES-02</code>
      </td>
      <td>es-ES</td>
      <td>Castilian Spanish</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>es-ES-03</code>
      </td>
      <td>es-ES</td>
      <td>Castilian Spanish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>es-MX-01</code>
      </td>
      <td>es-MX</td>
      <td>Mexican Spanish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>es-US-01</code>
      </td>
      <td>es-US</td>
      <td>US Spanish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>es-US-02</code>
      </td>
      <td>es-US</td>
      <td>US Spanish</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>es-US-03</code>
      </td>
      <td>es-US</td>
      <td>US Spanish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>fr-CA-01</code>
      </td>
      <td>fr-CA</td>
      <td>Canadian French</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>fr-FR-01</code>
      </td>
      <td>fr-FR</td>
      <td>French</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>fr-FR-02</code>
      </td>
      <td>fr-FR</td>
      <td>French</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>fr-FR-03</code>
      </td>
      <td>fr-FR</td>
      <td>French</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>hi-IN-01</code>
      </td>
      <td>hi-IN</td>
      <td>Hindi</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>is-IS-01</code>
      </td>
      <td>is-IS</td>
      <td>Icelandic</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>is-IS-02</code>
      </td>
      <td>is-IS</td>
      <td>Icelandic</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>it-IT-01</code>
      </td>
      <td>it-IT</td>
      <td>Italian</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>it-IT-02</code>
      </td>
      <td>it-IT</td>
      <td>Italian</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>it-IT-03</code>
      </td>
      <td>it-IT</td>
      <td>Italian</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>ja-JP-01</code>
      </td>
      <td>ja-JP</td>
      <td>Japanese</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>ja-JP-02</code>
      </td>
      <td>ja-JP</td>
      <td>Japanese</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>ko-KR-01</code>
      </td>
      <td>ko-KR</td>
      <td>Korean</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>nb-NO-01</code>
      </td>
      <td>nb-NO</td>
      <td>Norwegian</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>nl-NL-01</code>
      </td>
      <td>nl-NL</td>
      <td>Dutch</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>nl-NL-02</code>
      </td>
      <td>nl-NL</td>
      <td>Dutch</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>pl-PL-01</code>
      </td>
      <td>pl-PL</td>
      <td>Polish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>pl-PL-02</code>
      </td>
      <td>pl-PL</td>
      <td>Polish</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>pl-PL-03</code>
      </td>
      <td>pl-PL</td>
      <td>Polish</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>pl-PL-04</code>
      </td>
      <td>pl-PL</td>
      <td>Polish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>pt-BR-01</code>
      </td>
      <td>pt-BR</td>
      <td>Brazilian Portuguese</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>pt-BR-02</code>
      </td>
      <td>pt-BR</td>
      <td>Brazilian Portuguese</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>pt-BR-03</code>
      </td>
      <td>pt-BR</td>
      <td>Brazilian Portuguese</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>pt-PT-01</code>
      </td>
      <td>pt-PT</td>
      <td>Portuguese</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>pt-PT-02</code>
      </td>
      <td>pt-PT</td>
      <td>Portuguese</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>ro-RO-01</code>
      </td>
      <td>ro-RO</td>
      <td>Romanian</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>ru-RU-01</code>
      </td>
      <td>ru-RU</td>
      <td>Russian</td>
      <td>Male</td>
    </tr>
    <tr>
      <td>
        <code>ru-RU-02</code>
      </td>
      <td>ru-RU</td>
      <td>Russian</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>sv-SE-01</code>
      </td>
      <td>sv-SE</td>
      <td>Swedish</td>
      <td>Female</td>
    </tr>
    <tr>
      <td>
        <code>tr-TR-01</code>
      </td>
      <td>tr-TR</td>
      <td>Turkish</td>
      <td>Female</td>
    </tr>
  </tbody>
</table>

### Available Formats

The following table describes the available audio formats.

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

### Error Types

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
