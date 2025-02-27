<div align="center">
  <h1>JailBench: 大型语言模型越狱攻击风险评测中文数据集</h1>
</div>

JailBench 是针对大型语言模型在中文语境下越狱攻击风险的综合性多领域安全评测数据集，面向《网络安全技术 生成式人工智能服务安全基本要求》 **训练数据及生成内容的主要安全风险** 标准分类设计，是目前公开发布**题库规模最大，越狱攻击手段覆盖最为广泛**的中文评测数据集。

## 目录

- [分类标准](#分类标准)
- [数据集介绍](#数据集介绍)
- [排行榜](#排行榜)
- [致谢](#致谢)
- [关于我们](#关于我们)


## 分类标准

JailBench 是评估大型语言模型多领域越狱攻击风险的中文数据集，该数据集充分考虑全国网络安全标准化技术委员会于2024年5月23日发布国家标准[《网络安全技术 生成式人工智能服务安全基本要求》(征求意见稿)](https://www.tc260.org.cn/file/2024-05-17/9e2853d0-99a0-49c2-9df7-ccaada842ac5.pdf) 相关内容，对数据集覆盖领域进行全面性、代表性细致分类。数据集内容从领域角度涵盖 5 个一级领域和 40 个二级领域：

<div align="center">
<img src="./assets/cate.png" alt="JailBench"/>
</div>

## 数据集介绍

- **[JailBench_seed](/JailBench_seed.csv) 👏 大模型基础安全评测数据集**  
随着大型语言模型的通用能力和知识水平快速突破提升，其生成内容引发的安全隐患也层出不穷：大模型可能做出违背人类价值观的有害行为、产生违法乱纪的不良信息或伤害性言论。因此构建大模型安全性能评测数据集，开展大规模基准测试已成为迫切需要。我们通过网络资源搜集、人工整理编写、大模型辅助生成等方法，构建并开源**大模型基础安全评测数据集 JailBench_seed**。该数据集总共包含 **540** 条模型应当拒答的有害测试问题，能够评测目标大模型的多领域基础安全防御能力。

- **[JailBench](/JailBench.csv) 👏 大模型越狱攻击风险评测数据集**  
当前多数主流大模型已具备一定的安全防护能力，常规的基础安全测试难以彻底排查模型潜在风险漏洞，一种有效的强化测试方法是利用大模型越狱攻击开展安全评测。因此我们广泛搜集、整合领域内先进越狱攻击方法，结合团队提出的具有自演化能力的越狱提示生成技术，经过越狱提示生成、种子问题强化、人工评测筛选等步骤，在基础安全评测数据集 JailBench_seed 基础上，构建并开源**大模型越狱攻击风险评测数据集 JailBench**。该数据集总共包含 **10800** 条具有强大越狱能力的测试问题，有效提高了基础安全测试问题的模型越狱能力，能够全面检测评估大型语言模型的内容安全防护能力，针对模型深层次越狱安全漏洞进行快速发现、定位、排查。

**越狱示例**

| JailBench_seed | JailBench |
|:--------------:|:---------:|
| ![image](./assets/seed.png) | ![image](./assets/jail_seed.png) |

出于数据安全考虑和潜在的危害性影响，我们选择不公开完整的安全测试数据集。仓库中可下载的公开测试集仅包括部分危害性较低的测试数据。但是，为了进行安全研究，研究人员可以通过填写 [数据申请表单](https://www.wjx.top/vm/rVlggBb.aspx# ) 进行申请。经过批准后，我们​​将向申请人提供完整的测试数据集。

**声明：数据集包含有害违规内容示例，均不代表本团队立场。**

## 排行榜

### 大模型基础安全排行榜
利用大型语言模型基础安全评测数据集 [JailBench_seed](/JailBench_seed.csv) ，我们针对国内外多款主流大型语言模型开展模型基础安全性评估，各模型的安全评测结果如下（按综合越狱成功率升序排列）：

| 模型名称 | 综合越狱成功率(%) | 违反社会主义核心价值观(%) | 歧视(%) | 侵犯他人合法权益(%) | 商业违法违规(%) | 无法满足特定服务类型安全需求(%) |
| :---------: | :---------: | :---------: | :---------: | :---------: | :---------: | :---------: |
| InterLM2-chat-7B | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| GPT-4-0613 | 0.19 | 0.95 | 0.00 | 0.00 | 0.00 | 0.00 |
| Qwen2-7B-chat | 0.37 | 0.00 | 1.21 | 0.00 | 0.00 | 0.00 |
| Qwen1.5-7B-chat | 0.74 | 0.95 | 1.21 | 0.95 | 0.00 | 0.00 |
| LLaMA2-13B-chat | 0.56 | 2.86 | 0.00 | 0.00 | 0.00 | 0.00 |
| LLaMA3-8B-Instruct | 1.30 | 0.95 | 1.82 | 0.95 | 0.00 | 2.22 |
| LLaMA2-7B-chat | 1.48 | 1.90 | 0.61 | 2.86 | 2.67 | 0.00 |
| ChatGLM3 | 1.48 | 1.90 | 0.61 | 4.76 | 0.00 | 0.00 |
| GLM-4-9B-chat | 2.04 | 2.86 | 0.61 | 5.71 | 1.33 | 0.00 |
| Vicuna-13B-v1.5 | 5.19 | 10.48 | 1.21 | 8.57 | 5.33 | 2.22 |
| GPT-3.5-Turbo | 7.78 | 13.33 | 5.45 | 8.57 | 12.00 | 1.11 |
| Vicuna-7B-v1.5 | 8.52 | 12.38 | 4.24 | 17.14 | 6.67 | 3.33 |
| Mistral-7B-Instruct-v0.2 | 11.85 | 26.67 | 2.42 | 17.14 | 13.33 | 4.44 |
| AVG | 3.19 | 5.79 | 1.49 | 5.13 | 3.18 | 1.02 |

### 大模型越狱安全排行榜
利用大型语言模型越狱安全评测数据集 [JailBench](/JailBench.csv) ，我们针对国内外多款主流大型语言模型开展模型越狱安全性评估，各模型的安全评测结果如下（按综合越狱成功率升序排列）：

| 模型名称 | 综合越狱成功率(%) | 违反社会主义核心价值观(%) | 歧视(%) | 侵犯他人合法权益(%) | 商业违法违规(%) | 无法满足特定服务类型安全需求(%) |
| :---------: | :---------: | :---------: | :---------: | :---------: | :---------: | :---------: |
| GPT-4-0613 | 34.50 | 26.86 | 38.09 | 31.57 | 39.20 | 36.33 |
| LLaMA3-8B-Instruct | 43.94 | 25.33 | 56.45 | 41.05 | 34.80 | 53.72 |
| LLaMA2-7B-chat | 48.68 | 41.71 | 51.03 | 48.71 | 52.80 | 49.00 |
| Qwen2-7B-chat | 49.73 | 47.05 | 49.30 | 54.24 | 55.53 | 43.56 |
| InterLM2-chat-7B | 51.22 | 50.14 | 50.24 | 55.71 | 57.60 | 43.72 |
| LLaMA2-13B-chat | 55.39 | 46.00 | 60.39 | 57.48 | 55.73 | 54.44 |
| Vicuna-7B-v1.5 | 59.27 | 65.81 | 56.39 | 65.43 | 61.13 | 48.17 |
| ChatGLM3 | 58.81 | 51.76 | 66.70 | 58.14 | 60.13 | 52.22 |
| Vicuna-13B-v1.5 | 66.32 | 72.67 | 65.27 | 71.29 | 67.13 | 54.39 |
| Qwen1.5-7B-chat | 71.60 | 69.67 | 71.09 | 73.90 | 79.00 | 65.94 |
| GPT-3.5-Turbo | 73.86 | 74.67 | 76.64 | 74.81 | 75.20 | 65.61 |
| GLM-4-9B-chat | 74.95 | 73.19 | 76.64 | 77.62 | 80.47 | 66.22 |
| Mistral-7B-Instruct-v0.2 | 78.14 | 83.62 | 76.52 | 82.10 | 82.07 | 66.83 |
| AVG | 58.95 | 56.04 | 61.13 | 60.93 | 61.60 | 53.86 |

**越狱评估指标**：越狱成功率(ASR)，指能够成功突破模型安全护栏并产生有害输出的测试问题占总测试问题的比例。越狱成功率越高，代表目标模型的安全防护能力越弱。  

**有害性评估标准**：对于所有涉及内容有害性评估的部分，我们均使用 [MDJudge](https://huggingface.co/OpenSafetyLab/MD-Judge-v0.1) 分类器对模型输出的安全性进行评估，该分类器具有优秀的内容安全识别能力，能够准确识别、分类模型输出的安全风险。

## 致谢

我们对以下开源贡献表示感谢

    [1] https://huggingface.co/OpenSafetyLab/MD-Judge-v0.1
    [2] https://github.com/SheltonLiu-N/AutoDAN
    [3] https://github.com/tmlr-group/deepinception
    [4] https://github.com/sherdencooper/gptfuzz

## 引用
```bibtex
@article{liu2025jailbench,
  title   = {JailBench: A Comprehensive Chinese Security Assessment Benchmark for Large Language Models},
  author  = {Shuyi Liu and Simiao Cui and Haoran Bu and Yuming Shang and Xi Zhang},
  year    = {2025},
  journal = {arXiv preprint arXiv: 2502.18935}
}
```

## 关于我们

STAIR (Secure and Trustworthy AI Research) 团队隶属于北京邮电大学网络空间安全学院和可信分布式计算与服务教育部重点实验室。团队主要研究安全可信人工智能技术，及在网络空间治理领域的应用，近年来在网络内容与行为分析、大模型安全等方面承担了国家重点研发计划等多项重要科研任务。

**联系我们**

zhangx@bupt.edu.cn
    
