<h2 align="left">Olá 👋! Sou Ednilson Bastos, apaixando por tecnologias e especialmente por "Dados".</h2>

###

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=EdnilsonBastos&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false" height="150" alt="stats graph"  />

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="30" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apachespark/apachespark-original.svg" height="30" alt="apachespark logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/oracle/oracle-original.svg" height="30" alt="oracle logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="30" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" height="30" alt="postresql logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/r/r-original.svg" height="30" alt="r logo"  />
  <img width="12" />
  
</div>

###

<div align="left"> 
  <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/EdnilsonBastos/EdnilsonBastos/output/snake.svg" alt="Snake animation" />

###


name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/EdnilsonBastos/EdnilsonBastos/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/EdnilsonBastos/EdnilsonBastos/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/EdnilsonBastos/EdnilsonBastos/output/github-contribution-grid-snake.svg">
</picture>
