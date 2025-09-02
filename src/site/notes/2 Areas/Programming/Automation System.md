---
{"dg-publish":true,"permalink":"/2-areas/programming/automation-system/"}
---



https://github.com/VYNCX/F5-TTS-THAI

## MMPEG concat
`ffmpeg -f concat -i vid_list.txt output.mp4`
## Create voiceover
https://n8n.io/workflows/3547-convert-text-to-speech-with-local-kokoro-tts/
https://github.com/PierrunoYT/Kokoro-TTS-Local

## Transcribe and create .srt file
https://github.com/openai/whisper
`whisper output.mp4 --model tiny --output_format srt`
## Break long video into short video
`ffmpeg -i input.mp4 -c copy -map 0 -segment_time 600 -f segment output_%03d.mp4`

## Youtube Shorts
- [[Why your shorts are missing the algorithm\|Why your shorts are missing the algorithm]]
- [[RIght way to upload shorts\|RIght way to upload shorts]]

## node.js and npm
when you install node.js, it comes with npm (node package manager)


## Autocreating multiple video with template
- Canva with Bulk Editing function can do that, it could import data from csv files. However, PRO plan is required. (education not suitable)

## JSON2Videos
My personal API key: **d7vctLcKZLNDG3y8ec6nDIvwfnyEGFA7Xq0NUdqH**
- Free access to all JSON2Video API features
- Up to 600 seconds of video rendering
- Movies up to 3 minute long
- Access to template editor

## Pexel
API Key: TDsyUL5FPIiylnu3cDK2TQ7GDCZeL3ioElbksCggX1vA2iN4FELflQZl
`docker run -it --rm --name short-video-maker -p 3123:3123 -e LOG_LEVEL=debug -e PEXELS_API_KEY=TDsyUL5FPIiylnu3cDK2TQ7GDCZeL3ioElbksCggX1vA2iN4FELflQZl gyoridavid/short-video-maker:latest-tiny`

## MCP and SSE
### **MCP Server-Sent Events Endpoint**
- **MCP** likely stands for **Message Communication Protocol** or a similar messaging/control system used by the application you're working with
- **SSE** = **Server-Sent Events**
    - A standard for pushing updates from the server to the browser/client over HTTP
    - SSE allow you to keep connection with the server, to receive an update from the server (connect to server once, keep receiving the data)