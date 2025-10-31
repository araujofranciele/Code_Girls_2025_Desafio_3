# AWS CloudFormation – Laboratório de Primeira Stack

## 📌 Objetivo

O objetivo deste laboratório é **implementar a primeira Stack utilizando AWS CloudFormation**, entendendo os conceitos fundamentais de **infraestrutura como código (IaC)** e praticando a criação de recursos na AWS de forma automatizada.

---

## 📚 Conceitos Aprendidos

Durante a prática, foram explorados os seguintes conceitos:

* **Stack:** Conjunto de recursos AWS que podem ser criados, atualizados e deletados de forma unificada.
* **Template:** Arquivo em **YAML** ou **JSON** que define a infraestrutura desejada.
* **Recursos (Resources):** Componentes da AWS que serão provisionados, como **EC2, S3, IAM roles** etc.
* **Parâmetros (Parameters):** Valores dinâmicos que podem ser passados para o template.
* **Outputs:** Informações úteis sobre os recursos criados, exibidas ao final da criação da Stack.
* **Dependências:** Ordem de criação de recursos, controlada automaticamente pelo CloudFormation.

---

## 🛠️ Ferramentas e Serviços Utilizados

* **AWS CloudFormation:** Serviço principal para criar e gerenciar a Stack.
* **Amazon EC2:** Criar instâncias de máquinas virtuais.
* **Amazon S3:** Armazenamento de arquivos e logs (opcional, dependendo da Stack).
* **AWS CLI:** Para validação e deploy da Stack via terminal (opcional).

---

## 📝 Passo a Passo da Implementação

1. **Criação do template YAML**

   * Definição do `AWSTemplateFormatVersion` e `Description`.
   * Configuração de **Parameters** para flexibilidade do template.
   * Declaração de **Resources** (por exemplo, uma instância EC2 e um Security Group).
   * Configuração de **Outputs** para exibir informações como IP público da instância.

2. **Validação do Template**

   ```bash
   aws cloudformation validate-template --template-body file://meu-template.yaml
   ```

3. **Criação da Stack**

   ```bash
   aws cloudformation create-stack --stack-name MinhaPrimeiraStack --template-body file://meu-template.yaml --parameters ParameterKey=InstanceType,ParameterValue=t2.micro
   ```

4. **Monitoramento da Stack**

   * Acompanhar status de criação pelo console ou CLI.
   * Identificar possíveis erros e ajustar o template conforme necessário.

5. **Visualização de Outputs**

   * Conferir informações dos recursos criados, como IP da EC2.

6. **Atualização da Stack**

   * Modificar template e executar:

   ```bash
   aws cloudformation update-stack --stack-name MinhaPrimeiraStack --template-body file://meu-template.yaml
   ```

7. **Exclusão da Stack**

   * Garantir limpeza de recursos:

   ```bash
   aws cloudformation delete-stack --stack-name MinhaPrimeiraStack
   ```

---

## 💡 Insights e Dicas

* **IaC é poderoso:** Automatiza criação, atualização e remoção de recursos de forma segura.
* **Versionamento de templates:** Manter templates no GitHub facilita colaboração e rastreabilidade.
* **Validação antes do deploy:** Evita erros e provisionamento desnecessário de recursos.
* **Outputs ajudam muito:** Permitem usar informações de recursos em outras Stacks ou scripts.

---

## 📂 Estrutura do Repositório

```
aws-cloudformation-lab/
│
├── meu-template.yaml         # Template da Stack em YAML
├── README.md                 # Este arquivo
└── notas-de-estudo.md        # Anotações e aprendizados adicionais
```

---

Se você quiser, posso **criar já um template YAML de exemplo de CloudFormation** para você colocar no repositório e testar sua primeira Stack na AWS.

Quer que eu faça isso?

