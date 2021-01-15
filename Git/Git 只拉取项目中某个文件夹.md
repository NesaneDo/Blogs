# Git 只拉取项目中某个文件夹

1. git init
2. git remote add <name> <url>
3. git config core.sparsecheckout true  // git 1.7.0 之后
4. echo '<dir>' >> .git/info/sparse-checkout
5. git pull <name> <url>