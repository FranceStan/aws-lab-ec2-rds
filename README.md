# aws-lab-ec2-rds
Laboratoire AWS basé sur une architecture EC2 - RDS avec VPC, Security Groups et Subnets

Voici un bon fichier `README.md` pour ton repository GitHub, qui met en avant ton laboratoire AWS basé sur l'architecture EC2 et Aurora RDS. Il inclut une présentation du projet, les prérequis, les instructions de déploiement et des captures d’écran.

---

### 📌 **README.md - AWS Lab EC2 & Aurora RDS**  

```md
# 🌩️ AWS Lab - EC2 & Aurora RDS

Ce repository contient un laboratoire AWS mettant en place une architecture simple utilisant **Amazon EC2** et **Amazon Aurora** dans un **VPC** privé/public avec des sous-réseaux et des groupes de sécurité.

---

## 🏗️ **Architecture du projet**
L'architecture mise en place est la suivante :

![Architecture AWS](diagrams/Diagramme_ec2-database-connect.png)

- 🌍 **VPC** : Virtual Private Cloud
- 🌎 **Subnets** :
  - **Public Subnet** : Contient une instance EC2
  - **Private Subnet** : Contient une base de données Amazon Aurora
- 🔒 **Security Groups** :
  - EC2 ne peut être accédé que via SSH depuis l'extérieur.
  - Aurora RDS n'est accessible que depuis l'instance EC2.

---

## ⚙️ **Pré-requis**
Avant de commencer, assurez-vous d’avoir :
- Un compte **AWS** valide
- AWS CLI installé : [Documentation](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- Terraform (si utilisé) : [Télécharger Terraform](https://www.terraform.io/downloads.html)
- Git installé sur votre machine : [Installer Git](https://git-scm.com/downloads)

---

## 🚀 **Déploiement de l’Infrastructure**
### 1️⃣ **Cloner ce repository**
```bash
git clone https://github.com/TON-NOM-D-UTILISATEUR/aws-lab-ec2-rds.git
cd aws-lab-ec2-rds
```

### 2️⃣ **Créer un VPC avec des sous-réseaux**
Si Terraform est utilisé :
```bash
terraform init
terraform apply
```

Si manuel :
1. Créer un VPC dans AWS.
2. Ajouter deux sous-réseaux (public et privé).
3. Configurer un Internet Gateway et une Route Table.
4. Associer l’EC2 au sous-réseau public et Aurora au sous-réseau privé.

### 3️⃣ **Lancer une instance EC2**
```bash
aws ec2 run-instances --image-id ami-xxxxxxxx --count 1 --instance-type t2.micro \
  --key-name my-key --security-group-ids sg-xxxxxx --subnet-id subnet-xxxxx
```

### 4️⃣ **Créer une base de données Aurora**
```bash
aws rds create-db-cluster --db-cluster-identifier my-cluster --engine aurora \
  --master-username admin --master-user-password mypassword \
  --vpc-security-group-ids sg-xxxxxx
```

---

## 🔗 **Ressources**
- [AWS EC2](https://aws.amazon.com/ec2/)
- [Amazon Aurora](https://aws.amazon.com/rds/aurora/)
- [AWS VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)

🚀 **N’hésitez pas à contribuer ou à poser des questions !** 😃
```

---

