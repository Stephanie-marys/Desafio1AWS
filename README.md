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

![Imagem do projeto](https://viewer.diagrams.net/index.html?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&title=Desafio.drawio&dark=auto#R%3Cmxfile%3E%3Cdiagram%20name%3D%22P%C3%A1gina-1%22%20id%3D%22U74WHLHzAlpzyb5w_HUj%22%3E7VpJc6M4FP41PoYChDAcvaXnkKlJTaZqJqcuxci20oAcIW%2F960dCYhVeOjHdSWbwIdbTQ4j3ve8tigdgkuy%2FMLRe%2FU4jHA9cO9oPwHTgigsC8UdKDkrihJ6vJEtGIi2rBA%2FkO9ZCW0s3JMJZQ5FTGnOybgrnNE3xnDdkiDG6a6otaNx86hotsSF4mKPYlP5NIr5S0sAdVvLfMFmuiic7fqhmElQo6zfJViiiu5oIzAZgwijl6luyn%2BBYWq%2Bwi7rv9shsuTGGU37JDd%2BeH18e%2Fb%2Fsxe3M%2F%2BMleP5yP17cFGbeonij31jvlh8KE4hlhLXFYCxeYS2F85huxKrj3Ypw%2FLBGcyncCQ8QshVPYjFyxFe9NGYc749u2ilNIZwI0wRzdhAq%2BoYboDeo%2Fecm1ONdDYxCtqoBAaEWIu0Ay3LtykbiizbTj5jsvMXohsckxZPSJ21hjQhlKxzpgTQKEV52h55wfE8zwglNxdwT5ZwmNYVRTJZyglNpXKRHc2E%2BzJrWLsBJ9kvJRQvtMmBtabxJJHQLEscTGlOW7xDMbOh6QMiFbkTEasVcSlN8HegcrwldSekadNC1oIndEPYE3dD07UiwXQ8p4yu6pCmKZ5V0zOgmjUrcKp07KhHJLf%2BMOT%2Fo0IU2nDZxWcR0N0qJiAcK4ooZ8uGnjSv2Sjdsjk%2B8k%2FY%2BjtgS83Nua4LFcCw2tm3uo8vw%2BtZ7SsQOS5DDJsYgbLFObUvfVKE3YgwdamprqZAdf4xjt3zJt1vOoFasXKN8xdd7S2AQfZZuCcoTy8uGbGmnN%2BWMbnqAwdo2uRMSRcrZcEa%2Bo6d8Pelu2i5icTgewOkpYuoEqG%2Bu0k7dp46T4iiLbcsD0G0aX41e6zmFCl0sMswHbU5fATj3fIQ%2BG39Rtlahe0H2kv2nIm0mqoVsQQVPrR1%2BqgfbPIhk%2BSpaIvYxKQegPvDqN7oqTNvAjXy7PgH0RBRGEapPeGpikV%2BtgK%2BDesYZ%2FYavH%2BmHTXJCO7TC%2BuUZcd%2FvyNje0PLs%2BuX3lAWA4R6jORcmaftIAfMmiZXCq9N2zXc6S4MrYADcNghmtgVddZJrgb4KJfjx0u0vSqMe6M5v5RKqDDDy6LUipuMbnLgbTMBgNPps2U455Yl0Z4eO16xp3n26%2B4A8O1vWOsMLCamS%2B1sZ%2BaMFqec3nWT4E%2BpR1yTpn9OHz0FL9zQtb2zLgcD%2FYGXoZ2w3L%2Bel3Y1ov7yErYbUha1DsXP6XtA%2FkQsbvqlBqUHeXXSqar84tOwMAefPqTo1uk6aIgut17HYhdzn1wyzbf6E9rHTRH6MVkTMwJn8dDVeNVXdFbmh%2FFynbvZa2d7tqJvD0HL0qW69dC4PJa5fOXccPUxMHxFvzfsL8jK0ZCrKOMeax44m8xqYgMBqxnpgBwYqsKObAb0hEhqITG9mYzP7flZMnFaT7wYmIl1dfW%2BIFKXF%2F%2BfwZ5Dz%2FXd3Dl%2B8RD2%2B%2FafYZGDyy9l0wZnp%2B2ETizKTSu5sCMZBr1SCDigrAY2cZ5Jp6JrABScK3bclpg8FXP6P46%2BuCd4tDCDwegWvC6oujvm9Rb3AQOYn9IPCOuzwjxxYtmg8tOBRLmgBWGpM9%2FoRanSoj%2B4xI8IEEuFc2HOLqQ%2FczneY3XBf3GAeAVMMqx9lqJav%2Bm0LmP0L%3C%2Fdiagram%3E%3C%2Fmxfile%3E#%7B%22pageId%22%3A%22U74WHLHzAlpzyb5w_HUj%22%7D)

