# Qwen3.5-0.8B, 4-bit, for the Tunewave Roblox game

These files are [Qwen/Qwen3.5-0.8B](https://huggingface.co/Qwen/Qwen3.5-0.8B)'s text model,
converted to 4 bits and cut into pieces so a Roblox game server can download it with HttpService
and run it in Luau. They are not useful outside that runtime.

- Format: Q4_1 in groups of 32 weights (weight = q * scale + min, q 0..15, float16 scale and min).
  Norms, gates and the short convolution stay float32. The image encoder and the multi-token
  prediction head were dropped.
- Layout: `w4/<i>/` is worker i's share when one reply is split over 4 Parallel Luau workers
  (attention heads, feed-forward units and vocabulary rows divided between them);
  `manifest.json` says where each tensor sits in the share, `part<k>.bin` are its 16 MB pieces.
- `tokenizer/` holds the byte-level BPE vocabulary and merges.

Made with the Tunewave tools (roblox/tools/qwen_convert.py, qwen_package.py).

## License

The model is by the Qwen team and released under the Apache License 2.0 (see LICENSE).
These files are a modified version: converted to 4-bit and rearranged (see NOTICE.md).
