# elips-models

Model files used by the [Elips](https://github.com/canaslan1675-rgb/elips) Android app (on-device live captions / translation). Integrity values for every release are in its `SHA256SUMS`.

## 1. Whisper TR small v1 — Turkish speech recognition (release `whisper-tr-small-v1`)

- **File:** `elips-whisper-tr-small-v1.tar.bz2` (209,282,047 bytes, sha256 `0a9d4df2767599cf6902e5fcf26fec71314ca3f8dda4bfd6794d11b6a1236ec3`)
- **Contents:** `small-tr-encoder.int8.onnx`, `small-tr-decoder.int8.onnx`, `small-tr-tokens.txt`, `elips-model.json`, `CREDITS.txt`
- **Description:** [openai/whisper-small](https://huggingface.co/openai/whisper-small) fully fine-tuned for Turkish, then converted to ONNX int8 for [sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) 1.13.8.
- **Quality:** WER 0.1503 on the MediaSpeech Turkish test split (test split was not used in training).
- **License of the package:** MIT (derived from the MIT-licensed Whisper weights). The training data licenses below require attribution, which is given here.

### Base model
- OpenAI Whisper small — MIT License — Radford et al., "Robust Speech Recognition via Large-Scale Weak Supervision", 2022. https://github.com/openai/whisper

### Training data and attribution
- **YODAS** (`espnet/yodas`, subset `tr000`, filtered ≈ 46.6 h) — [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/). Attribution: YODAS dataset authors, Li et al., "YODAS: YouTube-Oriented Dataset for Audio and Speech", 2023.
- **MediaSpeech** (OpenSLR SLR108, Turkish, train split ≈ 7.75 h) — [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Attribution: Ferrero et al., "MediaSpeech: Multilanguage ASR Benchmark and Dataset", 2021. https://www.openslr.org/108/
- **Mozilla Common Voice 27, Turkish** (train ≈ 45.3 h) — [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Used for training only; no Common Voice audio or text is included in this package.

### Modifications
The Whisper-small weights were changed by full fine-tuning (training run "egitim4", step 1500) on the data above, and then converted to ONNX with int8 dynamic quantization (sherpa-onnx tooling). No other changes. This model is not endorsed by OpenAI, the dataset authors, or Mozilla.

## 2. Opus-MT tc-big en-tr int8 — English → Turkish translation (release `opus-mt-en-tr-int8`)

- **Original model:** [Helsinki-NLP/opus-mt-tc-big-en-tr](https://huggingface.co/Helsinki-NLP/opus-mt-tc-big-en-tr) (OPUS-MT, Jörg Tiedemann & Santhosh Thottingal et al.)
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- **Modifications:** converted to ONNX (encoder, decoder, decoder-with-past) and dynamically quantized to int8 (optimum + onnxruntime `quantize_dynamic`). Tokenizer/vocabulary exported to `vocab.json` / `src_spm.tsv`; `elips-mt.json` holds small app config. No other changes.
- This conversion is not endorsed by the original authors.
- Citation: Tiedemann & Thottingal, "OPUS-MT — Building open translation services for the World", EAMT 2020.
