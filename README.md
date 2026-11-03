# UNSEEN

Something was already in this room when you arrived.

UNSEEN is a chat room that gets worse the longer you stay. It starts warm, then repeats your words back slightly wrong, reacts to the time of day, notices when you leave, and by the eleventh message it names three of your own words, locks the chat, and says it is still there.

Started: October 31, 2026, for the Hacktoberfest Open-Source AI Challenge: Week 4 ("Ghost in the Machine").

## Changes after the deadline

The submission closed on October 31, 2026 at 11:59 PM PDT. The changes below were made after that time, as the challenge rules require them to be noted here:

- Renamed the project from "The Room Is Not Empty" to UNSEEN.
- Added the entry screen, typed lines, the occupancy counter, and older messages that fade.
- Moved most lines to the script, added time-of-day lines (night, day, evening), and stopped lines from repeating within a session.
- Added reactions to the device: leaving and returning, screen rotation, narrow screen, going offline and back online, charging, pasting, typing pauses, time spent in the room, and phone language.
- Updated this README to list every device signal the room uses.


## How it works

The fear comes from two parts working together:

1. **The script (the director).** Six stages control how the room behaves:
   - Turns 1-2: warm, and a little too glad to have company.
   - Turns 3-4: it repeats your words back slightly wrong.
   - Turns 5-6: it reacts to the time on your device. Late at night it tells you that you should not be awake. In the day and evening it says something different.
   - Turns 7-8: a second presence joins. Your first line changes, and it notices silence.
   - Turns 9-10: it turns your own words around and asks why you chose them.
   - Turn 11: it names three of your words, locks the chat, and sends one last line by itself.
2. **The open-weight model (the voice).** On devices with WebGPU, a small open model (Llama 3.2 1B, run through WebLLM) runs in your browser. It writes the replies that quote your words. Everything else is written by the script.

If the device cannot run the model, or a model reply breaks the illusion, pre-written lines take over. They still borrow your words, so the experience holds either way.

## What the room can notice

UNSEEN only reacts to what your browser already exposes. It never asks for camera, microphone, or location permission.

- **Time of day:** from your device clock, to choose the right lines for night, day, or evening.
- **Battery level and charging:** from the battery status API, where your browser supports it. It notices when you plug in or unplug.
- **Screen size and rotation:** a narrow screen gets a remark about holding the phone close, and rotating the screen gets one about facing the door.
- **Leaving and returning:** when you switch apps or lock the phone, the room notices when you come back.
- **Connection:** it notices when you go offline and when you come back online.
- **Pasting:** a paste of 30 or more characters gets a remark.
- **Typing pauses:** if you stop for 3 seconds or more in the middle of a message, the room asks what you were deciding.
- **Time in the room:** after five minutes, the room says how long you have been there.
- **Language:** if your phone is set to English, the room notes that the phone speaks English and the room does not.

## Privacy

- Nothing you type is sent to a server. Replies are written by the model on your device, or by the script.
- Your typing, pastes, and pauses are measured in the browser and are not stored after the session ends.
- The room does not use the camera, microphone, or location.
- The only network use is downloading the model once (about 700 MB), the fonts, and the WebLLM library from its CDN.
- Resetting the room clears everything the room has noted in that visit.

## Run it

**Online:** open the GitHub Pages link for this repo.

**Locally:** download `index.html` and open it in Chrome or Edge. The model needs WebGPU, so use a recent browser on a device that supports it. Everything else works without it.

## Files

- `index.html`: the whole app in one file (interface, script, device reactions, model loader, fallback).
- `README.md`: this file.

## Credits

- [WebLLM](https://github.com/mlc-ai/web-llm) by the MLC team, for running models in the browser.
- [Llama 3.2](https://www.llama.com/) by Meta, the open-weight model used for the replies that quote your words. Check its license before reusing the model.
- Fonts: IM Fell English and Special Elite, via Google Fonts.

## License

No License
