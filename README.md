# 🛡️ Simulação de Ataques de Força Bruta com Medusa e Kali Linux

## 📝 Descrição do Projeto
Este projeto prático faz parte do desafio da DIO e tem como objetivo demonstrar a compreensão sobre ataques de Força Bruta e testes de autenticação. Utilizando o **Kali Linux** e a ferramenta **Medusa**, foram simulados ataques contra um ambiente vulnerável controlado (Metasploitable 2 e DVWA) para fins educacionais e de auditoria de segurança.

Os testes englobam conceitos como Ataque de Dicionário e Password Spraying, focando na identificação de credenciais fracas em diferentes protocolos.

## 🛠️ Tecnologias e Ferramentas Utilizadas
*   **Sistema Operacional Atacante:** Kali Linux
*   **Sistema Operacional Alvo:** Metasploitable 2 (Ambiente Controlado)
*   **Ferramentas:** Medusa, Nmap
*   **Virtualização:** VirtualBox (Rede Host-only)

## 🚀 Execução do Laboratório

### 1. Preparação (Wordlists)
Foram criadas wordlists personalizadas (Ataque de Dicionário) para simular o ataque:
*   `users.txt` (ex: admin, root, msfadmin)
*   `passwords.txt` (ex: admin, password, 123456, msfadmin)

### 2. Cenário 1: Ataque de Força Bruta em FTP
Utilizando o Medusa, foi realizado um ataque de dicionário no serviço FTP do alvo.
*   **Comando utilizado:** 
    `medusa -h <IP_ALVO> -U users.txt -P passwords.txt -M ftp`
*   **Resultado:** O serviço Medusa testou as combinações e encontrou as credenciais válidas com sucesso (ex: msfadmin:msfadmin).

### 3. Cenário 2: Password Spraying em SMB
O Password Spraying consiste em testar poucas senhas comuns em muitos usuários para evitar bloqueio de contas.
*   **Comando utilizado:** 
    `medusa -h <IP_ALVO> -u msfadmin -P passwords.txt -M smbnt`
*   **Resultado:** Foi possível validar o acesso ao serviço SMB.

*(Opcional: Adicione capturas de tela dos terminais na pasta `/images` do repositório e insira elas aqui usando a sintaxe `![Descrição da imagem](/images/foto.png)`)*

## 🛡️ Vulnerabilidades Encontradas e Mitigação
Durante os testes, ficou evidente que serviços expostos com senhas fracas ou padrão são facilmente comprometidos.

**Recomendações de Mitigação (Prevenção):**
1.  **Políticas de Senhas Fortes:** Exigir senhas complexas (letras, números e caracteres especiais) e tamanho mínimo adequado.
2.  **Bloqueio de Contas (Account Lockout):** Implementar o bloqueio temporário da conta após "X" tentativas falhas de login para mitigar Força Bruta Pura e Dicionário.
3.  **Múltiplos Fatores de Autenticação (MFA):** Adicionar uma camada extra de segurança além da senha.
4.  **Monitoramento e Alertas:** Configurar logs para alertar sobre múltiplas tentativas de falha de login no FTP e SMB.

## 📚 Aprendizados
Este desafio permitiu consolidar na prática os conceitos teóricos de auditoria de senhas, entendendo como cibercriminosos operam ataques de permutação e dicionário, e qual a importância de configurar corretamente os serviços de rede.

---
*Desafio realizado para a plataforma DIO.*
