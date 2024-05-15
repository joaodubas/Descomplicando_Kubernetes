# Descomplicando `Kubernetes` - Dia 02

## _Deploy_ do `pod`

Inicialmente precisamos subir o _cluster_ com [`kind`][kind], seguindo as instruções do [dia-01][dia-01].

Com o _cluster_ rodando, podemos fazer o _deploy_ do nosso `pod` usando o comando:

```bash
kubectl apply -f pod.yml
```

Veja os detalhes do `pod` criado usando o comando:

```bash
kubectl describe pods
```

No resultado precisamos garantir que:

1. Os _containers_ `nginx`, `echo` e `shell` existam
2. Limites de recursos existam
3. O _container_ `nginx` tenha um novo volume no caminho `/opt/nginx`

<details>
<summary>Esse é um exemplo do resultado gerado</summary>

```
Name:             podsmania
Namespace:        default
Priority:         0
Service Account:  default
Node:             dk8s-day-001-worker/172.21.0.4
Start Time:       Wed, 15 May 2024 20:46:58 +0000
Labels:           run=podsmania
                  service=webserver
Annotations:      <none>
Status:           Running
IP:               10.244.2.7
IPs:
  IP:  10.244.2.7
Containers:
  nginx:
    Container ID:   containerd://88dc17958d8239662a337239b354d54e93e83e085fec6314509810b83b8ac7f5
    Image:          nginx
    Image ID:       docker.io/library/nginx@sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Wed, 15 May 2024 20:47:00 +0000
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     500m
      memory:  128Mi
    Requests:
      cpu:        300m
      memory:     96Mi
    Environment:  <none>
    Mounts:
      /opt/nginx from custom-nginx-opt (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-6s7g9 (ro)
  echo:
    Container ID:   containerd://6160153c3a075864a8cbbd54a0d9544c87ae1e9b75f2282919422e65f2e7113a
    Image:          ealen/echo-server
    Image ID:       docker.io/ealen/echo-server@sha256:ec8a6e95890df937a1eb5fafca033a32172d4f43c1fea1f302931d5f230a137f
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Wed, 15 May 2024 20:47:02 +0000
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     500m
      memory:  128Mi
    Requests:
      cpu:     250m
      memory:  96Mi
    Environment:
      PORT:  3000
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-6s7g9 (ro)
  shell:
    Container ID:  containerd://5bccc9905d38438ee05954cdb2e7283dfdb6e1a95ce7c260740887a13ee1ef64
    Image:         ubuntu
    Image ID:      docker.io/library/ubuntu@sha256:3f85b7caad41a95462cf5b787d8a04604c8262cdcdf9a472b8c52ef83375fe15
    Port:          <none>
    Host Port:     <none>
    Args:
      sleep
      infinity
    State:          Running
      Started:      Wed, 15 May 2024 20:47:04 +0000
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     250m
      memory:  96Mi
    Requests:
      cpu:        100m
      memory:     32Mi
    Environment:  <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-6s7g9 (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   True
  Initialized                 True
  Ready                       True
  ContainersReady             True
  PodScheduled                True
Volumes:
  custom-nginx-opt:
    Type:       EmptyDir (a temporary directory that shares a pod's lifetime)
    Medium:
    SizeLimit:  256Mi
  kube-api-access-6s7g9:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   Burstable
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type    Reason     Age   From               Message
  ----    ------     ----  ----               -------
  Normal  Scheduled  18m   default-scheduler  Successfully assigned default/podsmania to dk8s-day-001-worker
  Normal  Pulling    18m   kubelet            Pulling image "nginx"
  Normal  Pulled     18m   kubelet            Successfully pulled image "nginx" in 1.481s (1.481s including waiting)
  Normal  Created    18m   kubelet            Created container nginx
  Normal  Started    18m   kubelet            Started container nginx
  Normal  Pulling    18m   kubelet            Pulling image "ealen/echo-server"
  Normal  Pulled     18m   kubelet            Successfully pulled image "ealen/echo-server" in 1.86s (1.86s including waiting)
  Normal  Created    18m   kubelet            Created container echo
  Normal  Started    18m   kubelet            Started container echo
  Normal  Pulling    18m   kubelet            Pulling image "ubuntu"
  Normal  Pulled     18m   kubelet            Successfully pulled image "ubuntu" in 1.597s (1.597s including waiting)
  Normal  Created    18m   kubelet            Created container shell
  Normal  Started    18m   kubelet            Started container shell
```
</details>

### Limpando o _deploy_

Para remover o `pod` criado, executamos o comando:

```bash
kubectl delete -f pod.yml
```

[kind]: https://kind.sigs.k8s.io/
[dia-01]: ./day-001/README.md
