# CKAD Resources

Here I will document some of my actions for
the [CKAD](https://training.linuxfoundation.org/training/kubernetes-for-developers/)
certification preparation.

## Kubernetes Cluster

To exercise you can create an AWS cluster or Google Cloud one, but they may be
costly. You can also create your own cluster using virtualbox. I have created a
vagrant based project [here](http://ivo2u.nl/Z7) to easily create a cluster with
a master node and n worker nodes (default = 2).

## Courses

To prepare for the certification I followed two courses:

- [LFD259 at the linux foundation](https://training.linuxfoundation.org/training/kubernetes-for-developers/)
  This course has the certification included (with re test if needed)
- [Certified Kubernetes Administrator (CKA) with Practice Tests at Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
  A very nice video based course with a kodekloud exercise place.

## Tips and tricks

- to save time you can use variables and aliases to make commands easier and
  faster to type:

```shell
#setting the namespace (just do this one again for another namespace if needed)
export NS=default
# You will do dry runs often and now you can just type $DR in stead of the whole thing
export DR='--dry-run=client -o yaml'
# use k to run the kubectl command in the exported namespace. Saves typing
alias k='kubectl -n $NS'
# if you know you are going to dry run...
alias kdr='k $DR'
# Now get code completion on both commands
complete -F __start_kubectl k kdr

# the above is the minimal setup. I prefer the following to

alias ka='kubectl get all -A'
alias kc='k create -f'
alias kd='k delete -f'
```

So...

<details><summary>Show</summary>
<p>

```shell
# if you forgot the kdr at the beginning just add the $DR
k run nginx --image=nginx --port 80 $DR >nginx.yml

# or if you didn't forget
kdr run nginx --image=nginx --port 80 >nginx.yml

# doing commands on another namespace
export NS=otherns
#use 'k' 'kdr' as you would normally
#don't forget to go back to the default ns again or use the fully qualified
#kubectl command if just for one command (default ns is default :-))
export NS=default
```

</p>
</details>

- be sure to learn basic vi and adjust the ~/.vimrc to accommodate what is
  needed for yaml manipulation

```shell
# edit the resource
vi ~/.vimrc
# remove everything in there
2000dd
# Add the following
set ts=2 sts=2 sw=2 et
# https://stackoverflow.com/questions/1878974/redefine-tab-as-4-spaces
# tabstop=2
# softtabstop=2
# shiftwidth=2
# expandtab (makes them into spaces)
```

- replace tabs with spaces in vi (important for copy paste actions)

```shell
# while in the vi editor in command mode
:%s/\t/  /g
#      ^^ are two spaces
#search for tabs and replace them with two spaces
```

## kubernetes.io bookmarks

For the certification you are allowed to have the kubernetes docs open in an
extra tab in your browser. It is very advisable to create shortcuts for every
topic.

- [here](k8s_favorites.html) are the ones I used.

## Other resources

- [Home k8s cluster](http://ivo2u.nl/Z7)
- [CKAD-exercises by dgkanatsios](https://github.com/dgkanatsios/CKAD-exercises)
- [CKAD-resources by lucassha](https://github.com/lucassha/CKAD-resources)
- [ckad-prep-nodes by twajr](https://github.com/twajr/ckad-prep-notes)
- [My CKAD exam experience by Atharva Chauthaiwale](https://www.linkedin.com/pulse/my-ckad-exam-experience-atharva-chauthaiwale/)
- [Udemy](https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/)
- [Certified Kubernetes Application Developer (CKAD) Learnings & Tips](https://medium.com/marcus-tee-anytime/certified-kubernetes-application-developer-ckad-learnings-tips-cc83c12ed555)
- [Practice Enough With These 150 Questions for the CKAD Exam](https://medium.com/bb-tutorials-and-thoughts/practice-enough-with-these-questions-for-the-ckad-exam-2f42d1228552)
- [How I successfully cleared Certified Kubernetes Application Developer CKAD...](https://qainsights.com/how-i-successfully-cleared-certified-kubernetes-application-developer-ckad-exam-in-5-weeks/)
- [LF - Important instructions](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)
- [cncf - curriculum](https://github.com/cncf/curriculum)
- [LF - Handbook](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook)

