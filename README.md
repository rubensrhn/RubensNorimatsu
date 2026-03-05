Security Project: Pentest Prático com Kali Linux & Medusa
Este repositório contém a documentação detalhada e os artefatos do desafio prático realizado na plataforma DIO. O objetivo principal é simular ataques de força bruta em ambientes controlados para entender vulnerabilidades e aplicar medidas de mitigação.

🎯 Objetivo do Projeto
Implementar um ambiente de testes de invasão para explorar protocolos comuns (FTP, SMB, HTTP) utilizando a ferramenta Medusa, validando falhas de configuração e senhas fracas em máquinas deliberadamente vulneráveis.

🛠️ Cenário de Laboratório
Para garantir a segurança e o isolamento dos testes, o ambiente foi configurado utilizando virtualização:

Atacante: Kali Linux

Alvos: Metasploitable 2 & DVWA (Damn Vulnerable Web Application)

Rede: Host-Only (Rede Interna) para evitar tráfego externo.

Ferramenta de Ataque: Medusa (Brute-force modular).

🚀 Etapas Executadas
1. Configuração do Ambiente
Instalação das VMs no VirtualBox.

Configuração de adaptadores de rede para comunicação entre as máquinas.

Teste de conectividade via ping e varredura inicial com nmap.

2. Ataques Simulados
Foram realizados três cenários principais de exploração:

Força Bruta em FTP: Tentativas de login automatizadas no serviço de transferência de arquivos.

Automação em Formulário Web (DVWA): Ataque direcionado à interface de login da aplicação web.

Password Spraying em SMB: Enumeração de usuários de rede e teste de senhas comuns para evitar bloqueio de contas.

# 🛡️ Desafio de Projeto: Quebra de Senhas com Força Bruta

Este projeto demonstra a execução de um ataque de força bruta (Brute Force) contra uma aplicação web vulnerável (DVWA) hospedada em um servidor Metasploitable 2.

## 🚀 Tecnologias Utilizadas
* **Kali Linux**: Sistema operacional para testes de intrusão.
* **Metasploitable 2**: Máquina alvo com serviços vulneráveis.
* **Hydra**: Ferramenta utilizada para a quebra de senhas via protocolo HTTP-POST.
* **Curl**: Utilizado para diagnóstico de conectividade e análise de headers HTTP.

## 🛠️ Metodologia e Desafios
Durante o desenvolvimento, foram enfrentados e solucionados os seguintes desafios técnicos:

1. **Instabilidade do Medusa**: A ferramenta Medusa v2.3 apresentou erros 404 intermitentes devido à sensibilidade na formação dos cabeçalhos de Cookie.
2. **Diagnóstico de Endpoint**: Utilizei `curl -s -o /dev/null -w "%{http_code}"` para validar que o caminho `/dvwa/login.php` estava ativo (HTTP 200).
3. **Tratamento de Falsos Positivos**: Identifiquei que a omissão ou erro na string de falha (`F=`) resultava em todas as senhas sendo marcadas como válidas. A solução foi mapear a mensagem real do servidor: "Login failed".

## 📊 Resultado Final
O ataque foi bem-sucedido, identificando a credencial correta após sanitização da wordlist e ajuste dos parâmetros de formulário.

* **Alvo:** 192.168.56.101
* **Usuário:** admin
* **Senha identificada:** password

🛡️ Medidas de Mitigação

Após os testes, foram documentadas as seguintes recomendações:

Políticas de Senhas Fortes: Implementação de complexidade mínima.

Bloqueio de Conta (Account Lockout): Limitar tentativas consecutivas de login.

Desabilitação de Protocolos Inseguros: Substituição de FTP por SFTP/SSH.

2FA (Autenticação de Dois Fatores): Adição de camada extra de segurança em serviços críticos.

⚠️ Aviso Legal (Disclaimer)
Este projeto foi realizado em um ambiente de laboratório controlado para fins estritamente educacionais. Nunca execute ferramentas de varredura ou ataque em redes ou sistemas sem autorização expressa por escrito.

Desenvolvido por [Rubens Norimatsu]
