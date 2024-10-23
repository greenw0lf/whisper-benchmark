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
- [faster-whisper-batched](https://github.com/SYSTRAN/faster-whisper/pull/856) (faster-whisper with batching support added)
- [OpenAI/Whisper](https://github.com/openai/whisper)
- [Whisper JAX](https://github.com/sanchit-gandhi/whisper-jax)

## Output

The output can be found in `output.tar.gz`. This contains the transcripts generated by the different Whisper implementations, logs, and stats about how much time/memory it took to complete the individual files.

The structure is as follows:
```
├── Broadcast News
└── Conversational Telephone Speech
    ├── faster-whisper
    .
    .
    .
    └── whisperx
        ├── float16
        └── float32
            ├── large-v2
            └── large-v3
                ├── labelled
                └── unlabelled
                    ├── info.csv - contains stats per file
                    ├── log.txt - log output of the notebooks
                    .
                    .
                    .
                    └── nbest_eval_..._1.json
```

## Results

The WER scores + alignment files can be found under `results`. They are structured in a similar way as to the output described above. Only difference is the filename template for the ref(erence) and hyp(othesis) files:
```
fp{AA}_v{B}.{CCC}
```

Where:
- `AA`: 16 or 32, corresponding to `float16` or `float32` respectively
- `B`: 2 or 3, corresponding to Whisper `large-v2` or `large-v3`
- `CCC`: `ctm` for hyp, `stm` for ref

Each implementation contains a `hyp` folder corresponding to the transcription generated by that implementation (in `ctm` format), and a `results` folder which contains the WER, insertion, deletion, and substitution scores, as well as a file that shows the alignments between the hypothesis and reference segments:

- `.dtl` files contain the scores
- `.prf` files contain the alignments

There is also a `ref` folder under each subset (Broadcast News or Conversational Telephone Speech) that contains the `stm` reference files.

For more information about the `CTM` or `STM` formats of the hypothesis and reference respectively, check out [this repository](https://github.com/opensource-spraakherkenning-nl/ASR_NL_benchmark).
