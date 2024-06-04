
# BTAgent

This repository contains the official code for the paper "BTAgent: Large Language Model for Behavior Tree Generation with Constrained DPO".

### Step 1: Generation
```
python3 generate_instruction_bt.py generate_instruction_following_data
```


The generated data is in json format where each data contains the following attributes:
```
{
    "chosen": [{"role": "user", "content": <prompt>}, 
               {"role": "assistant", "content": <chosen bt>}],
    "rejected": [{"role": "user", "content": <prompt>}, 
                 {"role": "assistant", "content": <rejected bt>}]
}
```


__Example__. 
The following code generates 800 synthetic data for iteration 0.
```
bash scripts/generate.sh
``` 

### Step 2: Fine-tuning
```
accelerate launch --config_file configs/deepspeed_zero3.yaml bt_lora.py configs/config.yaml --num_train_epochs=6
```
<!-- **[TODO]**: wrap up necessary codes into the folder spin. Add explainations/instructions here.  -->

You might need to change the configuration in `configs/config.yaml`.

__Example__.
```
bash scripts/finetune.sh
```