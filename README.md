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
- [Kubernetes for Developers (LFD259) with practice tests at Udemy](https://www.udemy.com/course/certified-kubernetes-application-developer/)
  A very nice video based course with a kodekloud exercise place.

## Tips and tricks

- Practice for speed! Speed is what you need...
- Use commands as much as possible (dry-run) to save time.
- basic stuff from memory like volume mounts (emptyDir / persistentVolumeClaim)
- Apply the context command provided at every question!
- Read carefully
- To save time you can use variables and aliases to make commands easier and
  faster to type:

```shell
# Create and source the kubectl autocomplete script
source <(kubectl completion bash)
#setting the namespace (just do this one again for another namespace if needed)
export NS=default
# You will do dry runs often and now you can just type $DR in stead of the whole thing
export DR='--dry-run=client -o yaml'
# use k to run the kubectl command in the exported namespace. Saves typing
alias k='kubectl -n $NS'
# Now get code completion on the 'k' commands
complete -F __start_kubectl k
```

- These commands are also on the allowed [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) 
  if you want to cut and paste them.
- if you want to do a dry-run you can now just add `$DR` to your command...
  saves a lot of typing.
- I forgot the first command (`source <(kubectl completion bash)`) assuming it
  was already there and that hindered me quite a bit as I got error messages on
  cli completion.
    - the assumption stemmed from KodeKloud and KataCode where it was already
      sourced in.
    - Don't assume :-)
- by just changing `DR=db` you are now running on that namespace
    - Remember to change this back!!!
    - Don't do this if you do not feel comfortable with it... practice

So...

<details><summary>Show</summary>
<p>

```shell
# if you want a dry-run to get the yaml
k run nginx --image=nginx --port 80 $DR >nginx.yml

# doing commands on another namespace
export NS=others
#use 'k'  as you would normally
#don't forget to go back to the default ns again or use the fully qualified
#kubectl command if just for one command (default ns is default :-))
export NS=default
```

</p>
</details>

- be sure to learn basic vi and adjust the ~/.vimrc to accommodate what is
  needed for yaml manipulation

```shell
echo 'set ts=2 sts=2 sw=2 et'>~/.vimrc
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

# Proctor stuff

Stuff I had a bit of trouble with to show the proctor.

- Showing my walls and stuff because my laptop has only short lines to monitors and power and 
  streaming gets lost when decoupled... stressful.
- I had an error on creating a service and that took too long to fix
- not having code completion on tab broke my concentration
    - this was because I had assumed `source <(kubectl completion bash)` had already been provided therefore I had no completion when gave the `complete -F __start_kubectl k` command. It gave an error
    - every time I used `tab` to complete I received an error, and I had to type everything myself which I was not used to.
    - easily fixed by going to the allowed [kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) but forgotten by me at the moment of exam.

# Certification day preparation checklist

- Passport / Second ID
- Go to the restroom
- Clear browser history
- Phone on do not disturb and put it away
- Bottle of clear water (without label)
- Cabled internet or very reliable WiFi
- Clean desktop of everything except keyboard and mouse
- Close all applications except chrome
    - Check in the task manager (cmd+option+esc on macOS)
    - Don't forget applications like 'Alfred, docker, Dropbox, NordVPN' and
      other background / Cloud applications
- Stop notifications on your computer (Do Not Disturb)
- Charge your keyboard / mouse before the exam
- Stop unwanted browser extensions for the duration of the exam
- Make sure you can show all walls and your desktop with your webcam 
  without having to decouple from internet.
- Have the exam page ready
    - have the pre-checks been done?

## kubernetes.io Bookmarks / Favorites

For the certification you are allowed to have the kubernetes docs open in an
extra tab in your browser. It is very advisable to create shortcuts for every
topic.

- [here](k8s_favorites.html) are the ones I used.

You can import them into the browser by:

- `Opening Chrome` > `Bookmarks` > `Bookmarks Manager`
- Click on the three dots in the upper right corner and choose `Import bookmarks`
- navigate to the `k8s_favorites.html` from this project and import them
- they will appear in the `Imported` folder of your bookmarks bar.
- I sorted them on topic.
- Reorganise as needed :-)

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

# Exercises

below some exercises not in the exam style but to give you practice in speed and
agility. These are challenges I gave myself to practice. I tried to make them
more challenging as I went along and to time myself.

## Exercise 01: Create a database setup with admin panel

- give node worker1 the label `db=allow`
- Create a persistent volume with access mode `ReadWriteMany` in the home folder
  of your user called `mysql-data` with 200Mi space
- In the `db` namespace do:
    - Create a volume claim for the same amount called `mysql-pvc` claiming
      persistent volume `mysql-data`
    - Configure a secret called `db-secret` containing MYSQL_ROOT_PASSWORD with
      value `s3cr3t`
    - Create a multi-container pod with a mysql and a phpmyadmin image
        - mysql:
            - env: called 'MYSQL_ROOT_PASSWORD' bound the `db-secret`
            - port: 3306
            - image: ivonet/mysql:5.7.29
            - mount the persistent volume claim called `mysql-pvc`
              on `/var/lib/mysql`
              and subPath `dbdata`
            - this pod must only be deployed on a node with the label `db=allow`
        - phpmyadmin:
            - image: phpmyadmin
            - environment variables
                - PMA_HOST = \<the name of the mysql image>
                - PMA_PORT = \<the port of the mysql image>
                - MYSQL_ROOT_PASSWORD = \<the value of the secret
                  called `db-secret`>
                - port: 80
        - expose the phpmyadmin port to outside the cluster on port 32000
- Prove that it works by going to a browser tab an going to the http:
  //\<your_cluster_ip here>:32000 and log in with the credentials `root`
  and password `s3cr3t`
  ![](img/phpmyadmin.png)

<details><summary>Solution - cli</summary>
<p>

```shell
source <(kubectl completion bash)
export DR='--dry-run=client -o yaml'
export NS=default
alias k='kubectl -n $NS'
complete -F __start_kubectl k

# label node worker1
k label nodes worker1 db=allow
# create the needed folder on the needed worker (worker1)
# I assume you are using my vagrant setup
ssh 192.168.10.111 
mkdir mysql-data
exit
```

-
Create [PersistentVolume](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolume) (
copy example)

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: task-pv-volume
  labels:
    type: local
spec:
  storageClassName: manual
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

- change it to:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv
  labels:
    pv: mysql-pv
spec:
  storageClassName: manual
  capacity:
    storage: 200Mi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: "/home/vagrant/mysql-data"
```

```shell
# a PersistentVolume is not bound to a contect
k create -f pv.yml
#or if aliased
kc pv.yml 
# create namespace db
k create ns db
# set ns to db
export NS=db
# Create a PVC
# https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims
```

- change the `pvc.yml` to:

```shell
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pvc
  namespace: db
spec:
  accessModes:
    - ReadWriteMany
  volumeMode: Filesystem
  resources:
    requests:
      storage: 200Mi
  storageClassName: manual
  selector:
    matchLabels:
      pv: mysql-pv
```

- the `namespace` is not needed as you will be creating it within the namespace

```shell
kc pvc.yml
# check if bound
k get pv,pvc
NAME                        CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM          STORAGECLASS   REASON   AGE
persistentvolume/mysql-pv   200Mi      RWX            Retain           Bound    db/mysql-pvc   manual                  3m51s

NAME                              STATUS   VOLUME     CAPACITY   ACCESS MODES   STORAGECLASS   AGE
persistentvolumeclaim/mysql-pvc   Bound    mysql-pv   200Mi      RWX            manual         3m51s

# Create the secret
k create secret generic db-secret --from-literal=MYSQL_ROOT_PASSWORD=s3cr3t
# check
k get secret db-secret -o yaml
# or more specific
k get secret db-secret -o jsonpath='{.data}{"\n"}'
{"MYSQL_ROOT_PASSWORD":"czNjcjN0"} 

# create the base yaml for the multi pod
k run mysql --image=ivonet/mysql:5.7.29 --port 3306 --env=MYSQL_ROOT_PASSWORD=todo $DR>db.yml
# then env part needs to be changed to the secret
# https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables (copy paste)
# the phpmyadmin needs to be added etc
# edit it mysql.yml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: mysql
  name: mysql
  namespace: db
spec:
  affinity: # Add the node affinity db=allow
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: db
                operator: In
                values:
                  - allow
  containers:
    - name: mysql-pod
      image: ivonet/mysql:5.7.29
      ports:
        - containerPort: 3306
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom: # Change the 'value: todo' to these lines (https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
      imagePullPolicy: IfNotPresent # I added this because I got blocked after pulling to much by docker
      volumeMounts:
        - name: db-data
          mountPath: /var/lib/mysql
          subPath: dbdata
      resources: { }
    - name: phpmyadmin-pod # add this whole part based on the former part with
      image: phpmyadmin
      ports:
        - containerPort: 80
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
        - name: PMA_HOST
          value: mysql  # note that the host here must be the same as the .metadata.name
        - name: PMA_PORT
          value: "3306"
  restartPolicy: OnFailure
  volumes: # assign the pvc
    - name: db-data
      persistentVolumeClaim:
        claimName: mysql-pvc
```

```shell
# create it
kc db.yml
# check it
k describe po mysql
# and
k get po
NAME    READY   STATUS    RESTARTS   AGE
mysql   2/2     Running   0          5m36s
# expose it in a service
kdr expose pod mysql  --port 80 --type=NodePort >svc.yml
# change it to...
```

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: null
  labels:
    run: mysql
  name: mysql
  namespace: db
spec:
  ports:
    - port: 80
      protocol: TCP
      nodePort: 32000
  selector:
    run: mysql
  type: NodePort
status:
  loadBalancer: { }
```

- `curl -q http://192.168.10.100:32000` should give a html result.
- try it in the browser and log in with the given creds...

</p>
</details>

<details><summary>Solution - mostly yaml</summary>
<p>

```shell
# label node worker1
kubectl label nodes worker1 db=allow

# create the needed folder on the needed worker (worker1)
# I assume you are using my vagrant setup
ssh 192.168.10.111  #worker1
mkdir mysql-data
exit


```

- mysql-setup.yml:

```yaml
---
apiVersion: v1
kind: Namespace
metadata:
  name: db
  namespace: default
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: mysql-pv
  labels:
    pv: mysql-pv
spec:
  storageClassName: manual
  capacity:
    storage: 200Mi
  accessModes:
    - ReadWriteMany
  hostPath:
    path: "/home/vagrant/mysql-data"
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mysql-pvc
  namespace: db
spec:
  accessModes:
    - ReadWriteMany
  volumeMode: Filesystem
  resources:
    requests:
      storage: 200Mi
  storageClassName: manual
  selector:
    matchLabels:
      pv: mysql-pv
---
apiVersion: v1
kind: Secret
data:
  MYSQL_ROOT_PASSWORD: czNjcjN0
metadata:
  name: db-secret
  namespace: db
type: Opaque
---
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: mysql
  name: mysql
  namespace: db
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: db
                operator: In
                values:
                  - allow
  containers:
    - name: mysql-pod
      image: ivonet/mysql:5.7.29
      ports:
        - containerPort: 3306
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
      imagePullPolicy: IfNotPresent
      volumeMounts:
        - name: db-data
          mountPath: /var/lib/mysql
          subPath: dbdata
      resources: { }
    - name: phpmyadmin-pod
      image: phpmyadmin
      ports:
        - containerPort: 80
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
        - name: PMA_HOST
          value: mysql
        - name: PMA_PORT
          value: "3306"
  restartPolicy: OnFailure
  volumes:
    - name: db-data
      persistentVolumeClaim:
        claimName: mysql-pvc
---
apiVersion: v1
kind: Service
metadata:
  labels:
    run: mysql
  name: mysql
  namespace: db
spec:
  ports:
    - port: 80
      protocol: TCP
      nodePort: 32000
  selector:
    run: mysql
  type: NodePort
```

```shell
# Get it working
kubectl create -f mysql-setup.yml
curl http://192.168.10.100:32000

```

- try it in the browser and log in with the given creds...

</p>
</details>

## Exercise 02: change 01 by...

- changing the master node so that it also can schedule pods
- extracting the multipod to two single pods
- making sure the phpmyadmin will only be deployed on a node that has label
  `handles=stateless`
- label master to handle stateless applications
- fix all errors
- don't let the phpmyadmin become ready until mysql can be found on 3306

<details><summary>Show</summary>
<p>

```shell
#allow pods on master
kubectl taint node master node-role.kubernetes.io/master-
# label it
kubectl label node master handles=stateless
# Delete the old service
kubectl -n db delete svc mysql
# expose the mysql pod to the phpmyadmin pod
kubectl expose pod mysql --port 3306 --name=mysql-service --namespace=db
# change the old svc.yml
```

```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    run: phpmyadmin
  name: phpmyadmin-service
  namespace: db
spec:
  ports:
    - port: 80
      protocol: TCP
      nodePort: 32000
  selector:
    run: phpmyadmin
  type: NodePort
```

```shell
#create the service
kubectl -n db create -f svc.yml
# create a barebones pod def for phpmyadmin
kubectl -n db run phpmyadmin --image=phpmyadmin --port=80 --dry-run=client -o yaml>php.yml
# Now copy the container part for phpmyadin from from db.yml to php.yml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: phpmyadmin
  name: phpmyadmin
  namespace: db
spec:
  affinity: # only on nodes that handle stateless
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: handles
                operator: In
                values:
                  - stateless
  containers: # replaced with data from the db.yml
    - name: phpmyadmin-pod
      image: phpmyadmin
      ports:
        - containerPort: 80
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
        - name: PMA_HOST
          value: mysql-service # note this host needs to change to the mysql-service as it is not in the same pod anymore
        - name: PMA_PORT
          value: "3306"
      imagePullPolicy: IfNotPresent
  initContainers: # Used an initContainer for the readiness check as the nc command is not available in the phpmyadmin image
    - name: init-mysql
      image: busybox
      command: [ 'sh', '-c', 'until nc -zvw3 mysql-service 3306; do echo waiting for mysql; sleep 2; done;' ]
      imagePullPolicy: IfNotPresent
  restartPolicy: OnFailure
  volumes:
    - name: db-data
      persistentVolumeClaim:
        claimName: mysql-pvc
```

Details initContainer command:

- nc: It???s a command.
- z: zero-I/O mode (used for scanning).
- v: For verbose.
- w3: timeout wait seconds
- mysql-service: Destination system dns
- 3306: Port number needs to be verified.

```shell
# first delete the old setup of the multipod
kubectl -n db delete -f db.yml
# now create the php
kubectl -n db create -f php.yml
#it should stay in the init state
# see logs if the initContainer
kubectl -n db logs phpmyadmin -c init-mysql
waiting for mysql
waiting for mysql
waiting for mysql
waiting for mysql
```

```shell
# Remove the phpadminb part from db.yml
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    run: mysql
  name: mysql
  namespace: db
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
          - matchExpressions:
              - key: db
                operator: In
                values:
                  - allow
  containers:
    - name: mysql-pod
      image: ivonet/mysql:5.7.29
      ports:
        - containerPort: 3306
      env:
        - name: MYSQL_ROOT_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: MYSQL_ROOT_PASSWORD
      imagePullPolicy: IfNotPresent
      volumeMounts:
        - name: db-data
          mountPath: /var/lib/mysql
          subPath: dbdata
  restartPolicy: OnFailure
  volumes:
    - name: db-data
      persistentVolumeClaim:
        claimName: mysql-pvc
```

```shell
kubectl -n db create -f db.yml
kubectl -n db get po,svc -o wide
# both containers should become READY
NAME             READY   STATUS    RESTARTS   AGE     IP                NODE      NOMINATED NODE   READINESS GATES
pod/mysql        1/1     Running   0          2m12s   192.168.235.129   worker1   <none>           <none>
pod/phpmyadmin   1/1     Running   0          6m57s   192.168.219.76    master    <none>           <none>

NAME                         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE   SELECTOR
service/mysql-service        ClusterIP   10.97.164.232    <none>        3306/TCP       63m   run=mysql
service/phpmyadmin-service   NodePort    10.102.219.202   <none>        80:32000/TCP   72m   run=phpmyadmin
# phpmyadmin is running on master (handles=stateless label)
# db is running on worker1 (db=allow label)
#done
```

- check in browser: http://192.168.10.100:32000 USR:root PWD:s3cr3t

</p>
</details>

