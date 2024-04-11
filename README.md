# 项目：ChnSentiCorp中文情感分类

## 项目背景：
互联网有大量的消费者评价的文本数据，ChnSentiCorp数据集收集了上万条中文购物评价数据，包括酒店的居住体验，电脑、手机等电子产品购买后使用评价，书籍的阅读感受。对这些文本进行情感分类能够追踪用户体验，及时了解产品市场反馈。

## 项目内容：
把评价文本数据通过bert-base-chinese和deberta v3 large模型作为backbone进行特征抽取，分别尝试（1）直接把<CLS> token接入下游的神经网络分类层（2）采用Prompt-Tuning方法，把<MASK> token接入下游的神经网络分类层。

文本分类效果：使用google-bert/bert-base-chinese模型取得(1) 0.89和(2) 0.96的F1 score。

（1）在这个任务上bert-base-chinese表现优于deberta-v3-large，说明在高质量中文语料库上预训练的模型更适合中文任务，更复杂的模型未必表现更佳。

（2）只微调最后分类层，和微调backbone全部参数结果没有区别，说明谷歌的bert-base-chinese的预训练质量非常高，抽取中文文本特征效果非常好，无需微调。

（3）Prompt-Tuning相对于Fine-Tuning，更能对齐下游任务与预训练任务的目标，能够自动学习prompt pattern，能够显著提升模型的预测精度，0.88 -> 0.95。

项目架构：PyTorch+HuggingFace+BERT


Huggingface 工具集快速使用入门 以及 中文任务示例


视频课程:https://www.bilibili.com/video/BV1a44y1H7Jc
视频课程补充篇:https://www.bilibili.com/video/BV1Cr4y1V7mF

运行环境:
python=3.6
torch=1.10.1 (cpu)
transformers=4.18.0
datasets=2.4.0
