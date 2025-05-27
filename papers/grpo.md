## DeepSeekMath with GRPO

- First trained by 1.3B model, then extended to 7B, outperform most of open-source models (Figure 1)
- Pre-training: DeepSeekMath-Base 7B
  - Process Common_Crawl dataset, classify and identify the Math-related web pages
  - Label the data with few-shot, add example of how to use Math tool (python coding)
  - Pre-train 1.3B model, then extend to DeepSeekMath-Base 7B model (a dense model like Llama)
- SFT: DeepSeekMath-Instruct
  - construct instruction-tuning dataset with CoT, PoT, and tool-integrated reasoning (ToRA) format, by annotating GSM8K and MATH - 776K training samples
    ![image](https://github.com/user-attachments/assets/a7c48f65-b4fd-4ea9-8d58-88527ad8265c)
  - Instruction-tuning
- RL by GRPO: DeepSeekMath-RL
  - Policy gradient ==> using baseline ==> actor-critic ==> advantage actor-critic (A2C) ==> 
  - TRPO (KL: control the variation from old policy to new policy) --> PPO (KL clipping) --> GRPO (remove value model, baseline = average of N=64 CoT reward, then normalize) 
   ![image](https://github.com/user-attachments/assets/8937cbbb-a9b1-4949-afd9-3fc2135a298e)       
   PPO vs GRPo
   ![image](https://github.com/user-attachments/assets/0851cd4e-4f6e-47af-b7c9-be867e73ed00)
  - Using the Math values for reward model 

