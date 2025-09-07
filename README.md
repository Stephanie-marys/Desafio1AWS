# Desafio Gerenciando Instâncias EC2 na AWS - Santander Code Girls

## 📌 Visão Geral
Este diagrama representa uma arquitetura de software hospedada na **AWS**, utilizando **EC2**, **EBS** e **RDS**.  
O fluxo ilustra como o usuário interage com a aplicação e como os dados são armazenados e processados na nuvem.

---

## 🏗️ Componentes Principais

- **Actor (Usuário/Cliente)**  
  Responsável por interagir com a aplicação, enviando e recebendo arquivos.

- **EC2 (Elastic Compute Cloud)**  
  Instância de computação responsável por executar a aplicação e processar as requisições dos usuários.

- **D-EBS (Elastic Block Store - Dados)**  
  Volume de armazenamento EBS utilizado para **receber arquivos enviados pelo usuário**.  
  - Armazena dados persistentes.  
  - Pode ser acessado diretamente pela instância EC2 para leitura.

- **E-EBS (Elastic Block Store - Execução/Aplicação)**  
  Volume EBS adicional anexado ao EC2, usado para **armazenar dados da aplicação ou logs de execução**.

- **RDS (Relational Database Service)**  
  Serviço gerenciado de banco de dados relacional da AWS.  
  - Conectado ao EC2 para persistência estruturada de dados.  
  - Fornece alta disponibilidade e backup automático.

---

## 🔄 Fluxo de Funcionamento

1. O **usuário (Actor)** envia um arquivo pela aplicação.  
2. O arquivo é gravado no volume **D-EBS**.  
3. A instância **EC2** processa os dados:  
   - Pode ler diretamente do **D-EBS**.  
   - Pode gravar ou recuperar informações no banco de dados **RDS**.  
   - Pode salvar logs ou dados adicionais no volume **E-EBS**.  
4. O usuário recebe a resposta após o processamento.  

---

## ✅ Benefícios da Arquitetura
- **Escalabilidade**: EC2 pode ser redimensionado conforme a demanda.  
- **Persistência de dados**: volumes EBS garantem que dados não sejam perdidos mesmo após reinício do EC2.  
- **Gerenciamento simplificado**: RDS oferece backups automáticos, replicação e segurança integrada.  
- **Flexibilidade**: separação de volumes EBS para diferentes propósitos (dados x aplicação).  

<img width="1297" height="774" alt="image" src="https://github.com/user-attachments/assets/08137a06-14cc-4200-a5cf-1d7cee47449e" />

