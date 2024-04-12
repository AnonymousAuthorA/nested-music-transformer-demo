## Content

- [NMT Architecture](#architecture)
- [Generated Results](#generations)
  - [Best unconditioned generation samples](#best-unconditional)
  - [4-measure continuation comparison among models](#continuation)
  - [MAESTRO fine-tuned EnCodec token based continuated generation samples](#encodec)

---

## NMT Architecture {#architecture}

<img src="img/diagram.PNG" style="border: 2px solid grey">

Diagram of the Nested Music Transformer
{:.center .larger}
<br>
<br>
<img src="img/structure.PNG" style="border: 2px solid grey" class="wider">

Multiple architectures of the Nested Music Transformer
{:.center .larger}
<br>

> __Note__: All the samples are generated in single pass through the model using a sequence length of 1024. Thus, the generated music is usually shorter for a more complex ensemble than a simple ensemble.

---

## Generated Results {#generations}

### Best unconditioned generation samples {#best-unconditional}

> __Settings__: The results of unconditional generation from different models.

<div class="table-wrapper" markdown="block">

| {% include audio_player.html filename="audio/unconditional/1.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/2.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/3.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/4.mp3" style="width:240px;" %} |
| {% include audio_player.html filename="audio/unconditional/5.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/6.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/7.mp3" style="width:240px;" %} | {% include audio_player.html filename="audio/unconditional/8.mp3" style="width:240px;" %} |

</div>
---
### 4-measure continuation comparison among models {#continuation}

> __Settings__: The model is given a 4-measure length of piece as prompt. The model then generates the note sequence.

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

---