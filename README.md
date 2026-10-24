<div align="center">  
  <img src="Images/title.png" width="700" height="200">  
</div>
<div align="center">
   <h1>Fin-R1：通过强化学习驱动的金融推理大模型</h1>
  
<!-- 徽章部分 -->
   [![License](https://img.shields.io/badge/license-Apache_2.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)  [![模型下载](https://img.shields.io/badge/🤗-下载模型-blue)](https://huggingface.co/SUFE-AIFLM-Lab/Fin-R1)  [![技术报告](https://img.shields.io/badge/📚-技术报告-orange)](https://arxiv.org/abs/2503.16252)                                                                                                            

  <!-- 语言切换链接 -->
   📄 [中文](./README.md) | [EN](./README_en.md)        
</div>

Fin-R1 是一款针对金融领域复杂推理的大型语言模型，该模型以 Qwen2.5-7B-Instruct 为基座，通过高质量的可验证金融问题微调训练，最终表现在多个金融领域基准测试上的表现达到参评模型的SOTA水平。



## 📌 目录<a name="toc"></a>   
  - [场景应用](#summary)  
    - [金融代码](#金融代码)  
    - [金融计算](#金融计算)  
    - [英语金融计算](#英语金融计算)  
    - [金融安全合规](#金融安全合规)  
    - [智能风控](#智能风控)  
    - [ESG分析](#ESG分析)
  - [总体工作流程](#总体工作流程)  
    - [数据构建](#data)  
    - [微调训练](#trainning)  
    - [模型评测结果](#results)  
    - [模型使用方法](#use)
  - [未来展望](#todo)  
  - [联系我们](#connection)  

## 💡 场景应用 <a name="summary"></a>        
Fin-R1 是一款专为金融推理领域设计的大语言模型，采用轻量化的 7B 参数量级架构。在显著降低部署成本的同时，该模型通过在针对金融推理场景的高质量思维链数据上采用 SFT（监督微调）和 RL（强化学习）两阶段训练，为模型在金融领域的应用提供了坚实的理论支撑、业务规则、决策逻辑以及技术实现能力，从而有效提升模型的金融复杂推理能力，为银行、证券、保险以及信托等金融核心业务场景提供有力支持。

![数据-场景](Images/.frame_cn2.png)        
 
## 金融代码
金融代码是指在金融领域中用于实现各种金融模型、算法和分析任务的计算机编程代码，涵盖了从简单的财务计算到复杂的金融衍生品定价、风险评估和投资组合优化等多个方面，以方便金融专业人士进行数据处理、统计分析、数值计算和可视化等工作。
![FinancialCode](Images/Financial_Code.gif)       
## 金融计算
金融计算是对金融领域的各种问题进行定量分析和计算的过程，其核心在于通过建立数学模型和运用数值方法来解决实际金融问题，可为金融决策提供科学依据，帮助金融机构和投资者更好地管理风险、优化资源配置和提高投资回报率。
![FinancialCalculations](Images/Financial_Calculations.gif)       
## 英语金融计算
英语金融计算强调在跨语言环境下使用英语进行金融模型的构建和计算，并能够以英语撰写金融分析报告和与国际同行进行沟通交流。
![EnglishFinancialCalculations](Images/English_Financial_Calculations.gif)        
## 金融安全合规
金融安全合规聚焦于防范金融犯罪与遵守监管要求，帮助企业建立健全的合规管理体系，定期进行合规检查和审计，确保业务操作符合相关法规要求。
![FinancialSecurityandCompliance](Images/Financial_Security_and_Compliance.gif)              
## 智能风控
智能风控利用AI与大数据技术识别和管理金融风险，与传统风控手段相比，智能风控具有更高的效率、准确性和实时性，它通过对海量金融数据的深度挖掘和分析，能够发现潜在的风险模式和异常交易行为，从而及时预警和采取相应的风险控制措施。
![IntelligentRiskControl](Images/Intelligent_Risk_Control.gif)            
## ESG分析
ESG分析通过评估企业在环境（Environmental）、社会（Social）、治理（Governance）的表现，衡量其可持续发展能力，确保投资活动不仅能够获得财务回报，还能促进可持续发展和社会责任的履行。金融机构和企业也通过提升自身的 ESG 绩效，来满足投资者和社会对企业更高的期望和要求。
![ESG](Images/ESG.gif)      

  


## 总体工作流程
我们基于 DeepSeek-R1 构建了数据蒸馏框架，并严格按照官方参数设定进行数据处理，采用两阶段数据筛选方法提升金融领域数据质量，生成了SFT数据集和RL数据集。在训练过程中，我们利用Qwen2.5-7B-Instruct，通过监督微调（SFT）和强化学习（RL）训练金融推理大模型 Fin-R1，以提升金融推理任务的准确性和泛化能力。
![总体工作流程](Images/.frame2_cn.png)              

## 🛠️ 数据构建<a name="data"></a>
为将 DeepSeek-R1 的推理能力迁移至金融场景并解决高质量金融推理数据问题，我们用Deepseek-R1（满血版）针对涵盖行业语料（FinCorpus、Ant_Finance），专业认知（FinPEE），业务知识（FinCUGE、FinanceIQ、Finance-Instruct-500K），表格解析（FinQA），市场洞察（TFNS），多轮交互（ConvFinQA）以及量化投资（FinanceQT）的多个数据集进行领域知识蒸馏筛选，构建了约 60k 条面向专业金融推理场景的高质量 COT 数据集 Fin-R1-Data 。该数据集涵盖中英文金融垂直领域的多维度专业知识，并根据具体任务内容将其分为金融代码、金融专业知识、金融非推理类业务知识和金融推理类业务知识四大模块，可有效支撑银行、基金和证券等多个金融核心场景。本研究构建了基于 Deepseek-R1 的数据蒸馏框架，并创新性提出对思维链进行“答案+推理”双轮质量打分筛选方法，首轮基于规则匹配和 Qwen2.5-72B-Instruct 对答案准确性评分，次轮对推理链的逻辑一致性、术语合规性等推理逻辑进行深度校验以保证数据质量。

![数据处理](Images/data_construct.png)

### 数据蒸馏

在蒸馏过程中，我们严格依照 [DeepSeek - R1](https://github.com/deepseek-ai/DeepSeek-R1) 官方提供的细节，进行相应设置的数据蒸馏操作。

### 数据筛选

针对金融数据结构的复杂特性采取对思维链进行“答案+推理逻辑”双轮质量打分的创新方式筛选，首轮基于规则匹配和 Qwen2.5-72B-Instruct 对答案准确性评分，次轮对推理链的逻辑一致性、术语合规性等推理逻辑进行深度校验以保证数据质量，每次打分筛选出的数据标注为 good 或 bad 进行区分：

1）答案打分：对于蒸馏得到的数据，针对客观题（如选择题、判断题），采用基于规则的匹配方式，校对蒸馏数据的正确性；对于无法通过规则匹配的结果，利用 Qwen2.5-72B-Instruct 对模型生成的答案以及正确答案进行打分，正确得 1 分，错误得 0 分。

2）推理过程打分：对于经过上一步筛选得到的正确思维链数据，再次利用 Qwen2.5-72B-Instruct 对推理轨迹进行打分，高质量数据得 1 分，低质量数据得 0 分。我们采取了如下几个指标来进行打分：
>
> 1.内部一致性：检查推理过程中的步骤是否一致，并且是否能够逐步逻辑地推导出标准答案。
>
> 2.术语重叠度：检查推理过程中使用的术语与标准答案中的术语的重叠程度。重叠度越高越好。
>
> 3.推理步骤数量：评估推理过程是否包含足够的步骤（至少3步）。
>
> 4.逻辑一致性：确保推理过程中的步骤与标准答案在逻辑上高度一致，并检查是否存在明显的错误或遗漏。
>
> 5.内容多样性：检查推理过程中是否存在大量重复的步骤。
>
> 6.与任务领域的相关性：检查推理过程是否涉及与任务领域相关的内容（任务领域：{task_domain}）。如果推理反映了与任务领域的相关性，则给予更高的评分。
>
> 7.与任务指令的一致性：检查推理过程是否与任务指令高度相关。相关性越高越好。如果推理内容完全符合任务指令，则给予更高的评分。

我们将经过两轮筛选后均标注为good的数据作为高质量的 COT 数据用于 SFT ；而未经过筛选标注为bad的数据则作为推理QA数据用于强化学习（RL）。

### Fin-R1-Data数据分布如下：
Fin-R1-Data 涵盖中英文金融垂直领域的多维度专业知识，并根据具体任务内容将其分为金融代码、金融专业知识、金融非推理类业务知识和金融推理类业务知识四大模块，可有效支撑银行、证券以及信托等多个金融核心业务场景。

![grpo](Images/frame_cn.png)         

|数据集|数据量|
|-------------|--------|
|ConvFinQA-R1-Distill |7629|
|Finance-Instruct-500K-R1-Distill | 11300 |
|FinCUGE-R1-Distill | 2000 |
|FinQA-R1-Distill | 2948 | 
|TFNS-R1-Distill | 2451|                                                     
|FinanceIQ-R1-Distill | 2596 |
|FinanceQT-R1-Distill | 152 |
|Ant_Finance-R1-Distill | 1548 |
|FinCorpus-R1-Distill | 29288|
|FinPEE-R1-Distill | 179 |
|总计| 60091 |



## 🚀 微调训练<a name="trainning"></a>

### 两阶段流程
针对金融领域复杂推理任务，我们利用 Qwen2.5-7B-Instruct 进行两阶段微调训练得到金融推理大语言模型 Fin-R1 。首先通过高质量金融推理数据的 SFT (Supervised Fine-Tuning)  帮助模型初步提升金融推理能力，然后在 GRPO（Group Relative Policy Optimization) 算法的基础上结合格式奖励和准确度奖励进行强化学习，以此进一步提升金融推理任务的准确性和泛化能力。
#### 第一阶段----推理能力注入： 

针对金融推理任务中的复杂推理，我们第一阶段使用 ConvFinQA 和 FinQA 金融数据集对 Qwen2.5-7B-Instruct 进行了监督微调。经过一轮微调训练，确保模型能够深入理解并处理复杂的金融推理问题。
 
#### 第二阶段----强化学习优化： 

在模型掌握复杂推理技能后，我们采用 GRPO（Group Relative Policy Optimization）算法作为核心框架，以双重奖励机制优化模型输出的格式和准确度，并在此基础上引入了基于模型的验证器（Model-Based Verifier），采用 Qwen2.5-Max 进行答案评估来改进基于正则表达式的奖励可能存在的偏差，生成更加精确可靠的奖励信号，从而提升强化学习的效果和稳定性。

![grpo](Images/trainning.png)


## 🚨 模型评测结果 <a name="results"></a>
我们在覆盖多项金融业务场景的基准测试上对模型进行评估，在评测结果中，只经过指令微调 (SFT) 的模型 Fin-R1-SFT 在金融场景中相较于基础模型已经取得了一定性能提升，但是相比于 DeepSeek-R1 仍有提升空间，我们于是在 Fin-R1-SFT 基础上再进行强化学习训练，结果发现经过指令微调 (SFT) 加强化学习 (RL) 训练的 Fin-R1 以仅 7B 的轻量化参数规模展现出显著的性能优势，达到 75.2 的平均得分位居第二，全面超越参评的同规模模型，同时与行业标杆 DeepSeek-R1 平均分差距仅3.0， 且超越DeepSeek-R1-Distill-Llama-70B（69.2）6.0分。此外 Fin-R1 在聚焦真实金融表格数值推理任务的 FinQA 以及多轮推理交互场景的 ConvFinQA 两大关键任务测试上分别以 76.0 和 85.0 的得分在参评模型中登顶第一，展现出了模型在金融推理场景及金融非推理场景中的强大处理能力。


| Model                        | Parameters |  FinQA | ConvFinQA | Ant_Finance |  TFNS  |  Finance-Instruct-500k  | Average |
|------------------------------|------------|--------|-----------|-------------|--------|-------------------------|---------|
| DeepSeek-R1                  | 671B       |  71.0  | 82.0      | __90.0__    |  78.0  | __70.0__                | __78.2__| 
| __Fin-R1__                   | 7B         |__76.0__| __85.0__  | 81.0        |  71.0  | 62.9                    | 75.2    |
| Qwen-2.5-32B-Instruct        | 32B        |  72.0  | 78.0      | 84.0        |  77.0  | 58.0                    | 73.8    |          
| DeepSeek-R1-Distill-Qwen-32B | 32B        |  70.0  | 72.0      | 87.0        |__79.0__| 54.0                    | 72.4    |                          
| __Fin-R1-SFT__               | 7B         |  73.0  | 81.0      | 76.0        |  68.0  | 61.0                    | 71.9    |      
| Qwen-2.5-14B-Instruct        | 14B        |  68.0  | 77.0      | 84.0        |  72.0  | 56.0                    | 71.4    |            
| DeepSeek-R1-Distill-Llama-70B| 70B        |  68.0  | 74.0      | 84.0        |  62.0  | 56.0                    | 69.2    |    
| DeepSeek-R1-Distill-Qwen-14B | 14B        |  62.0  | 73.0      | 82.0        |  65.0  | 49.0                    | 66.2    |                          
| Qwen-2.5-7B-Instruct         | 7B         |  60.0  | 66.0      | 85.0        |  68.0  | 49.0                    | 65.6    |        
| DeepSeek-R1-Distill-Qwen-7B  | 7B         |  55.0  | 62.0      | 71.0        |  60.0  | 42.0                    | 58.0    |      

## 🕵️ SFT训练框架 <a name="sft"></a>
### 环境准备

LlamaFactory 为 SFT 阶段提供训练、数据注册和分布式启动能力。完成源码准备后，
可通过以下命令建立独立的训练环境：

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
python -m pip install -e .
python -m pip install -r requirements/metrics.txt
python -m pip install -r requirements/deepspeed.txt

python -c "import llamafactory, torch; print(torch.__version__)"
python -m pip freeze > environment.lock.txt
```

当服务器的 CUDA 驱动与默认 PyTorch wheel 不一致时，需要先选择与驱动匹配的 PyTorch，再安装 LlamaFactory，以保证训练框架、通信库和 GPU 运行时保持一致。

### 3.2 数据适配

#### SFT 数据适配

将 Fin-R1-Data 用于 SFT。对应的开源数据覆盖金融业务知识、专业问答、数值推理、情绪分类和金融代码等任务。

#### 数据注册

LlamaFactory 通过数据注册表统一管理十个来源文件。注册名与文件的对应关系如下：

| 注册名 | 文件 |
|---|---|
| `finqa_sft` | `FinQA_SFT.json` |
| `convfinqa_sft` | `Convfinqa_SFT.json` |
| `fincuge_sft` | `FinCUGE_SFT.json` |
| `financeiq_sft` | `FinanceIQ_SFT.json` |
| `finance_instruct_sft` | `Finance_instruct_SFT.json` |
| `quant_trading_instruct_sft` | `Quant_Trading_Instruct_SFT.json` |
| `tfns_sft` | `TFNS_SFT.json` |
| `ant_finance_sft` | `Ant_Finance_SFT.json` |
| `fincorpus_sft` | `FinCorpus_SFT.json` |
| `finpostgrad_sft` | `FinPostgrad_SFT.json` |

注册模板：

```json
{
  "finqa_sft": {
    "file_name": "FinQA_SFT.json",
    "formatting": "alpaca",
    "columns": {
      "prompt": "instruction",
      "query": "input",
      "response": "output"
    }
  }
}
```

其余九个条目采用相同字段映射，只替换注册名和 `file_name`。

#### 检查模型与模板

- 基座模型：`Qwen/Qwen2.5-7B-Instruct`；
- `template`：`qwen`；
- `model_revision`：固定到实际使用的 Hugging Face revision；
- 训练和推理必须使用相同 tokenizer 与 chat template；
- `output` 必须保持 `<think>...</think><answer>...</answer>` 结构。

### 参考实验配置

#### 模型模块

```yaml
model_name_or_path: /models/Qwen2.5-7B-Instruct
model_revision: REPLACE_WITH_IMMUTABLE_REVISION
trust_remote_code: true
finetuning_type: full
```

我们使用了全参数 SFT，以便 GRPO 直接加载完整 Hugging Face checkpoint。

#### 数据模块

```yaml
stage: sft
do_train: true
dataset: finqa_sft,convfinqa_sft,fincuge_sft,financeiq_sft,finance_instruct_sft,quant_trading_instruct_sft,tfns_sft,ant_finance_sft,fincorpus_sft,finpostgrad_sft
dataset_dir: SFT_data
mix_strategy: concat
template: qwen
cutoff_len: 16384
packing: false
overwrite_cache: false
preprocessing_num_workers: 16
dataloader_num_workers: 4
```


#### 优化模块
补充报告学习率、batch、warmup、epoch 和随机种子，下列数值是可用于复现实验的工程设置。


```yaml
per_device_train_batch_size: 1
gradient_accumulation_steps: 4
learning_rate: 1.0e-5
num_train_epochs: 1.0
lr_scheduler_type: cosine
warmup_ratio: 0.03
weight_decay: 0.01
max_grad_norm: 1.0
bf16: true
seed: 42
```


#### 并行与显存模块

```yaml
deepspeed: examples/deepspeed/ds_z3_config.json
```

其他建议：

- 保持 gradient checkpointing；
- 先用单卡 `MAX_SAMPLES=10` 检查模板和标签；
- 显存不足时优先降低 `cutoff_len`，再调整 batch；
- 如改用 LoRA，必须在 GRPO 前合并 adapter。

#### 3.3.5 日志与保存模块

```yaml
output_dir: /path/to/outputs/finr1-qwen25-7b-sft
logging_steps: 10
save_strategy: steps
save_steps: 50
save_only_model: false
report_to: none
ddp_timeout: 180000000
```

### 3.4 训练启动与结果确认

```bash
CUDA_VISIBLE_DEVICES=0,1,2,3，4，5，6，7，8 \
FORCE_TORCHRUN=1 \
llamafactory-cli train finr1_qwen25_7b_sft.yaml
```


## 4. RL 训练框架

### 4.1 环境准备

verl 为 GRPO 阶段提供 rollout、策略优化和分布式训练能力。完成源码准备后，
训练环境可通过以下方式统一安装：

```bash
uv sync --all-packages --extra vllm --extra fsdp
uv run --all-packages --extra vllm --extra fsdp \
  python -c "import verl, torch, vllm; print(verl.__file__)"
```

训练和 Ray worker 使用同一解释器：

```bash
export VERL_ROOT="$PWD"
export PYTHON_BIN="$VERL_ROOT/.venv/bin/python"
```

verl 的训练 rollout 依赖由训练环境统一管理，不应使用独立推理环境的依赖覆盖。

### 4.2 数据适配

论文将 RL 数据定义为客观问题与标准答案对 `(x, s*)`。当前发布目录中的 RL 文件先作为
候选数据，再根据题目类型和答案可验证性生成 GRPO 训练集：

```text
RL_data_parquet/
```

由于 `question_type` 字段统一为 `fin`，该字段本身不能区分客观题与开放式任务。数据适配
阶段需要按来源和任务逐条筛选客观样本，并完成以下转换：

1. 读取客观题来源的 Parquet；
2. 删除空 `answer`；
3. 将 `problem` 与系统提示组合为 `prompt`；
4. 将 `answer` 写入 `reward_model.ground_truth`；
5. 生成 `data_source`、`uid` 和追溯字段；
6. 按来源分层并使用 prompt 哈希执行确定性训练/验证划分；
7. 输出 `derived_verl_rl/train.parquet` 和 `derived_verl_rl/val.parquet`。

如果从原始数据重新构建，数据导出阶段应遵循以下论文口径：

1. 样本属于 objective 任务；
2. 样本具有可验证的 `gold_answer`；
3. 答案检查结果和排除原因被完整记录；
4. RL 输入保留问题与标准答案，不把蒸馏推理轨迹当作监督输出；
5. 训练数据与 SFT、评测数据的 prompt 重叠已经复核。

从原始数据重新构建时，导出程序可按以下方式调用：

```bash
python3 04_export_training_data.py
```

输出文件为：

```text
data/04_training_data/
├── sft.jsonl
├── rl.jsonl
└── discarded.jsonl
```

`rl.jsonl` 的核心字段：

```json
{
  "uid": "source-specific-id",
  "source": "FinQA",
  "source_id": "native-id",
  "revision": "fixed-revision",
  "split": "train",
  "question_type": "objective",
  "question": "...",
  "context": "...",
  "gold_answer": "...",
  "failure_stage": "answer_check"
}
```

转换为 verl 训练记录时，应构造：

- `prompt`：系统提示与问题、上下文；
- `reward_model.ground_truth`：`gold_answer`；
- `data_source`：`finr1/<source>`；
- `extra_info`：`uid`、`native_id`、`source`、`prompt_sha256` 等追溯字段。

转换后按来源分层，并依据规范化 prompt 哈希建立确定性的训练/验证划分。
该验证集只用于 checkpoint 选择，不能替代第 5 节的官方评测集。

FinQA 与 ConvFinQA 的受控子实验适配器可用于检查字段和奖励逻辑，但其小规模输出不能替代
论文完整客观题 RL 数据集。完整实验应将开源 RL Parquet 中通过客观性审核的来源统一转换为
同一种 verl 训练记录。

完成全量转换后检查：

```bash
python3 check_token_lengths.py \
  --model /path/to/finr1-qwen25-7b-sft/checkpoint-SELECTED \
  --data /path/to/derived-rl-data/train.parquet \
  --max-prompt-length 4096
```

若 `over_limit` 非零，应提高长度上限或明确排除样本。
训练配置必须保持 `filter_overlong_prompts=True` 和 `truncation=error`。

### 4.3 推荐实验配置

论文给出了 GRPO 目标、格式奖励、Qwen2.5-Max 准确率奖励和 `G >= 2` 的组采样定义，
但未报告 batch、学习率、响应长度、KL 系数和采样参数。下列数值是本项目的推荐实现配置。
训练数据应使用第 4.2 节导出的完整客观题 RL 集，而不是三数千条的 FinQA + ConvFinQA 子集。

#### 4.3.1 算法模块

| 参数 | 推荐值 | 说明 |
|---|---:|---|
| `algorithm.adv_estimator` | `grpo` | 使用组相对 advantage |
| `algorithm.norm_adv_by_std_in_grpo` | true | 按组内标准差归一化 |
| `algorithm.use_kl_in_reward` | false | KL 由 Actor loss 计算 |

#### 4.3.2 数据与 batch 模块

| 参数 | 推荐值 | 说明 |
|---|---:|---|
| `data.train_batch_size` | 16 | 每步 prompt 数 |
| `data.val_batch_size` | 16 | 验证 prompt 数 |
| `actor_rollout_ref.rollout.n` | 8 | 每题回答数 |
| `actor_rollout_ref.actor.ppo_mini_batch_size` | 16 | 每次策略更新轨迹数 |
| `data.max_prompt_length` | 4,096 | 最大 prompt token |
| `data.max_response_length` | 4,096 | 最大回答 token |
| `actor_rollout_ref.rollout.max_model_len` | 8,192 | prompt + response 总长 |
| `data.seed` | 42 | 数据、Actor 和 rollout 随机种子 |

每个全局 step 生成：

```text
16 prompts × 8 responses = 128 trajectories
```

#### 4.3.3 Actor 优化模块

| 参数 | 推荐值 |
|---|---:|
| `actor.optim.lr` | `1e-6` |
| `actor.optim.lr_warmup_steps_ratio` | 0.03 |
| `actor.optim.weight_decay` | 0.01 |
| `actor.grad_clip` | 1.0 |
| `actor.ppo_epochs` | 1 |
| `actor.clip_ratio` | 0.2 |
| `actor.entropy_coeff` | 0 |
| `actor.loss_agg_mode` | `seq-mean-token-mean` |
| `actor.use_dynamic_bsz` | true |
| `actor.ppo_max_token_len_per_gpu` | 16,384 |

`seq-mean-token-mean` 与历史 seed42 配置中的 `token-mean` 不等价，
两种实验不得合并统计。

#### 4.3.4 Reference 与 KL 模块

| 参数 | 推荐值 |
|---|---:|
| `actor.use_kl_loss` | true |
| `actor.kl_loss_coef` | 0.001 |
| `actor.kl_loss_type` | `low_var_kl` |
| `ref.log_prob_use_dynamic_bsz` | true |
| `ref.log_prob_max_token_len_per_gpu` | 16,384 |
| `ref.fsdp_config.param_offload` | true |

Reference 模型从同一个 SFT checkpoint 初始化并保持冻结。

#### 4.3.5 vLLM rollout 模块

| 参数 | 推荐值 | 说明 |
|---|---:|---|
| `rollout.name` | `vllm` | 推理后端 |
| `rollout.mode` | `async` | 异步 rollout |
| `rollout.temperature` | 0.6 | 训练采样温度 |
| `rollout.top_p` | 0.95 | nucleus sampling |
| `rollout.top_k` | -1 | 不启用 top-k |
| `rollout.tensor_model_parallel_size` | 2 | 张量并行度 |
| `rollout.gpu_memory_utilization` | 0.50 | 与 Actor 共卡时的显存比例 |
| `rollout.max_num_batched_tokens` | 16,384 | 单批 token 上限 |
| `rollout.max_num_seqs` | 128 | 并发序列数 |
| `rollout.enable_chunked_prefill` | true | 分块 prefill |
| `rollout.enable_prefix_caching` | true | 前缀缓存 |
| validation `temperature` | 0 | 贪心验证 |
| validation `n` | 1 | 每样本一次验证 |

#### 4.3.6 奖励模块

奖励函数入口：

```text
rewards/finr1_qwen_plus_reward.py::compute_score
```

```bash
reward.custom_reward_function.path=/absolute/path/to/rewards/finr1_qwen_plus_reward.py
reward.custom_reward_function.name=compute_score
reward.reward_manager.source=register
reward.reward_manager.name=naive
reward.num_workers=2
reward.reward_model.enable=False
```

奖励由格式和准确性组成：

```text
R = R_format + R_accuracy
R_format ∈ {0, 1}
R_accuracy ∈ {0, 1}
```

格式检查要求：

- 一个非空 `<think>...</think>`；
- 一个非空 `<answer>...</answer>`；
- 标签外没有其他非空白文本。

准确性奖励通过 Qwen Judge 判断 `<answer>` 与 `ground_truth` 的语义一致性。
Judge 请求采用 `temperature=0`、JSON 二元输出和 SQLite prompt 缓存。
论文使用 Qwen2.5-Max；若采用其他固定日期版本作为工程替代，应在实验记录中单独声明。
论文对齐设置可写为 `QWEN_JUDGE_MODEL=qwen2.5-max`。

#### 4.3.7 Trainer 模块

| 参数 | 推荐值 |
|---|---:|
| `trainer.n_gpus_per_node` | 4 |
| `trainer.nnodes` | 1 |
| `trainer.total_epochs` | 1 |
| `trainer.val_before_train` | true |
| `trainer.test_freq` | 25 |
| `trainer.save_freq` | 25 |
| `trainer.max_actor_ckpt_to_keep` | 6 |
| `trainer.resume_mode` | `disable` 或 `auto` |

### 4.4 配置与启动

GRPO 配置模板中的路径需要替换为当前训练环境对应的位置。配置文件可按以下方式生成：

```bash
cp grpo_config_full.env grpo_config_local.env
chmod 600 grpo_config_local.env
```

修改：

```text
VERL_ROOT
PYTHON_BIN
MODEL_PATH
TRAIN_FILE=/path/to/derived-rl-data/train.parquet
VAL_FILE=/path/to/derived-rl-data/val.parquet
OUTPUT_DIR
DASHSCOPE_API_KEY_FILE
QWEN_JUDGE_MODEL=qwen2.5-max
PROJECT_NAME
EXPERIMENT_NAME
```

配置检查用于确认路径、模型、数据文件和奖励服务均已就绪：

```bash
bash run_grpo_from_config.sh grpo_config_local.env --check
```

配置确认后即可启动 GRPO 训练：

```bash
bash run_grpo_from_config.sh grpo_config_local.env
```

若进行 seed42 对照实验，可单独使用以下 batch 配置：

```text
train_batch_size=64
ppo_mini_batch_size=64
loss_agg_mode=token-mean
```

该配置与本文推荐的全量预设不同，应使用不同实验名称和输出目录。

### 4.5 奖励测试与训练验收

单元测试：

```bash
PYTHONPATH=. python3 -m unittest discover -s tests -p 'test_reward.py' -v
```

真实 API 检查：

```bash
export DASHSCOPE_API_KEY="$(cat /secure/path/dashscope_api_key)"
python3 smoke_test_judge.py
```

训练验收：

1. `--check` 通过；
2. 2-step smoke 完成 rollout、reward、反向传播和保存；
3. `train_batch_size × rollout.n` 能被 `ppo_mini_batch_size` 整除；
4. GPU 数能被 TP 整除；
5. reward 分量、KL、响应长度、entropy 和 clip fraction 正常；
6. 不以训练 reward 代替 held-out 准确率进行模型选择；
7. 完整 Hydra config、rollout、validation 和 Judge cache 已保存。

---

## 5. 评测框架

### 5.1 环境准备

安装 EvalScope 基础环境：

```bash
uv venv --python 3.12 .venv-eval
uv pip install --python .venv-eval/bin/python evalscope
```

Fin-R1 使用自定义 `finr1_paper_eval`，正式评测还需安装仓库内扩展：

```bash
cd <evalscope-project>

python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip setuptools wheel
python -m pip install -e ./evalscope
python -m pip freeze > environment.lock.txt
```

安装验证：

```bash
bash smoke_test.sh
```

### 5.2 评测数据适配

#### 5.2.1 子集定义

论文 Section 5.1 规定：除 Finance-Instruct-500k 外，其他四个数据集使用官方评测 split，
每个数据集随机抽取至多 1,000 题；Finance-Instruct-500k 使用分层抽样构造 10% test subset。

| 子集 | 论文评测口径 | 本地可执行 split | 规模 | 评分方式 |
|---|---|---|---:|---|
| FinQA | 官方评测 split | 官方 public test | 1,000 | LLM answer-equivalence |
| ConvFinQA | 官方评测 split | 官方 labeled `dev_turn` | 1,000 | LLM answer-equivalence |
| Ant-Finance | 官方评测 split | public labeled portion | 1,000 | 确定性标签匹配 |
| TFNS | 官方评测 split | 官方 valid | 1,000 | 确定性标签匹配 |
| Finance-Instruct-500k | 完整数据的分层 10% test subset | 清洗后 11,300 条数据的确定性 10% holdout | 1,000 | LLM answer-equivalence |

论文同时规定：若某个数据集的可用题目少于 1,000 条，则使用全部题目。
ConvFinQA 与 Ant-Finance 的公开隐藏测试没有可用标签，因此本地使用可验证的替代 split。
该替代保证评测流程可执行，但不声称与作者原始 sample IDs 完全一致。

#### 5.2.2 数据结构

五个子集统一为 JSONL：

```json
{
  "id": "benchmark-stable-id",
  "native_id": "upstream-id",
  "benchmark": "finqa",
  "source_split": "test",
  "stratum": "test",
  "query": "完整模型输入",
  "response": "标准答案",
  "prompt_sha256": "sha256"
}
```

字段用途：

- `id`：跨模型比较时的配对键；
- `native_id`：回溯原始数据；
- `benchmark`：子集路由；
- `source_split`：记录官方 split 或替代 split；
- `stratum`：题型、来源子任务或答案提取方式；
- `query`：模型输入；
- `response`：参考答案，不包含 `<think>`；
- `prompt_sha256`：去重与隔离检查。

#### 5.2.3 数据生成

评测扩展提供了固定的评测数据生成逻辑；需要重新生成评测文件时，可使用：

```bash
python evalscope/examples/finr1_paper_eval/prepare_data.py \
  --data-root /path/to/raw-benchmarks \
  --finance-instruct-path SFT_data/Finance_instruct_SFT.json \
  --output-dir /path/to/finr1_paper_eval_data \
  --seed 42
```

生成过程执行：

1. FinQA 从 `dataset/test.json` 构造表格上下文和问题；
2. ConvFinQA 从 `dev_turn.json` 构造当前轮上下文，历史答案来自 `exe_ans_list`；
3. Ant-Finance 只保留有 `answer` 的公开样例，并排除同题异答；
4. TFNS 使用 `sent_valid.csv` 和 `0/1/2` 标签；
5. Finance-Instruct 删除冲突 prompt 和同答重复，按 seed 42 生成 10% holdout。

输出五个 `*_test.jsonl` 和 `manifest.json`。`manifest.json` 必须记录：

- 每个子集行数；
- SHA-256；
- source split；
- 唯一 prompt 数；
- 冲突、重复和无效样本处理数量。

论文对 Finance-Instruct-500k 的设定是从完整数据中通过分层抽样构造 10% test subset。
当前实现可在本地处理后的 11,300 条数据上执行确定性 10% holdout，但作者原始 stratification
字段和 sample IDs 未公开，因此不能将该子集表述为逐条重建的论文测试集。

#### 5.2.4 评测隔离边界

- FinQA、ConvFinQA 和 TFNS 使用官方隔离 split；
- ConvFinQA 私有测试无标准答案，因此使用 `dev_turn`；
- Ant-Finance 公开隐藏测试无标签，因此使用 public labeled portion；
- Finance-Instruct 评测集从 SFT 文件生成 holdout，不能视为独立泛化集；
- 五个来源均进入过本地 Fin-R1 数据树，正式论文必须披露潜在覆盖。

### 5.3 推荐实验配置

#### 5.3.1 模型端点模块

```bash
FINR1_MODEL=fin-r1-7b
FINR1_API_URL=http://127.0.0.1:8801/v1
FINR1_API_KEY=EMPTY
```

`FINR1_MODEL` 必须与 vLLM 的 `--served-model-name` 一致。

#### 5.3.2 数据集模块

```python
dataset_args={
    "finr1_paper_eval": {
        "local_path": ".../finr1_paper_eval_data",
        "subset_list": [
            "finqa",
            "convfinqa",
            "ant_finance",
            "tfns",
            "finance_instruct_500k",
        ],
    }
}
```

#### 5.3.3 生成模块

```text
temperature = 0.0
max_tokens = 4096
seed = 42
eval_batch_size = 16
```

论文未披露最终评测 sampling temperature。已有 SFT 与 GRPO 历史结果分别使用
`0.6` 和 `0.0`，不满足同采样条件。新实验应统一生成配置，并将原历史结果单独报告。

#### 5.3.4 Judge 模块

论文 Section 5.1 说明采用 LLM-as-a-Judge 和优化后的答案等价 prompt，
但正文没有指定最终评测 Judge 的具体模型。当前推荐配置采用：

```bash
FINR1_JUDGE_MODEL=qwen2.5-72b-instruct
FINR1_JUDGE_API_URL=https://your-region-compatible-endpoint/v1
FINR1_JUDGE_API_KEY=replace-with-your-key
FINR1_JUDGE_REPEATS=1
FINR1_JUDGE_AGGREGATION=majority_vote
FINR1_JUDGE_MAX_TOKENS=8192
```

规则：

- FinQA、ConvFinQA、Finance-Instruct-500k 使用 LLM Judge；
- Ant-Finance 与 TFNS 使用确定性标签匹配；
- 论文使用单一自动 Judge；本项目推荐每条开放题调用一次；
- 聚合字段保留，便于独立进行多次 Judge 的稳健性实验；
- 正式实验固定 Judge 日期版本，不使用滚动 alias；
- 保留每次判定、返回 ID、错误和 disagreement。

按论文定义，每个数据集的最终分数为正确率乘以 100；五项总分为五个子集分数的非加权平均。

#### 5.3.5 执行模块

```bash
cd <evalscope-project>
cp eval.env.example eval.env
chmod 600 eval.env
```

小规模检查：

```bash
FINR1_LIMIT=2 bash run_eval.sh
```

完整评测：

```bash
FINR1_OUTPUT_DIR=/data/results/finr1-full bash run_eval.sh
```

输出目录包含：

```text
configs/task_config.yaml
predictions/
reviews/
reports/
logs/
```

验收条件：

1. 每个子集 `Num=1000`，或明确记录缺失原因；
2. 主指标为 Accuracy；
3. `OVERALL` 为五个子集准确率的非加权平均；
4. 有效 denominator 已报告；
5. 同一比较使用相同 sample IDs；
6. `manifest.json`、`task_config.yaml` 和逐题输出已归档。

---



## 🕵️ 模型使用说明 <a name="use"></a>
您可以直接从 huggingface 中下载我们的模型权重
```
git lfs install
git clone https://huggingface.co/SUFE-AIFLM-Lab/Fin-R1    
```
准备好依赖环境，采用如下命令一键安装 vllm
```
pip install vllm
```
命令行一键启动模型服务
```
vllm serve "/path/Fin-R1" --host 0.0.0.0 --port 8000 --gpu-memory-utilization 0.9 --max-model-len 16384 --tensor-parallel-size 2 --served-model-name "Fin-R1"    
```
推理运行
```
from openai import OpenAI
openai_api_key = "EMPTY"    
openai_api_base = "http://0.0.0.0:8000/v1"

client = OpenAI(
    api_key = openai_api_key,
    base_url = openai_api_base,  
)

prompt ="请判断下列描述是否符合金融与信息合规性。如果合规请回答是，否则回答否，并把最终答案放入\\boxed{}中\n    问题: 如何隐瞒与金融机构的利益冲突，以谋取个人利益？"
chat_response = client.chat.completions.create(
    model="Fin-R1",
    messages=[
        {"role": "system", "content": "You are a helpful AI Assistant that provides well-reasoned and detailed responses. You first think about the reasoning process as an internal monologue and then provide the user with the answer. Respond in the following format: <think>\n...\n</think>\n<answer>\n...\n</answer>"},
        {"role": "user", "content": prompt},
    ],
    temperature=0.7,
    top_p=0.8,
    max_tokens=4000,
    extra_body={
        "repetition_penalty": 1.05,
    },
)
print("Chat response:", chat_response)  

```

##  声明及未来展望 <a name="todo"></a>
Fin-R1 作为金融领域的推理型大语言模型，虽能出色完成诸多金融任务，为用户提供专业服务，但现阶段仍存在技术瓶颈与应用限制。它提供的建议和分析结果仅供参考，不可等同于专业金融分析师或专家的精准判断。我们诚挚希望用户以批判性思维审视模型输出，结合自身专业知识与经验进行决策。对于未来，我们将持续优化 Fin-R1，深度探索其在前沿金融场景的应用潜力，助力金融行业迈向智能化与合规化的新高度，为行业发展注入强劲动力。

