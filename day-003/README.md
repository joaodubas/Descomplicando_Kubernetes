# Descomplicando `kubernetes` - Dia 03

## Criar `namespace`

Podemos criar nosso primeiro `namespace` manualmente, usando o comando:

```bash
kubectl create namespace <namespace-name>
```

Ou, a partir de um manifesto `yaml`:

```bash
kubectl apply -f <namespace-definition>.yml
```

No nosso _cluster_ criaremos o primeiro `namespace` utilizando o arquivo [`namespace.yml`][namespace-config].

## _Deploy_ do `nginx`

Além dos recursos de definição do `pod` vistos nos dias [01][day-001-pod] e
[02][day-002-pod]. Podemos definir detalhes adicionais usando o [`deployment.yml`][deployment-config].

O _deploy_ do `nginx` será feito usando o comando:

```bash
kubectl apply -f deployment.yml
```

Nele definimos o:

1. Número de _replicas_ do serviço
2. Estrategia de _rollout_ do _deploy_
3. Detalhes dos _containers_ a serem executados

[Voltar para o `README`][readme]

[namespace-config]: ./namespace.yml
[day-001-pod]: ../day-001/pod.yml
[day-002-pod]: ../day-002/pod.yml
[deployment-config]: ./deployment.yml
[readme]: ../README.md
