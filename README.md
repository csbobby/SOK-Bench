# SOK-Bench
**[CVPR 2024] SOK-Bench: A Situated Video Reasoning Benchmark with Aligned Open-World Knowledge**

<!-- 
Reasoning from visual dynamics scenes has many real-world applications. However, existing video reasoning benchmarks are still inadequate since they were mainly designed for factual or situated reasoning and rarely involve broader knowledge in the real world.
-->

Our work aims to delve deeper into reasoning evaluations, specifically within dynamic, open-world, and structured context knowledge. 
We propose a new benchmark, consisting of 44K questions and 10K situations with instance-level annotations depicted in the videos. The reasoning process is required to understand and apply situated knowledge and general knowledge for problem-solving.
Concretely, we first extract observable situated entities, relations, and processes from videos for situated knowledge and then extend to open-world knowledge beyond the visible content. 
The task generation is facilitated through multiple dialogues as iterations and subsequently corrected and refined by our designed self-promptings and demonstrations.
With a corpus of both explicit situated facts and implicit commonsense, we generate associated question-answer pairs and reasoning processes, finally followed by manual reviews for quality assurance.

## Benchmark Overview
* 44k Situated Questions
* 12 Qutestion Types
* 10k Situation Video Clips
* Situation Commonsense Knowledge Graphs
* Chain of Reasoning Rationals

<div align="center">
<img src="imgs/fig_overview.png" width="800" >
</div>

## Benchmark Example

<div align="center">
<img src="imgs/fig_qa_examples.png" width="800" >
</div>

## Data Download
Download the SOK-Bench dataset [```sok-bench_v1.json```](https://drive.google.com/file/d/1jWPY4yF-iBChvfN4MmlhXRhUJLySXRne/view?usp=sharing). 

## Dataset Format
Here, we introduce the data format of the SOK-Bench.
The dataset file ```sok-bench.json``` is a collection of data samples which organized as a json dict:
```python
{"type": list_of_questions_in_that_type}
```
Each question itself is a dict with the following entries:
```python
{
    "question": "The question",
    "answer": {
        "direct": "Direct answer to the question",
        "choices": [
            "Choice 0",
            "Choice 1",
            "Choice 2",
            "Choice 3",
            ...
        ],
        "right_choice": 0 # the index of the correct choice
    },
    "related_objs_acts": [
        "object/action 0",
        "object/action 1",
        "object/action 2",
        ... # key objects and actions in the video used to generate questions
    ],
    "related_subgraph": {}, # a knowledge graph of the video
    "video": "video_id",
    "video_path": "relative path to video",
    "rationale": "rationale for the answer",
    "time_slot": [
        start_time,
        end_time
    ]
}
```
Here is a data sample [`example_question.json`](data/example_question.json) for a better and quick exploration of the data format.


## Video Source 
### YouCook2

1. Install pytube with `pip install pytube`
2. Download YouCook2 with `download_YouCook2.py` (put `splits` folder in the same directory)
3. Organize `QAs_with_rationale_for_pub_corrected.json` and downloaded data as follows:
```
data/
├── QAs_with_rationale_for_pub_corrected.json
├── videos_mp4/
```
### HOMAGE
The videos of HOMAGE dataset provided on their [website](https://homeactiongenome.org/). Please refer to their [download page](https://homeactiongenome.org/download.html) for more information.

## Citation
Please link back and cite the work if you would like to use the website template.
```BibTeX
@inproceedings{SOK_Bench,
author={Wang*, Andong and Wu*, Bo and Chen, Sunli and Chen, Zhenfang and Guan, Haotian and Lee, Wei-Ning and Li, Erran Li and Tenenbaum, Joshua B and Gan, Chuang},
title = {SOK-Bench: A Situated Video Reasoning Benchmark with Aligned Open-World Knowledge},
booktitle = {The IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
year = {2024}
}
```

