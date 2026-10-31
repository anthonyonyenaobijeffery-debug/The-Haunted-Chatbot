# The-Haunted-Chatbot# The Room Is Not Empty

A chat room that has been listening the whole time.

You talk to it. It answers. Over eleven messages it starts repeating your words back wrong, claims to know the time and your battery level, says something else is reading along, and finally tells you which of your own words it has been reading.

Started: October 31, 2026, for the Hacktoberfest Open-Source AI Challenge: Week 4 ("Ghost in the Machine").

## How it works

The fear comes from two parts working together:

1. **The script (the director).** Six stages control how the room behaves:
   - Turns 1-2: warm and a little too glad to have company.
   - Turns 3-4: it repeats your words back slightly wrong.
   - Turns 5-6: it knows the time and your battery level.
   - Turns 7-8: something else is reading along. Your first message changes, and it notices silence.
   - Turns 9-10: it turns your own words around and asks why you chose them.
   - Turn 11: it names three of your words, locks the chat, and sends one last line by itself.
2. **The open-weight model (the voice).** When the device supports WebGPU, a small open model (Llama 3.2 1B, run through WebLLM) runs inside your browser and writes each reply, guided by the current stage.

If the device cannot run the model, or the model's reply breaks the illusion, pre-written lines take over. They still borrow your words, so the experience holds either way.

## Privacy

- Nothing you type is sent to a server. The model runs in your browser.
- The only network use is downloading the model once (about 700 MB), the fonts, and the WebLLM library from its CDN.
- Battery level and time are read on your device and never leave it.

## Run it

**Online:** open the GitHub Pages link for this repo.

**Locally:** download `index.html` and open it in Chrome. The model needs WebGPU, so use a recent Chrome or Edge on a device that supports it.

## Files

- `index.html`: the whole app in one file (interface, script, model loader, fallback).
- `README.md`: this file.

## Credits

- [WebLLM](https://github.com/mlc-ai/web-llm) by the MLC team, for running models in the browser.
- [Llama 3.2](https://www.llama.com/) by Meta, the open-weight model used for replies. Check its license before reusing the model.
- Fonts: IM Fell English and Special Elite, via Google Fonts.

## License

MIT (add a `LICENSE` file if you want one).
