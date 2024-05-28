# Descomplicando `Kubernetes`

## Preparando o ambiente

Para facilitar a instalação dos _softwares_ necessários utilizo o [`mise`][mise] como gestor de ferramentas e _runtimes_.

A instalação do [`mise`][mise] pode ser feita seguindo o [guia de uso][mise-guide].

Com o [`mise`][mise] instalado, executamos o seguinte comando para instalar as ferramentas:

```bash
mise install
```

E, para garantir que tudo esta correto, podemos verificar a instalação rodando:

```bash
mise current
```

O resultado esperado é:

```
kind 0.22.0
kubectl 1.29.4
```

## Curso por dias

* [dia-01][dia-01]: subindo primeiro _cluster_ com [`kind`][kind] e fazendo _deploy_ do primeiro `pod`
* [dia-02][dia-02]: realizando _deploy_ de `pod` com múltiplos _containers_, definição de volume e limitação de recursos
* [dia-03][dia-03]: criando `namespace` e `deployment` em conjunto com estratégias de _rollout_

Pode ser seguido em no 

[mise]: https://mise.jdx.dev/
[mise-guide]: https://mise.jdx.dev/getting-started.html#quickstart
[kind]: https://kind.sigs.k8s.io/
[dia-01]: ./day-001/README.md
[dia-02]: ./day-002/README.md
[dia-03]: ./day-003/README.md
