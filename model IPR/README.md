# Always Remember

focus on embedding watermark in model, not images.

# Have Read
---
## Passport-based

Main Idea: 将trigger set在pytorch等pretrained的相同网络每层上的features作为passport。添加passport layer使得scale和bias因子成为passport的函数。当伪造的passport输入的时候会影响model的性能，通过fedility达到erification的目的。训练时的passport branch不会分发到客户端，只有在进行验证的时候加入。

1. (Passport)Jie Zhang, Dongdong Chen, Jing Liao, Weiming Zhang, Gang Hua, Nenghai Yu: “Passport-aware Normalization for Deep Model Protection”, 2020

    Code Check. 代码上来看最大的改变在于get_scale和get_bias最后添加了一个三层的fc block。还有就是原版norm只能使用gn之后的那几个，这个版本的可以继续使用bn类型的norm。
    
    Main Idea: two-branch decoupled way。避免修改原网络结构。减少模型performance degradation. scala和bias learnable.
    
    Code: [Passport-aware-normalization](https://github.com/ZJZAC/Passport-aware-Normalization)

2. (Passport)Lixin Fan, Kam Woh Ng, Chee Seng Chan: “[Extended version] Rethinking Deep Neural Network Ownership Verification: Embedding Passports to Defeat Ambiguity Attacks”, 2019

    Code: [DeepIPR](https://github.com/kamwoh/DeepIPR)

3. (Passport)L. Fan, K. W. Ng, C. S. Chan and Q. Yang, "DeepIPR: Deep Neural Network Intellectual Property Protection with Passports," in IEEE Transactions on Pattern Analysis and Machine Intelligence, doi: 10.1109/TPAMI.2021.3088846.

    Code Check. 原版

## Deep Watermark: 主要针对surrogate model
4. Jie Zhang, Dongdong Chen, Jing Liao, Han Fang, Zehua Ma, Weiming Zhang, Gang Hua, Nenghai Yu: “Exploring Structure Consistency for Deep Model Watermarking”, 2021

    No Code.
    
    Motivation: Aug destroy watermark consistency.
    
    Main Idea: embed watermark information into semantic structures. Incremental Training Strategy. Loss包含基础l2,adv,同时还考虑到structure(watermark) regions提取的watermark和GT要相近，非此region提取为空。同时没有watermark的图片提取为空。

5. Jie Zhang, Dongdong Chen, Jing Liao, Weiming Zhang, Huamin Feng, Gang Hua, Nenghai Yu: “Deep Model Intellectual Property Protection via Deep Watermarking”, 2021

    No Code.
    
    Main Idea: Loss包含基础l2,perceptual,adv. 无wm clean loss. 鼓励从不同图片提取的wm相近。

6. Jie Zhang, Dongdong Chen, Jing Liao, Han Fang, Weiming Zhang, Wenbo Zhou, Hao Cui, Nenghai Yu: “Model Watermarking for Image Processing Networks”, 2020

    No Code.

7. (GAN) Ding Sheng Ong, Chee Seng Chan, Kam Woh Ng, Lixin Fan, Qiang Yang: “Protecting Intellectual Property of Generative Adversarial Networks from Ambiguity Attack”, 2021

    Code: [ipr-gan](https://github.com/dingsheng-ong/ipr-gan)
    
    Main Idea: 通过在loss中嵌入SSIM，通过对input noise进行transform创造一个distribution不同的trigger。同时利用wm image创造一个specific target，让Generator产生的output和这个target尽可能相似。同时perceptual和adv穿插着出现。针对white-box attack，把signature嵌入norm层(scale和bias那一套)，随后用提取的signature验证。

8. Xiquan Guan, Huamin Feng, Weiming Zhang, Hang Zhou, Jie Zhang, and Nenghai Yu. 2020. Reversible Watermarking in Deep Convolutional Neural Networks for Integrity Authentication. In Proceedings of the 28th ACM International Conference on Multimedia

    No code.
    
    Main Idea: 引申传统reversible watermark概念到image construction领域。利用entropy找到less important layer weight.然后在weight的小数非零位置挑选两位准备embed bit string。最后通过histogram shift方法正式嵌入
    
27. Xin Zhong, Frank Y. Shih: “A Robust Image Watermarking System Based on Deep Neural Networks”, 2019

28. Xin Zhong, Pei-Chi Huang, Spyridon Mastorakis, Frank Y. Shih: “An Automated and Robust Image Watermarking Scheme Based on Deep Neural Networks”, 2020

29. Yuki Nagai, Yusuke Uchida, Shigeyuki Sakazawa, Shin'ichi Satoh: “Digital Watermarking for Deep Neural Networks”, 2018
    
## Others

9. MaungMaung AprilPyone, Hitoshi Kiya: “Training DNN Model with Secret Key for Model Protection”, 2020

    Main Idea: image classification。input分block加key再复原作为预处理。train和test时都使用预处理的。
    
11. Mingfu Xue, Yushu Zhang, Jian Wang, Weiqiang Liu: “Intellectual Property Protection for Deep Learning Models: Taxonomy, Methods, Attacks, and Evaluations”, 2020

    Main Idea: model ip问题overview总览及企盼
    
14. Yuanchun Li, Ziqi Zhang, Bingyan Liu, Ziyue Yang, Yunxin Liu: “ModelDiff: Testing-Based DNN Similarity Comparison for Model Reuse Detection”, 2021

    code: [ModelDiff](https://github.com/ylimit/ModelDiff)
    
18. Tang, Ruixiang & Du, Mengnan & Hu, Xia. (2020). Deep Serial Number: Computational Watermarking for DNN Intellectual Property Protection. 

25. Bita Darvish Rouhani, Huili Chen, Farinaz Koushanfar: “DeepSigns: A Generic Watermarking Framework for IP Protection of Deep Learning Models”, 2018

    Main Idea: use the activations of some target layer of the source model to encode a message. 从属于同一源类的样本中提取的特征形成簇，其特性可用于嵌入水印信息。
    
26. B. Wang, Y. Yao, S. Shan, H. Li, B. Viswanath, H. Zheng, and B. Y.Zhao, “Neural cleanse: Identifying and mitigating backdoor attacks in neural networks,”
    
    Main Idea: For backdoor removal. It first reverse-engineers the watermark trigger and then remoes the trigger from the model. 
    
19. Lukas N, Jiang E, Li X, et al. SoK: How Robust is Image Classification Deep Neural Network Watermarking?(Extended Version)[J]. arXiv preprint arXiv:2108.04974, 2021.

    Main Idea: 复现各类paper，综述类文章
    
## Artificial Fingerprints

已知缺陷: require the models to have the same output space.

12. Ning Yu, Vladislav Skripniuk, Sahar Abdelnabi, Mario Fritz: “Artificial Fingerprinting for Generative Models: Rooting Deepfake Attribution in Training Data”, 2020

14. Xiaoyu Cao, Jinyuan Jia, and Neil Zhenqiang Gong. 2019. IPGuard: Protecting the Intellectual Property of Deep Neural Networks via Fingerprinting the
Classification Boundary. arXiv preprint arXiv:1910.12903 (2019).

    Main Idea:在decision boundary附近找一堆点，和在这些点上的prediction作为验证集。
    
15. Nils Lukas, Yuxuan Zhang, and Florian Kerschbaum. 2019. Deep Neural Network Fingerprinting by Conferrable Adversarial Examples. arXiv preprint
arXiv:1912.00888 (2019).

    Main Idea: introduced the concept of conferrable inputs, i.e. targeted adversarial inputs that are transferable to surrogate models while not transferable to reference models that are trained independently. 

## Traditional Method Involved

13. Feng, Le & Zhang, Xinpeng. (2020). Watermarking Neural Network with Compensation Mechanism. 10.1007/978-3-030-55393-7_33. 

    Review: 使用了传统的一些加密手段，需要一定知识积累。
    
16. MaungMaung AprilPyone, Hitoshi Kiya: “Piracy-Resistant DNN Watermarking by Block-Wise Image Transformation with Secret Key”, 2021

    Main Idea: 分block,然后把Binary Key K作为mask改变每个block的值,制造transformed的图片加入训练.使网络记住这一种transform,这样测试的时候只需要对比网络对original test和transformed test输出是否一样就能verify.
    
## Embed During Training

10. Huiying Li, Emily Wenger, Shawn Shan, Ben Y. Zhao, Haitao Zheng: “Piracy Resistant Watermarks for Deep Neural Networks”, 2019

## textual domain

## Model Independent: 不关注model本身,只修改training set

20. Y. Adi, C. Baum, M. Cisse, B. Pinkas, and J. Keshet, “Turning your weakness into a strength: Watermarking deep neural networks by backdooring,”

    Main Idea: trigger set的label是随机的.
    
21. J. Zhang, Z. Gu, J. Jang, H. Wu, M. P. Stoecklin, H. Huang, and I. Molloy, “Protecting intellectual property of deep neural networks with watermarking

    Main Idea: 来自同一个类的image,加上additive mask或者noise mask,还有一种是用其他domain的图片作为watermark key.
    
## Model Dependent: 类似手法有针对model生成对抗样本,跟模型有关.

22. E. Le Merrer, P. Perez, and G. Tredan, “Adversarial frontier stitching for remote neural network watermarking"
    
    Main Idea: 使用可能被识别错误也可能被识别正确的对抗样本作为watermark key.
    
23. The authors propose a pre-processing step that clusters all class labels into two groups using k-means clustering on the pre-trained source model’s logit activations.

    Main Idea: 根据logit的输出使用KNN分成两类,再使用另一个cluster的label学习生成对抗样本,其余步骤同上.
    
24. H. Jia, C. A. Choquette-Choo, and N. Papernot, “Entangled watermarks as a defense against model extraction,”

    Main Idea: 

# Haven't Read
---

17. Mohammad Mehdi Yadollahi, Farzaneh Shoeleh, Sajjad Dadkhah, Ali A. Ghorbani: “Robust Black-box Watermarking for Deep NeuralNetwork using Inverse Document Frequency”, 2021

30. Changhoon Kim, Yi Ren, Yezhou Yang: “Decentralized Attribution of Generative Models”, 2020

    Main Idea: attributability
    
31. Convolutional Neural Network-Based Digital Image Watermarking Adaptive to the Resolution of Image and Watermark
