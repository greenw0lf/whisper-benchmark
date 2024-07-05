# whisper-benchmark
Files used for benchmarking various implementations of Whisper, done as part of my work at University of Twente + Netherlands Institute for Sound and Vision on the OH-SMArt project.

For files used for preprocessing/postprocessing of the transcriptions, check here: https://github.com/greenw0lf/OH-SMArt

Results: https://opensource-spraakherkenning-nl.github.io/ASR_NL_results/ (under NISV's Whisper benchmark).

## Python versions

`Python 3.12.3` was used for creating the virtual environments of:
- [WhisperX](https://github.com/m-bain/whisperX)
- [Huggingface (HF) `transformers`](https://huggingface.co/docs/transformers/index)

Whereas for the other implementations, `Python 3.9.18` was used:
- [faster-whisper](https://github.com/SYSTRAN/faster-whisper/)
- [OpenAI/Whisper](https://github.com/openai/whisper)
- [Whisper JAX](https://github.com/sanchit-gandhi/whisper-jax)
