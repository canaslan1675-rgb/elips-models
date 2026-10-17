# elips-models

ONNX int8 model files used by the Elips Android app for offline English → Turkish translation.

## Model

- **Original model:** [Helsinki-NLP/opus-mt-tc-big-en-tr](https://huggingface.co/Helsinki-NLP/opus-mt-tc-big-en-tr) (OPUS-MT, Jörg Tiedemann & Santhosh Thottingal et al.)
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- **Modifications:** the original model was converted to ONNX (encoder, decoder, decoder-with-past) and dynamically quantized to int8 (optimum + onnxruntime `quantize_dynamic`). Tokenizer/vocabulary were exported to `vocab.json` / `src_spm.tsv`; `elips-mt.json` holds small app config. No other changes were made.
- This conversion is not endorsed by the original authors.

## Files

See the release `opus-mt-en-tr-int8`; integrity values are in `SHA256SUMS`.

## Citation

Tiedemann & Thottingal, "OPUS-MT — Building open translation services for the World", EAMT 2020.
