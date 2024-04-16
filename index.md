
<hr style="border: double 1.35px silver;">
## Content
---
- [NMT Architecture](#architecture)
- [Encoding Comparison](#Encoding)
- [Results](#Tables)
- [Generated Results](#generations)
  - [Best unconditioned generation samples](#best-unconditional)
  - [4-measure continuation comparison among models](#continuation)
  - [MAESTRO fine-tuned EnCodec token based continuated generation samples](#encodec)

<hr style="border: double 1.35px silver;">

## NMT Architecture {#architecture}
---
<img src="img/demo_teaser_fig.PNG" style="border: 2px solid grey">

Diagram of different prediction method in subdecoder.
{:.center .larger}
> __Note__: Our proposed Nested Music Transformer (NMT) predicts each feature in a fully-sequential manner, which is different from how the previous decoding architectures work.

<img src="img/demo_subdecoder_fig.PNG" style="border: 2px solid grey" class="wider">

 Illustrations of the proposed Nested Music Transformer (NMT) and other sub-decoder structures
{:.center .larger}
<br>

## Encoding Comparison {#Encoding}
---
<img src="img/demo_encoding_fig.PNG" style="border: 2px solid grey">

An example illustrating proposed representations, note-based encoding (c) NB-Type1st and (d) NB-Pitch1st, alongside REMI and Compound word for the sake of comparison.
{:.center .larger}

> __Note__: All the encodings represent the same piece of music by utilizing 8 features. Specifically, REMI and Compound word weren’t designed for multi-instrument pieces. That’s why we renamed the encoding with “+I” to (a) and (b). However, the main ideas for these two encoding is reserved for (a) and (b). The piece has K number of notes in the representation. If we used F number of different features for the encoding, the scale factors between REMI;r, Compound word;c can be expressed as an inequality like followings: 1 < c <= 2  < r < F. c can reach up to 2 in the case where every notes are positioned differently (no simultaneous note played at the same time).

<hr style="border: double 1.35px silver;">

## Results {#Tables}
---
<img src="tables/dataset_analysis.PNG" style="border: 2px solid grey">
The statistics of the dataset used in the experiments.
{:.center .larger}
<br>

---
<img src="tables/param_dataset.PNG" style="border: 2px solid grey">
The hyperparameters used in the experiments for each dataset.
{:.center .larger}

---
<img src="tables/main_table.PNG" style="border: 2px solid grey">
The main results of the experiments for symbolic music generation. Comparison average NLL loss for each model.
{:.center .larger}

> __Note__: We used total 12 number of layers including number of main deocer layers, sub-decoder layers and feature-enricher layers in case it is utilized. All models are trained with 512 dimension of hidden size and 8 heads of multi-head attention.

## Generated Results {#generations}
---
### Best unconditioned generation samples {#best-unconditional}

> __Settings__: The results of unconditional generation from 4 different datasets are shown. The model is given a random seed with only Start-of-Suence (SOS) token and generates the note sequences.

<div class="table-wrapper" markdown="block">

|  | __Pop1k7__{:.center} | __Pop909__{:.center} | __SOD__{:.center} | __Lakh__{:.center} |
| --- | --- | --- | --- | --- |
| __REMI + flattening__ | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/0_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/2_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/5_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/remi/3_lakh_remi.mp3" %} | 
|  | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/9_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/6_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/10_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/remi/10_lakh_remi.mp3" %} | 
|  | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/23_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/26_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/14_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/remi/20_lakh_remi.mp3" %} | 
| __NB-PF + enricher__ | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/0_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/2_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/5_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/nb/1_lakh_nb.mp3" %} | 
|  | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/9_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/6_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/10_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/remi/10_lakh_remi.mp3" %} | 
|  | {% include audio_player.html filename="audio/symbolic_uncond/pop1k7/remi/23_pop1k7_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/pop909/remi/26_pop909_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/sod/remi/14_sod_remi.mp3" %} | {% include audio_player.html filename="audio/symbolic_uncond/lakh/remi/20_lakh_remi.mp3" %} |

</div>
---
### 4-measure continuation comparison among models {#continuation}

> __Settings__: The model is given a 4-measure length symbolic tokens of selected pieces. The model then generates the note sequences. Selection of pieces for prompt is required as interesting motifs are needed for the continuation.

<div class="table-wrapper" markdown="block">

|  | __Prompt 1__{:.center} | __Prompt 2__{:.center} |
| __REMI + flattening__ | {% include audio_player.html filename="audio/symbolic_continuation/91_01_REMI+flattening.mp3" %} | {% include audio_player.html filename="audio/symbolic_continuation/101_01_REMI+flattening.mp3" %} |
| __CP + Catvec__ | {% include audio_player.html filename="audio/symbolic_continuation/91_02_CP+Catvec.mp3" %} | {% include audio_player.html filename="audio/symbolic_continuation/101_02_CP+Catvec.mp3" %} |
| __CP + enricher__ | {% include audio_player.html filename="audio/symbolic_continuation/91_03_CP+enricher.mp3" %} | {% include audio_player.html filename="audio/symbolic_continuation/101_03_CP+enricher.mp3" %} |
| __NB-PF + enricher__ | {% include audio_player.html filename="audio/symbolic_continuation/91_04_NB-PF+enricher.mp3" %} | {% include audio_player.html filename="audio/symbolic_continuation/101_04_NB-PF+enricher.mp3" %} |
| __Ensemble__ | {% include audio_player.html filename="audio/symbolic_continuation/91_05_Ensemble.mp3" %} | {% include audio_player.html filename="audio/symbolic_continuation/101_05_Ensemble.mp3" %} |

</div>
---
### MAESTRO fine-tuned EnCodec token based continuated generation samples {#encodec}

> __Settings__: The model is given a 10-second length audio sample in EnCodec tokens. The model then generates the note sequence.

<div class="table-wrapper" markdown="block">

|  | __Prompt 1__{:.center} | __Prompt 2__{:.center} |
| __Parallel__ | {% include audio_player.html filename="audio/encodec_continuation/1_00_Parallel.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_00_Parallel.wav" %} |
| __Flatten__ | {% include audio_player.html filename="audio/encodec_continuation/1_01_Flatten.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_01_Flatten.wav" %} |
| __Delay__ | {% include audio_player.html filename="audio/encodec_continuation/1_02_Delay.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_02_Delay.wav" %} |
| __Self_attn__ | {% include audio_player.html filename="audio/encodec_continuation/1_05_Selff-attn.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_05_Selff-attn.wav" %} |
| __Cross_attn__ | {% include audio_player.html filename="audio/encodec_continuation/1_06_Cross-attn.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_06_Cross-attn.wav" %} |
| __Enricher__ | {% include audio_player.html filename="audio/encodec_continuation/1_07_Enricher.wav" %} | {% include audio_player.html filename="audio/encodec_continuation/3_07_Enricher.wav" %} |

</div>
<hr style="border: double 1.35px silver;">