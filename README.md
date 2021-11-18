## Introduction

Learn to Copy from the Copying History: Correlational Copy Network for Abstractive Summarization

## Installation

- PyTorch: 1.5.0
- Fairseq: 0.10.1   

## Train

```sh
export CUDA_VISIBLE_DEVICES=0,1,2,3,4,5,6,7

fairseq-train data-bin \
    --user-dir src \
    --load-from-pretrained-model /path/to/bart.large/model.pt \
    --max-tokens 8192 \
    --task translation \
    --source-lang source \
    --target-lang target \
    --truncate-source \
    --layernorm-embedding \
    --share-all-embeddings \
    --share-decoder-input-output-embed \
    --reset-optimizer \
    --reset-dataloader \
    --reset-meters \
    --required-batch-size-multiple 1 \
    --arch bart_copy_large \
    --criterion label_smoothed_cross_entropy \
    --label-smoothing 0.1 \
    --dropout 0.1 --attention-dropout 0.1 \
    --weight-decay 0.01 \
    --optimizer adam \
    --adam-betas "(0.9, 0.999)" \
    --adam-eps 1e-08 \
    --clip-norm 0.1 \
    --lr-scheduler polynomial_decay \
    --lr 3e-5 \
    --total-num-update 2000000 \
    --warmup-updates 500 \
    --fp16 --update-freq 4 \
    --skip-invalid-size-inputs-valid-test \
    --find-unused-parameters
```
