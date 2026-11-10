# Image to Three.js miner

Generates a Three.js module for a prompt image through the competition witness: drafts, selection, rewrites against
renders and a final pick, within the per-prompt budget.

Entry point: `main.py` -> `async generate(image, seed, witness) -> str | None`. The plan is in `miner404/versions.py`.

## Live run

```sh
uv venv --python 3.13 .venv-live
uv pip install --python .venv-live/bin/python -r requirements.txt
git clone --branch witness-client-v0.2.19 --depth 1 https://github.com/404-Repo/404-gen-subnet.git ../404-sdk
```

Copy `witness.example.json` to `witness.json` next to `main.py` and set `proof_parameters` to the absolute path of
`404-sdk/witness-server/worker/witness_pod/verifier/params` (the proof parameters of the same SDK tag). Then:

```sh
.venv-live/bin/python main.py --prompts prompts.txt --seed PUBLISHED_SEED --wallet-name NAME --wallet-hotkey HOTKEY
```

`--parallel-preparations N` (default 3) is passed to the miner runtime's batch runner (miner runtime 0.1.6).
