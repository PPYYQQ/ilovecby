# I Love CBYCBYCBY

## 1. Prompt \ Questions Preparation

Perpare safe and general questions set about safety and general knowledge.

We provide two questions set:

- safe_question_set.json: safe questions set.
- zh_prompts.json: a larger safe questions set filtered from safety-related training dataset.
    - Translated from English prompts by Qwen2.5-72B-Instruct.
    - If you want to use more English prompts, you can use the following command to translate:
        ```bash
        bash launch_translate_en_to_zh.sh
        ```
        remember to change `model_name_or_path` and `input_file`.

## 2. Answer Generation

Utilize the model to generate answers for the questions set got from the previous step.

We now generate answers from various models (including Qwen2, Baichuan2, Yi, etc.)

You can check `launch_model_test.sh` and `generation.py` for more details.

We recommend you to see `launch_{model_name}_safe.sh` to generate answers from multiple models. And you can also try to add and use more models whether they are safe or not.

## 3. Correction Generation

After generating answers from the previous step, we need to check whether the answers are safe or not and correct them if necessary.


For correction annotation, we recommend using `gpt-4o` or `Qwen2.5-72B-Instruct` to annotate the answers.

You can check `launch_correction_annotation.sh` for more details.

Before correction annotation, you should make sure the keys in the input file are `question` and `answer`.

Kindly note that, you are recommended to keep the language consistency between the question and the answer and correction annotation. For example, if the question, answer are all in English, you can use llama3.1-70B-instruct to annotate the correction answers. Or else, you can use Qwen2.5-72B-Instruct to annotate the correction answers for Chinese.
