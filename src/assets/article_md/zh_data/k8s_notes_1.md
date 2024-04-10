# Kubernetes 筆記
> *Kubernetes，因開頭字母"k"到結尾"s"之間有8個字，又可稱作 k8s*
## 前言
k8s 可以管理多個容器的自動化部屬工具，主要功能如下
* 同時部署多個容器到多台機器上（Deployment）
* 服務的乘載量有變化時，可以對容器做自動擴展（Scaling）
* 管理多個容器的狀態，自動偵測並重啟故障的容器（Management）

## 架構
### K8S
* 以下為 k8s 的四個元件，由小到大介紹
* ### Pod
    * k8s 中最小單位
    * 一個 pod 通常對應一個 container ， 但也可以多個 container
    * 每個 pod 對應一個 yaml 檔
* ### Worker Node
    * 對應一台 server (硬體設備)
    * 每個 node 之中有三個元件
        * ### kubelet
            * 管理 pods 並負責對外與 master node 溝通
        * ### kube-proxy
            * 藉由更新 iptables ，讓流量可以正確被傳送到 Pod 上的元件
            * iptables 是 Linux 上的防火牆(firewall)，不只限制哪些連線可以連進來，也會管理網路連線，決定收到的 request 要交給哪個 Pod
        * ### Container Runtime
            * 真正負責 container 執行的元件
* ### Master Node
    * 一個專門管理其他 worker node 的 node
    * 每個 master node 之中有四個元件
    * ### kube-apiserver
        * nodes 之間的溝通
        * 身份認證與授權
    * ### etcd
        * 備份資料
    * ### kube-controller-manager
        * 負責管理 controllers 的元件
        * controller 是負責監視 Cluster 狀態的 Process
    * ### kube-scheduler
        * 判斷哪個 node 適合分配給當前開啟的 pods
* ### Cluster
    * k8s 中多組 "前三個元件" 的集合

## 運作流程
### 創建一個新的 Pod
#### 1. 創建 Pod 的指令送到 kube-apiserver
    1-1. 進行確認使用者身份和權限
    1-2. 把指令備份到 etcd
    1-3. 通知 kube-controller-manager 、 kube-scheduler 、 kubelet
#### 2. kube-controller-manager 會從 kube-apiserver 收到需要創建 Pod 的訊息
    2-1. kube-controller-manager 檢查資源是否許可，並建立 Pod
#### 3. kube-scheduler 會定期詢問 kube-controller-manager 是否有新的 Pod
    3-1. 若有便將 Pod 分配到對應的 Worker Node 上。
#### 4. kubelet 會先收到 master node 指令，創建一個 Pod。
    4-1. kube-proxy 會去更新 iptables，目前該 Pod 可用。
### 使用者發送 Request

#### 1. 使用者發送 requests 時，會先到 Load Balancer 決定要把 request 交給哪個 Node
#### 2. 到 node 之後透過 iptables 決定要送給哪個 Pod
#### 3. 接收的 Node 上沒有可以處理 request 的 Pod，該 Node 會透過 iptables 把 request 轉給其他可以處理這個 request 的 Node

## 進階元件
* ### Service
    * 可設定一群 pods 的規則，方便管理
    * 用 port 來達成 port forward ，連接內外部
    * Node <--> Serivce <--> Pod
* ### Ingress
    * 當 service 增加時，會有很多對內和對外的 port 導致不好管理，使用 ingress 可以統一 service 的 port 號，改為用 path 導向
    * Node <--> Ingress <--> Serivce <--> Pod
* ### Deployments
    * 可以複製和刪除同一個 pod ，目的是為了在 pod 故障或更新版本時透過複製新的 Pod 替代，確保 API 不中斷的繼續服務
    * 可以用於負載平衡
