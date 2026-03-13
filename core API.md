Core API — Convert Text → Speech

This is the main API your clients will use.

Endpoint
POST /tts
Full URL
https://codvoice.codelessai.in/tts
Request

Content-Type:

application/x-www-form-urlencoded

or JSON.

Example Request
{
 "text": "Hello welcome to our platform",
 "voice": "ryan"
}
Request Parameters
Parameter	Type	Required	Description
text	string	✅	Text to convert to speech
voice	string	✅	Voice model name
Example CURL Request
curl -X POST https://codvoice.codelessai.in/tts \
-d "text=Hello this is Ryan speaking" \
-d "voice=ryan"
Response

Content-Type:

audio/wav

Binary audio stream.

Example response headers:

HTTP/1.1 200 OK
Content-Type: audio/wav
Content-Length: 234001

The frontend will play this audio directly.

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2️⃣ Frontend Audio Playback Example

Example JavaScript client:

const response = await fetch("https://codvoice.codelessai.in/tts", {
  method: "POST",
  headers: {
    "Content-Type": "application/x-www-form-urlencoded"
  },
  body: new URLSearchParams({
    text: "Hello this is Ryan speaking",
    voice: "ryan"
  })
});

const audioBlob = await response.blob();

const audioUrl = URL.createObjectURL(audioBlob);

const audio = new Audio(audioUrl);
audio.play();

This is how the client website plays the speech.