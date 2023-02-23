<!-- SPDX-License-Identifier: 0BSD -->

# algal - hosted NLP model API example bikeshed

These are some examples of accessing language models remotely through APIs.
They didn’t fit, in this form, in other repositories, so I’ve put them here.

It’s one notebook per model, currently. Most of the notebooks access models
hosted on HuggingFace, by using the [Inference
API](https://huggingface.co/inference-api). But one notebook,
[`ada.ipynb`](ada.ipynb), accesses an [OpenAI](https://openai.com/api/) model.

## License

This repository is licensed [0BSD](https://spdx.org/licenses/0BSD.html). See
[**`LICENSE`**](LICENSE).

## Models used

### Completion (text generation)

#### BLOOM

[BLOOM](https://huggingface.co/bigscience/bloom), a large language model, is
used for text generation/completion in:

- [`bloom_raw.ipynb`](bloom_raw.ipynb) - accessing it by doing explicit HTTP
  POST requests via [Requests](https://requests.readthedocs.io/en/latest/)
- [`bloom.ipynb`](bloom.ipynb) - [accessing it
  via](https://huggingface.co/docs/huggingface_hub/how-to-inference) the
  [`huggingface-hub`
  library](https://huggingface.co/docs/huggingface_hub/index)

### Embeddings

#### Ada 2

[text-embedding-ada-002](https://platform.openai.com/docs/guides/embeddings/second-generation-models),
OpenAI’s [second generation embedding
model](https://openai.com/blog/new-and-improved-embedding-model/), which is
suitable for small and large texts (up to 4000 tokens) as well as code, is used
for sentence embeddings in:

- [`ada.ipynb`](ada.ipynb) - accessing it via the [OpenAI Python
  library](https://github.com/openai/openai-python)

That notebook also explores the token encoding used by that model, and shows
some examples comparing it to the older encoding used by GPT-2 and GPT-3.

#### FLAX Sentence Embeddings

[flax-sentence-embeddings/all_datasets_v3_roberta-large](https://huggingface.co/flax-sentence-embeddings/all_datasets_v3_roberta-large),
a model trained for sentence embeddings, is used in:

- [`flax.ipynb`](flax.ipynb) - [accessing it
  via](https://huggingface.co/docs/huggingface_hub/how-to-inference) the
  [`huggingface-hub`
  library](https://huggingface.co/docs/huggingface_hub/index)

## Credits for model inputs

Some model inputs, such as the prompts for text generation and the silly
phrases I explore tokenization with in [`ada.ipynb`](ada.ipynb), are
spontaneous examples I came up with.

However, there are two inputs that are not due to me and that I wish to credit:

### “The Open Window”

The short story “The Open Window” by Saki (H.H. Munro), which is in the public
domain, is used, including with modification, as model input.

See [`the_open_window.md`](the_open_window.md) for details.

### Happy person/dog, sunny day

These four phrases, which I use in a few important places, are the example text
from the hosted inference widget on HuggingFace:

- “That is a happy person”
- “That is a happy dog”
- “That is a very happy person”
- “Today is a sunny day”
