---
title: "Certified Kubernetes Application Developer (CKAD) Exam Preparation Tips"
description: "Kubernetes exam preparation tips"
layout: post
toc: true
comments: true
search_exclude: false
author: Arif Hossen
categories: [Kubernetes, Certification, Cloud Native]
show_tags: true
---


# Certified Kubernetes Application Developer (CKAD)

Recently, I have completed Certified Kubernetes Application Developer ([CKAD](https://www.cncf.io/certification/ckad/)) certification of [The Linux Foundation](https://www.linuxfoundation.org). Here are a few tips for the exam which might help you as well to crack the same exam.



## Vi / Vim setting for yaml to Edit Comfortably & Efficiently

Added few setting in .vimrc profile which help to edit yaml file effectively and efficiently. 

```bash
cat <<EOF>~/.vimrc
set ts=2 sw=2 sts=2 et ai number
syntax on
EOF
```

Or may be follow below procedure:
```bash
echo "set ts=2 sts=2 sw=2 et number" >> ~/.vimrc
```

While copying part of yaml from kubernetes.io site, enable past mode first using `:set paste` which will keep source formatting. 

Disable paste mode by using command: `:set nopaste` in vim command mode. Again turn on auto intendation mode using `:set ai`.

To indent multiple line, go to appropriate line and press `:shift+v` and select required line using `up/down` arrow keys. Then to indent the marked lines press  `>`or `<` and to repeat same action use `.`.



## Command Alias

Used below command alias to type command quickly and check various resources in a single command for a namespace. 

```bash
cat <<EOF>kalias.sh
alias k="kubectl"
alias kgn="kubectl get node" 
alias aa='kubectl get all,sa,ep,sc,pv,pvc,cm,netpol'
alias kn='kubectl config set-context --current --namespace '
alias kcc='kubectl config get-contexts'

export do="--dry-run=client -o yaml" o="-o wide" y="-o yaml" l="--show-labels" r="--recursive"

source <(kubectl completion bash)
complete -F __start_kubectl k
EOF

source kalias.sh
```

Command alias and environment will help to type or generate yaml spec quickly and then modify specification file if required.
```bash
# check current context (as per command alias above)
kcc 

# set namespace (as per command alias above)
kn namespace

# check necessary information by one command (as per command alias above)
aa

# for pod spec
k run podname --image=nginx $do > pod-spec.yaml

# for deployment spec
k create deployment nginx-deploy --image=nginx -r 3 $do > deployment-spec.yaml
```


## Tmux Setting

Tmux is a great tool but I havn't used because copy and paste method is different than the normal termal. Also time is ticking and need to move quickly to answer all the questions.....



## Bookmark Allowed Website Content (Mainly yaml format) 

In my bookmark manager, added necessary sample yaml from [kubernetes.io site](https://kubernetes.io) so that I could check content quickly when it is required. 



## Lab Practice

At the end, do a lot of practice in your lab which will help to think and make an action plan for the question in the exam. To answer all the questions you have to act quickly and the allowed time is only 120 min which runs fast.

* Use imperative command to create skeleton for pod or deployment and then modify/add extra parameters
* Use imperative command to expose service
* Use bash search command `ctl+r`to run previously executed command.


## During Exam
During the exam, first try to solve the question which has more weight compared to the lower weight question.

In this way, most likely, you will be able to avoid troubleshooting activity for the lower weight question if not solved in the first attempt or easily within your timeline. Because of exam pressure, sometimes you may give more time to lower weight questions, As a consequence, at the end you may not be able to give sufficient time to higher weight questions.


# Appendix

## Frequenly Use vi/vim commands

```bash
w ==> jump by start of words
4w >> jump muultiple word
e ==> jump by end of words
3e>> multiple at a time
b ==> jump backward by words
0 ==> (zero) is to jump to the start of the line
$ ==> (dollar) jumps to end of line
gg ==> to go to top of page
G ==> to go to bottom of page
dd ==> delete current line
y ==> yank/copy current line
P ==> paste content before cursor
p ==> paster content after cursor
i ==> enter insert mode to input text in current cursor location
a ==> enter insert mode and move cursor to append to the existing line
u ==> undo last action
. ==> (dot) to repeat last command
Ctrl + r ==> redo last action
v ==> to visually select multiple lines


:5 ==> go to 5th line in the file
:N ==> go to Nth line in the file
/search_text ==> search for search_text
n ==> repeat search in same direction
:%s/old_text/new_text/g ==> replace all old_text with new_text throughput file
:%s/old_text/new_text/gc ==> replace all old_text with new_text throughput file asking for confirmation before making each change
:set et ==> set expandtabs to spaces
:set number ==> show line numbers
:set sw=2 ==> shiftwidth of tab from default 8 to 2 spaces
:set ts=2 ==> set tabstop to 2 spaces
:set sts ==> set softtabstop to 2 spaces
```

