项目：ChnSentiCorp中文情感分类
项目背景：互联网有大量的消费者评价的文本数据，ChnSentiCorp数据集就收集了上万条中文购物评价文本数据，包括酒店的居住体验，电脑、手机等电子产品购买后使用评价，书籍的阅读感受。对这些文本进行情感分类能够追踪用户体验，及时了解产品市场反馈。
项目内容：

实验1:把用户消费后产生的中文评价，通过分词器，把每个token嵌入为768维度的向量。然后使用bert-base-chinese模型作为backbone进行文本的特征抽取，再接入下游的神经网络分类层进行二分类。我们尝试了（1）只微调网络最后分类层，冻结backbone参数（2）微调模型全部参数，包括backbone和最后分类层。最后在测试集上都达到了89%的分类精度。说明BERT预训练模型抽取的信息非常全面，无需微调，能大大减少下游任务计算量，并取得不错的结果。

实验2:用deberta_v3_large又跑了一遍，效果不佳。

实验3:用Prompt-tuning方法，效果相对方法1大幅提升。达到了0.95的micro f1 score
项目架构：PyTorch+HuggingFace+BERT

Huggingface 工具集快速使用入门 以及 中文任务示例


视频课程:https://www.bilibili.com/video/BV1a44y1H7Jc
视频课程补充篇:https://www.bilibili.com/video/BV1Cr4y1V7mF

运行环境:
python=3.6
torch=1.10.1 (cpu)
transformers=4.18.0
datasets=2.4.0
