# Elk_Draw add-ons

Optional parts of [Elk_Draw](https://github.com/AllexSpectra) that are too large for its installer. Elk_Draw
downloads them itself, the first time they are needed, with a **Download** button in the window that uses them.
Each download is checked against its SHA-256 and installed for the current user in
`%LocalAppData%\Programs\Elk_Draw`. Nothing else has to be installed.

The files are in the release [addons-1](../../releases/tag/addons-1).

| File | Size | Used by | Unpacks to |
|---|---|---|---|
| `decimer-onnx.zip` | 276 MB | Structure › Insert Structure from Image (DECIMER on this computer) | `decimer/onnx/DECIMER` |
| `decimer-onnx-handdrawn.zip` | 276 MB | the same, with **Hand-drawn** ticked | `decimer/onnx/DECIMER_HandDrawn` |
| `orthonym-win-x64.zip` | 114 MB | Structure › Name Structure (Windows x64) | `orthonym` |

SHA-256:

```
0dcf0b46aa1736e58374071cff11a0014e7577d4c421847fcd8b3d06787bf2ba  decimer-onnx.zip
41b20c4403fd2bc0b18252cd095455236fa0c9104b001b90196089c28c93bcb1  decimer-onnx-handdrawn.zip
d611c837e2059eacb713889d4246b31c341ec9693b021fdf4414ad3d5c97339e  orthonym-win-x64.zip
```

## Credits and licences

### DECIMER models

The DECIMER Image Transformer models, **converted** from the TensorFlow saved_model to ONNX (encoder and decoder)
and the tokenizer to JSON, so that Elk_Draw runs them with ONNX Runtime without Python. The weights are otherwise
unchanged.

- Weights: K. Rajan, H. O. Brinkhaus, A. Zielesny, C. Steinbeck, "DECIMER V2 Models" v2.4, Zenodo,
  [doi:10.5281/zenodo.8300489](https://doi.org/10.5281/zenodo.8300489), and "DECIMER V2 – Hand drawn Model"
  v1.0.0, Zenodo, [doi:10.5281/zenodo.10781330](https://doi.org/10.5281/zenodo.10781330), licensed under
  [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
- DECIMER: K. Rajan et al., "DECIMER.ai: an open platform for automated optical chemical structure
  identification, segmentation and recognition in scientific publications", Nat. Commun. 2023, 14, 5045;
  code under the MIT licence, [github.com/Kohulan/DECIMER-Image_Transformer](https://github.com/Kohulan/DECIMER-Image_Transformer).

Each model folder holds a `CREDIT.txt` with the same.

### Orthonym pack

[Orthonym](https://github.com/Steinbeck-Lab/Orthonym) (MIT; K. Rajan, A. Zielesny, C. Steinbeck, ChemRxiv 2026,
doi:10.26434/chemrxiv.15009769) with everything it needs, unchanged:

- Python 3.12 (python.org embeddable build) – PSF licence
- RDKit, numpy, lxml – BSD; JPype – Apache 2.0; Pillow – MIT-CMU (licences in each package's `dist-info`)
- a Java 21 runtime cut with jlink from Eclipse Temurin – GPLv2 with the Classpath Exception (`jre/legal`)
- OPSIN – MIT, [github.com/dan2097/opsin](https://github.com/dan2097/opsin)
- centres – LGPL 2.1 or later, [github.com/SiMolecule/centres](https://github.com/SiMolecule/centres), holding the
  CDK – LGPL 2.1 or later, [github.com/cdk/cdk](https://github.com/cdk/cdk); the sources are at those addresses

The pack's `README.txt` lists every part. It is made with `tools/orthonym/make_pack.py` in the Elk_Draw sources.
