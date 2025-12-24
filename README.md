# Hi there 👋

## 🐍 My GitHub Snake
![snake gif](https://raw.githubusercontent.com/shiyiyueshihao/shiyiyueshihao/output/github-snake.svg)


#	gihub贪吃蛇

##	1.创建一个同名的仓库

##	2.创建  snake.yml 文件 

###	路径如图所示

  <img width="825" height="308" alt="snake yml文件位置" src="https://github.com/user-attachments/assets/01a96123-2431-4afa-94ab-7f3baf3eff83" />

你的仓库名/.github/workflows/snake.yml

##	3.粘贴代码
###  将下列代码粘贴到你的 snake.yml 里去


```
name: GitHub Snake Game



on:

  # Schedule the workflow to run daily at midnight UTC

  schedule:

    - cron: "0 0 * * *"



  # Allow manual triggering of the workflow

  workflow_dispatch:



  # Trigger the workflow on pushes to the main branch

  push:

    branches:

      - main



jobs:

  generate:

    runs-on: ubuntu-latest

    timeout-minutes: 10



    steps:

      # Step 1: Checkout the repository

      - name: Checkout Repository

        uses: actions/checkout@v3



      # Step 2: Generate the snake animations

      - name: Generate GitHub Contributions Snake Animations

        uses: Platane/snk@v3

        with:

          # GitHub username to generate the animation for

          github_user_name: ${{ github.repository_owner }}



          # Define the output files and their configurations

          outputs: |

            dist/github-snake.svg

            dist/github-snake-dark.svg?palette=github-dark

            dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9

        env:

          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}



      # Step 3: Deploy the generated files to the 'output' branch

      - name: Deploy to Output Branch

        uses: peaceiris/actions-gh-pages@v3

        with:

          github_token: ${{ secrets.GITHUB_TOKEN }}

          publish_dir: ./dist

          publish_branch: output

          # Optionally, you can set a custom commit message

          commit_message: "Update snake animation [skip ci]"
```

##	4.回Actions查看状态

###	一般会因为权限不足导致运行失败

<img width="1603" height="666" alt="权限不足处理方案" src="https://github.com/user-attachments/assets/8fe83bc4-4cf2-44fd-b497-7048d19f4ca3" />


我们可以  在仓库的上面找到 settings  点开之后找到左侧的Actions 下面的 General，然后往下拉 找到  Workflow permissions 将 读写权限  勾选 即可
（别忘了点击保存 save）

<img width="1467" height="887" alt="仓库Actions权限设置" src="https://github.com/user-attachments/assets/2a228f9b-8804-45b1-bd9a-cdaffae0229a" />


##	5.二次运行

###	点击workflows，找到选项 右边有 Run workflow

<img width="1838" height="641" alt="二次运行" src="https://github.com/user-attachments/assets/4e70b938-574e-4e21-b1cb-6bd4f3a22cee" />


运行完成  进入 README.md  进行编辑 将下面代码粘贴进去保存即可

```
![snake gif](https://raw.githubusercontent.com/你的仓库名字/你的仓库名名字/output/github-snake.svg)
```

