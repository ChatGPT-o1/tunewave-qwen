# Notice

This repository contains a modified version of Qwen3.5-0.8B
(https://huggingface.co/Qwen/Qwen3.5-0.8B), Copyright the Qwen team, Alibaba Cloud,
licensed under the Apache License, Version 2.0.

Changes: the text model's weights were quantized to 4 bits (Q4_1, groups of 32), the vision
encoder and multi-token-prediction weights were removed, and the result was split into worker
shares and fixed-size pieces for loading in Roblox.
