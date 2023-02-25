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

## Usage

### Setup

You can install dependencies with
[`conda`](https://en.wikipedia.org/wiki/Conda_(package_manager)) or
[`pipenv`](https://pipenv.pypa.io/en/latest/).

#### conda

```sh
conda env create
conda activate algal  # To use the conda environment.
```

#### pipenv

```sh
pipenv install
pipenv shell  # To use the Python virtual environment.
```

### Running the notebooks

You can open the notebooks in any application that supports viewing and running
Jupyter notebooks. I suggest VS Code, which I used, but you could also use
JupyterLab or other applications.

Whatever you use, you should make sure the conda environment (if you used
`conda`) or the Python virtual environment (if you used `pipenv`) is activated
in the application. This is often separate from the `conda activate algal` and
`pipenv shell` commands. In VS Code, you select this for a notebook near the
upper right of the window.

### Where it looks for API keys

As written, the HuggingFace token and OpenAI API key are expected to be found
in files called`.hf_token` and `.openai_key`, respectively. Make sure not to
commit those files! They are included in `.gitignore`.

You can make those files, or change the code accordingly to look elsewhere. If
you supply your OpenAI API key as `OPENAI_API_KEY` environment variable, then
the OpenAI Python library will find and use it automatically, and no
key-related logic is needed in the code. You should probably not put your keys
in the code itself, even if you’re not currently planning to commit the change,
since this runs a high risk of accidentally committing them later.

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

For a somewhat similar approach to accessing BLOOM from a Jupyter notebook that
is more user-friendly and versatile, see
[complete](https://github.com/EliahKagan/complete).

### Embeddings

#### Ada 2

[text-embedding-ada-002](https://platform.openai.com/docs/guides/embeddings/second-generation-models),
OpenAI’s [second generation embedding
model](https://openai.com/blog/new-and-improved-embedding-model/), which is
suitable for small and large texts (up to 8191 tokens) as well as code, is used
for sentence embeddings in:

- [`ada.ipynb`](ada.ipynb) - accessing it via the [OpenAI Python
  library](https://github.com/openai/openai-python)

That notebook also explores the token encoding used by that model, and shows
some examples comparing it to the older encoding used by GPT-2 and GPT-3.

For more on accessing OpenAI embeddings from Python—besides the official
resource [openai-cookbook](https://github.com/openai/openai-cookbook) (which is
the most important place to find examples)—see
[bed](https://github.com/EliahKagan/bed) and
[embed-encode](https://github.com/EliahKagan/embed-encode).

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
domain, is used, both with and without intentional modification, as model
input.

See [`the_open_window.md`](the_open_window.md) for details.

### Happy person/dog, sunny day

These four phrases, which I use in a few important places, are the example text
from the hosted inference widget on HuggingFace:

- “That is a happy person”
- “That is a happy dog”
- “That is a very happy person”
- “Today is a sunny day”
