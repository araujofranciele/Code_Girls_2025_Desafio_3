# Laboratório AWS CloudFormation – Minha Primeira Stack

## 📌 Objetivo

O objetivo deste laboratório é **implementar uma Stack utilizando AWS CloudFormation**, praticando **Infraestrutura como Código (IaC)** e entendendo como automatizar a criação de recursos na AWS.

Nesta Stack, criamos:

* Uma instância **EC2** com Amazon Linux 2
* Um **Security Group** para permitir acesso SSH (porta 22) e HTTP (porta 80)
* Um **Apache Web Server** instalado automaticamente via **User Data**
* Uma **página HTML simples** como teste
* **Outputs** com informações úteis (IP público e ID do Security Group)

---

## 📚 Conceitos Aprendidos

* **Stack:** Conjunto de recursos AWS que podem ser criados, atualizados e deletados juntos.
* **Template:** Arquivo YAML que descreve a infraestrutura desejada.
* **Resources:** Recursos provisionados na AWS (EC2, Security Group, etc.).
* **Parameters:** Permitem definir valores dinâmicos, como tipo de instância e chave SSH.
* **User Data:** Script executado na inicialização da instância para configuração automática.
* **Outputs:** Informações úteis que podem ser utilizadas em outras Stacks ou scripts.

---

## 🛠️ Serviços e Ferramentas Utilizados

* **AWS CloudFormation** – Criação e gerenciamento da Stack
* **Amazon EC2** – Máquina virtual para teste
* **Security Group** – Controle de acesso à instância
* **AWS CLI** – Para validar e executar a Stack (opcional)

---

## 📝 Passo a Passo

1. **Criação do template YAML**
   Salvar o arquivo como `cloudformation-ec2.yaml` (template fornecido no repositório).

2. **Validação do Template**

   ```bash
   aws cloudformation validate-template --template-body file://cloudformation-ec2.yaml
   ```

3. **Criação da Stack**

   ```bash
   aws cloudformation create-stack \
   --stack-name MinhaPrimeiraStack \
   --template-body file://cloudformation-ec2.yaml \
   --parameters ParameterKey=KeyName,ParameterValue=minha-chave-ec2
   ```

4. **Monitoramento da Stack**

   * Acompanhar status pelo console ou via CLI:

   ```bash
   aws cloudformation describe-stacks --stack-name MinhaPrimeiraStack
   ```

5. **Acessando a Instância**

   * Após a criação, utilize o **IP público** (Output `EC2PublicIP`) para acessar a página web criada.
   * Para SSH:

   ```bash
   ssh -i minha-chave-ec2.pem ec2-user@<EC2PublicIP>
   ```

6. **Atualização da Stack**

   * Modificar template e atualizar Stack:

   ```bash
   aws cloudformation update-stack \
   --stack-name MinhaPrimeiraStack \
   --template-body file://cloudformation-ec2.yaml
   ```

7. **Exclusão da Stack**

   * Para limpar recursos:

   ```bash
   aws cloudformation delete-stack --stack-name MinhaPrimeiraStack
   ```

---

## 💡 Insights e Dicas

* **IaC automatiza tudo:** Criação, atualização e exclusão de recursos sem tocar no console.
* **Validação é essencial:** Evita erros e provisionamento de recursos desnecessários.
* **User Data é poderoso:** Permite configurar a instância automaticamente.
* **Outputs ajudam na integração:** Facilita referência de IPs, IDs e outros recursos.
* **Tags organizam recursos:** Úteis para controle e cobrança.

---

## 📂 Estrutura do Repositório

```
aws-cloudformation-lab/
│
├── cloudformation-ec2.yaml   # Template CloudFormation
├── README.md                 # Este arquivo
└── notas-de-estudo.md        # Anotações e insights do laboratório
```
