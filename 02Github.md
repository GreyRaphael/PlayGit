# Github

- [Github](#github)
  - [Introduction](#introduction)
  - [Github with Collaborator](#github-with-collaborator)
  - [Github Organization](#github-organization)
  - [Development Flow](#development-flow)

## Introduction

[Github Features](https://github.com/features)
> github的CI是3rd提供的  
> gitlab本身具有CI

Github Search Repos Trick:
- [Advanced Search](https://github.com/search/advanced?) Repos: `created:<2019-01-01`
- search readme: `ipv6 hosts google in:readme filename:hosts`
- search readme: `ipv6 hosts in:readme stars:>1000`
- search blog: `github blog in:readme stars:>2000`

**Github blog**

Github Advanced Search: `github blog in:readme`
> [jekyll](https://github.com/barryclark/jekyll-now)

example: sync with github

```bash
git remote add github git@github.com:GreyRaphael/test.git
git remote -v
# github  git@github.com:GreyRaphael/test.git (fetch)
# github  git@github.com:GreyRaphael/test.git (push)
# zhineng file://C:\Users\Administrator\Downloads\zhineng.git (fetch)
# zhineng file://C:\Users\Administrator\Downloads\zhineng.git (push)

# push all branches to remote
git push github --all
# To github.com:GreyRaphael/test.git
#  * [new branch]      gewei -> gewei
#  * [new branch]      temp -> temp
#  ! [rejected]        master -> master (fetch first)
# error: failed to push some refs to 'git@github.com:GreyRaphael/test.git'

# pull: 先fetch再merge; 保险起见fetch
git fetch github master
# From github.com:GreyRaphael/test
#  * branch            master     -> FETCH_HEAD
#  * [new branch]      master     -> github/master

# fetch会将remote的tree拿下来，但trees并没有连接
gitk --all
```

non fast-forward: master与remote/github/master没有共同的祖先; 所以non fast-forward再push回报错;

method1: merge

```bash
# method1: merge
git checkout master
git merge github/master # 因为master没有父子关系，会报错
# fatal: refusing to merge unrelated histories
git merge --allow-unrelated-histories github/master # ok
gitk --all # merge之后的HEAD有两个Parent节点
git push github master
```

method2: rebase
> 以remote/github/master作为基础，`rebase -i`, 然后pick, squish, squish来形成一个新的tree, 代价就是更改了以前commits的hash值

## Github with Collaborator

Method1: repo/Settings/Collaborators(recommended)
> all collaborators should have Github account

Method2: 

## Github Organization

Organization包含repos, Organization中有People(Github user), 权限控制采用Team
> 对比Gitlab, People中的所有人都可以看到其他人的权限，方便申请

[ExampleOrganization](https://github.com/pku-ion-beam)

## Development Flow

Trunk Based Development
> Java开发挺适用的  
> <img src="Res02/trunk.png" height=400>

Git Flow
> 适用于：不具备主干开发能力。有预定的发布周期。需要执行严格的发布流程。研发周期长。  
> <img src="Res02/gitflow.png" height=400>

Github Flow
> <img src="Res02/github_flow.png" height=400>

Production branch with GitLab flow
> 适用于：不具备主干开发能力。无法控制准确的发布时间，但又要求不停的集成。  
> <img src="Res02/gitlab_flow_production.png" height=400>

Environment branches with GitLab flow
> 适用于：不具备主干开发能力。需要逐个通过各个测试环境的验证才能发布  
> <img src="Res02/gitlab_flow_env.png" height=400>

Release branches with GitLab flow
> 适用于：不具备主干开发能力。需要对外发布和维护不同版本(比如不同驱动的不同版本都可以用，那么就要维护多个版本)。  
> <img src="Res02/gitlab_flow_release.png" height=400>

简单的一般采用Github多个特性分支开发的方式
