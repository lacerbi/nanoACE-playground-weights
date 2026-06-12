# nanoACE Playground Weights

This repository stores the exported browser model weights for the
[nanoACE](https://github.com/acerbilab/nanoACE) web playground.

The main nanoACE repository keeps the source code, examples, and TypeScript
playground. The weight blobs live here separately so normal nanoACE clones stay
small, while the GitHub Pages deployment workflow can still fetch the pretrained
browser models and build a working static demo.

Expected layout:

```text
bo1d/manifest.json
bo1d/weights.bin
gaussian/manifest.json
gaussian/weights.bin
gp1d/manifest.json
gp1d/weights.bin
sbi_sir/manifest.json
sbi_sir/weights.bin
```

These files are generated from nanoACE checkpoints with:

```bash
python playground/export_weights.py --task gp1d     --checkpoint artifacts/gp1d.pt         --out playground/public/models/gp1d
python playground/export_weights.py --task gaussian --checkpoint artifacts/gaussian_toy.pt --out playground/public/models/gaussian
python playground/export_weights.py --task sbi_sir  --checkpoint artifacts/sbi_sir.pt      --out playground/public/models/sbi_sir
python playground/export_weights.py --task bo1d     --checkpoint artifacts/bo1d.pt         --out playground/public/models/bo1d
```

The weights are exported as little-endian IEEE float16 blobs plus JSON manifests.
They are intended for the nanoACE playground's in-browser TypeScript forward
pass, not as general-purpose model checkpoints.

