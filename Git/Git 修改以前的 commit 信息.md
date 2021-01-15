# Git 如何修改之前 commit 的信息

1. **`git rebase -i HEAD~3`** 找到最近 **`3`** 次的提交

   ![image-20200911172332100](修改以前的 commit 信息.assets/image-20200911172332100.png)

2. 找到你要修改的项，将前面的 **`pick`** 修改为 **`edit`** 后直接 **`:wq`** 保存退出，其他的不要动

   ![image-20200911172457938](修改以前的 commit 信息.assets/image-20200911172457938.png)

3. 保存退出后会提示如下信息

   ![image-20200911172834455](修改以前的 commit 信息.assets/image-20200911172834455.png)

4. 照提示输入 **`git commit --amend`** 后，会进入到修改界面，修改提交信息后，**`:wq`** 保存退出

   ![image-20200911173156821](修改以前的 commit 信息.assets/image-20200911173156821.png)

5. 继续输入 **`git rebase --continue`** 

   ![image-20200911173256657](修改以前的 commit 信息.assets/image-20200911173256657.png)

6. 最后输入 **`git push -f`** 强制提交，*有可能需要指定远程分支*

   ![image-20200911173440982](修改以前的 commit 信息.assets/image-20200911173440982.png)

