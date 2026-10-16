# GRAFT: Grid-Aligned FP4 Trellis Quantization for FP4-Native Language Models

Emi Huang

**Paper:** [GRAFT.pdf](GRAFT.pdf)

## Abstract

Frontier mixture-of-experts (MoE) models increasingly release their routed experts only in MXFP4 (4.25 bits per weight). Current methods that go below this rate treat the experts as continuous weights; EXL3, for example, rotates them with random Hadamard transforms and codes them with a Gaussian-matched trellis. An MXFP4 matrix, however, is a discrete source on a known grid, and at 3 bits its memoryless distortion–rate function is about 0.6× that of a Gaussian source of the same variance. We present GRAFT (GRid-Aligned FP4 Trellis), a 3-bit trellis code that keeps EXL3's trellis and state hash, drops the rotation and uses a grid-aligned value map, so that it decodes to MXFP4 blocks with a per-column output scale and a sparse tail correction. On the routed experts of DeepSeek-V4.1-Flash at 3.006 bits per weight, GRAFT's held-out expert error is 0.63× that of EXL3 at 3 bits (lower on all but 11 of the 15,358 experts with held-out rows) and 0.66× that of EXL3 refitted with GRAFT's own fitting objective. Its excess NLL over the native model is 0.0085 nats, against 0.0131 for EXL3, and 0.0095 when its MXFP4 blocks run through the model's own MXFP8×MXFP4 expert kernel. The smaller representation reduces weight traffic, but whether it also raises throughput depends on overlapping the decode with memory access, which we do not measure here.

## Source

`paper/` contains the LaTeX source. To build it:

```
cd paper
tectonic paper.tex
```

## Citation

```bibtex
@misc{huang2026graft,
  title        = {{GRAFT}: Grid-Aligned {FP4} Trellis Quantization for {FP4}-Native Language Models},
  author       = {Huang, Emi},
  year         = {2026},
  howpublished = {\url{https://github.com/coolbho3k/GRAFT}}
}
```
