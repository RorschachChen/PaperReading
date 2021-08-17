# Have Read
---
## Passport-based

Main Idea: 将trigger set在pytorch等pretrained的相同网络每层上的features作为passport。添加passport layer使得scale和bias因子成为passport的函数。当伪造的passport输入的时候会影响model的性能，通过fedility达到erification的目的。训练时的passport branch不会分发到客户端，只有在进行验证的时候加入。

1. (Passport)Jie Zhang, Dongdong Chen, Jing Liao, Weiming Zhang, Gang Hua, Nenghai Yu: “Passport-aware Normalization for Deep Model Protection”, 2020

    Code Check. 代码上来看最大的改变在于get_scale和get_bias最后添加了一个三层的fc block。还有就是原版norm只能使用gn之后的那几个，这个版本的可以继续使用bn类型的norm。
    
    Main Idea: two-branch decoupled way。避免修改原网络结构。减少模型performance degradation. scala和bias learnable.

2. (Passport)Lixin Fan, Kam Woh Ng, Chee Seng Chan: “[Extended version] Rethinking Deep Neural Network Ownership Verification: Embedding Passports to Defeat Ambiguity Attacks”, 2019

    Code Check. 原版

3. (Passport)L. Fan, K. W. Ng, C. S. Chan and Q. Yang, "DeepIPR: Deep Neural Network Intellectual Property Protection with Passports," in IEEE Transactions on Pattern Analysis and Machine Intelligence, doi: 10.1109/TPAMI.2021.3088846.

    Code Check. 原版

## Deep Watermark
4. Jie Zhang, Dongdong Chen, Jing Liao, Han Fang, Zehua Ma, Weiming Zhang, Gang Hua, Nenghai Yu: “Exploring Structure Consistency for Deep Model Watermarking”, 2021

    No Code.

5. Jie Zhang, Dongdong Chen, Jing Liao, Weiming Zhang, Huamin Feng, Gang Hua, Nenghai Yu: “Deep Model Intellectual Property Protection via Deep Watermarking”, 2021

    No Code.

6. Jie Zhang, Dongdong Chen, Jing Liao, Han Fang, Weiming Zhang, Wenbo Zhou, Hao Cui, Nenghai Yu: “Model Watermarking for Image Processing Networks”, 2020

    No Code.

7. (GAN) Ding Sheng Ong, Chee Seng Chan, Kam Woh Ng, Lixin Fan, Qiang Yang: “Protecting Intellectual Property of Generative Adversarial Networks from Ambiguity Attack”, 2021

    Code Check.

8. Xiquan Guan, Huamin Feng, Weiming Zhang, Hang Zhou, Jie Zhang, and Nenghai Yu. 2020. Reversible Watermarking in Deep Convolutional Neural Networks for Integrity Authentication. In Proceedings of the 28th ACM International Conference on Multimedia

    No code.
    
    Main Idea: 引申传统reversible watermark概念到image construction领域。利用entropy找到less important layer weight.然后在weight的小数非零位置挑选两位准备embed bit string。最后通过histogram shift方法正式嵌入

# Haven't Read
---

