
可参考：
http://www.xderedu.com/2020/04/15/DEEPBINDIFF%E8%AE%BA%E6%96%87%E9%98%85%E8%AF%BB%E7%AC%94%E8%AE%B0/
https://www.zybuluo.com/SmashStack/note/726255

A Survey of Binary Code Similarity：https://arxiv.org/pdf/1909.11424.pdf

https://users.encs.concordia.ca/~youssef/Publications/Papers/AsiaCCS2017.pdf

多个二进制分析工具各项性能进行的分析与比较：https://zhuanlan.zhihu.com/p/87611894

程序安全分析平台初探：IR 与应用。： https://zhuanlan.zhihu.com/p/127174468
https://github.com/GoSSIP-SJTU
自动化二进制文件分析框架：angr：  https://zhuanlan.zhihu.com/p/25192237





# DeepBinDiff

This is the official repository for DeepBinDiff, which is a fine-grained binary diffing tool for x86 binaries. We will actively update it.

### Paper
Please consider citing our paper.

Yue Duan, Xuezixiang Li, Jinghan Wang, and Heng Yin, "DeepBinDiff: Learning Program-Wide Code Representations for Binary Diffing", NDSS'2020


### Requirements:

* tensorflow (2.0 > tensorflow version >= 1.14.0)
* gensim
* angr
* networkx
* lapjv



### Run the tool


```
python3 src/deepbindiff.py --input1 path_to_the_first_binary --input2 /path_to_the_second_binary --outputDir output/
```

* For example, to compare O0 and O1 chroot binaries from coreutils v5.93, you may run:

```
python3 src/deepbindiff.py --input1 /home/DeepBinDiff/experiment_data/coreutils/binaries/coreutils-5.93-O0/chroot --input2 /home/DeepBinDiff/experiment_data/coreutils/binaries/coreutils-5.93-O1/chroot --outputDir output/
```


* You can also use **src/analysis_in_batch.sh** script to perform binary diffing in batches.


### Misc
1. IDA Pro or Angr?

We have both the IDA pro version and the angr version. IDA pro is used in order to directly compare with BinDiff, which uses IDA pro as well. The code here uses Angr.

2. Results?

Results are printed directly on the screen as "matched pairs" once the diffing is done. Each pair represents a matched pair of basic blocks in the two binaries. The numbers are the basic block indices, which can be found in output/nodeIndexToCode file.

3. CPU or GPU?

The current version is using CPU only. 

4. NLP pre-training?

The current version uses an on-the-fly training process, meaning we only use the two input binaries for NLP training. Therefore, we don't need any pre-trained model. This will eliminate the OOV problem but will slow down the process a bit.
