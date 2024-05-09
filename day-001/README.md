# Descomplicando `Kubernetes` - Dia 01

## Criando o _cluster_ com [`kind`][kind]

Para subir o _cluster_ com as [configurações especificadas][kind-config], executaremos:

```bash
kind create cluster --config ./kind-cluster.yml --name dk8s-day-001
```

## _Deploy_ do `pod` aplicando o manifesto

Com o _cluster_ rodando, podemos subir um novo `pod` usando o comando:

```bash
kubectl apply -f pod.yml
```

[Voltar para o `README`][readme]

[kind]: https://kind.sigs.k8s.io/
[kind-config]: ./kind/kind-cluster.yml
[readme]: ../README.md
