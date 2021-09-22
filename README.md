# bioseq

A C++/Python package performing fast one-hot encoding for DNA or Protein sequences with C++ code, optionally converting to pytorch and moving to device.

Offers 4-letter DNA, 20-letter amino acid, and a variety of other compressed protein and DNA alphabets, and optionally is parallelized.

Most of this is used via bioseq.Tokenizer.

Tokenizer can tokenize (`batch_tokenize`), which creates array of tokens, (char by default),
or it can one-hot encode (`batch_onehot_encode`), which takes the tokens one-step further into one-hot encoding.
Both of these `Tokenizer::batch_*` functions can be parallelized by providing `nthreads={int}`.

tokenizing uses seq-first ordering by default as well, but this can be changed with `batch_first=True`.
one-hot encoding uses seq-first ordering (not batch-first). It does not support `batch_first`.

Both of these are ~30x as fast as using bytes.translate + np.frombuffer + np.vstack + `torch.from_numpy`.


## Dependencies

pybind11 v2.7 is required, in order to support bytearray
numpy is required
pytorch (as torch) is also required

Besides these, there are some python-only dependencies which setup.py should download for you.

All of these should be installed via `python3 -m pip install -r requirements.txt`.
