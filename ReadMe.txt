更换电脑后重新拉去hexo的步骤：

1.使用以下命令拉取hexo分支代码
  git clone -b hexo git@github.com:ShellyDong/shellydong.github.io.git

2.powershell进入本地repo目录，依次安装以下hexo及插件
  npm install hexo-cli -g
  npm install
  npm install hexo-deployer-git --save

3.hexo clean
  hexo g
  hexo s

4.新建blog
  hexo new draft "your title"
  hexo g --draft
  hexo publish post "your title"


5.修改后提交源码到hexo分支
  git checkout
  git add --all
  git commit -m "commit note"
  git push --set-upstream origin hexo