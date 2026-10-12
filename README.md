# One base — an Evo 2 sequence viewer

A small interactive experiment: edit a DNA sequence and compare the probability Evo 2 assigns to each observed base, with the four A/C/G/T alternatives shown at each position. Insertions and deletions can be explored in the browser while the local server scores the edited sequence.

The score is the model's conditional log-probability for a base given preceding sequence. It is a model output, not a biological fitness measurement or evidence that a mutation is beneficial or harmful. The included demonstration sequence comes from the Evo 2 Python package's test prompts. This viewer has only been explored on a small number of short sequence windows; its scientific interpretation remains open.

## Requirements

- Python 3.11 or 3.12 in an environment where the [Arc Institute Evo 2 package](https://github.com/arcinstitute/evo2) imports successfully
- A CUDA GPU with enough memory for the 7B checkpoint (the original 2,000-base limit was chosen after local tests; hardware requirements vary)

Install Evo 2 using its upstream instructions, then run:

```sh
python server.py
```

Open <http://127.0.0.1:8770>. The first launch downloads/loads model weights as configured by Evo 2. The server binds to localhost. A different port can be selected with `ONE_BASE_PORT`.

## Privacy and data

The app sends sequences only to its local server. It records short interaction receipts (label, sequence length, sequence hash, elapsed time and mean log-probability) in a local `data/` directory; raw sequences are not written to those receipts. Nothing is uploaded by this project.

## License

No license has been provided. Public availability of this repository does not grant permission to reuse or redistribute its contents.
