![Banner Dark Tech](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExamJrdXJlZHgwNGZ1bXQ2b3ZldWl6NXRuZmQ0NjZmOHVsNW1tdG1tciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/EcnAlQcGnZq9y/giphy.gif)

# RootMe | TryHackMe Write-up

## 📌 Overview

Este repositório documenta minha resolução da máquina **RootMe** da plataforma TryHackMe, marcando a conclusão do meu primeiro CTF (Capture The Flag).

O objetivo deste laboratório foi praticar conceitos fundamentais de Pentest Web e Linux, incluindo:

* Reconhecimento e enumeração
* Descoberta de diretórios ocultos
* Análise de aplicação web
* Upload de arquivos
* Execução de código
* Enumeração local
* Escalação de privilégios
* Captura de flags

> Este relatório tem caráter educacional e documenta o processo de aprendizagem realizado em ambiente controlado.

---

# 🎯 Objetivos

* Identificar superfícies de ataque da aplicação web.
* Obter execução de código através da funcionalidade de upload.
* Enumerar o sistema comprometido.
* Encontrar a User Flag.
* Realizar escalada de privilégios.
* Obter acesso administrativo e concluir o desafio.

---

# 🛠️ Ferramentas Utilizadas

* Nmap
* DIRB
* OpenVPN
* Linux Terminal
* PHP
* Netcat
* Navegador Web
* Kali Linux

---

# 🔍 Fase 1 - Reconhecimento

Inicialmente foi realizada a enumeração da máquina para identificar serviços expostos.

### Portas Descobertas

| Porta | Serviço |
| ----- | ------- |
| 22    | SSH     |
| 80    | HTTP    |

A presença do serviço HTTP indicou que a aplicação web seria o principal vetor de investigação.

---

# 🌐 Fase 2 - Enumeração Web

Foi realizada enumeração de diretórios utilizando wordlists.

### Diretórios Encontrados

* `/css`
* `/js`
* `/panel`
* `/uploads`

O diretório `/panel` revelou uma funcionalidade de upload de arquivos.

---

# 📤 Fase 3 - Análise do Upload

Durante os testes foram observadas restrições relacionadas à extensão dos arquivos enviados.

### Comportamento observado

Extensões bloqueadas:

* `.php`

Extensões aceitas:

* `.phtml`
* `.php5`
* outras extensões não filtradas

A validação implementada na aplicação era insuficiente e permitia o envio de arquivos executáveis utilizando extensões alternativas.

---

# ⚙️ Fase 4 - Execução de Código

Após o upload de arquivos PHP utilizando extensões permitidas, foi possível confirmar a execução de código no servidor.

Durante essa etapa foram realizadas atividades de enumeração local para compreender:

* Usuário em execução
* Estrutura do sistema
* Diretórios acessíveis
* Arquivos da aplicação

---

# 🧠 Fase 5 - Enumeração Local

A enumeração permitiu identificar:

### Usuário da aplicação

```text
www-data
```

### Usuários locais

```text
rootme
test
ubuntu
```

Também foram analisados:

* Arquivos da aplicação
* Estrutura web
* Diretórios dos usuários
* Configurações relevantes

---

# 📦 Fase 6 - Análise do Código-Fonte

Foi identificado um arquivo compactado contendo artefatos da aplicação.

A análise do código permitiu compreender:

* Como funcionava o filtro de upload.
* Quais extensões eram bloqueadas.
* Como o mecanismo de envio de arquivos havia sido implementado.

Essa etapa foi fundamental para validar o raciocínio utilizado durante a exploração.

---

# 🚩 Fase 7 - Captura da User Flag

Após a enumeração do sistema foi possível localizar a User Flag.

Essa etapa validou o acesso obtido através da exploração da aplicação.

---

# 🔐 Fase 8 - Escalação de Privilégios

Foi realizada enumeração de binários com permissões especiais (SUID).

A análise dos resultados revelou um caminho para elevação de privilégios.

Após validação, foi possível obter contexto administrativo.

### Resultado

```text
root
```

---

# 👑 Fase 9 - Root Flag

Com privilégios elevados foi possível concluir a máquina e capturar a flag final.

---

# 📚 Conceitos Aprendidos

Durante a resolução deste laboratório foram praticados:

* Reconhecimento de alvo
* Enumeração de diretórios
* Upload Vulnerabilities
* Bypass de filtros de extensão
* Execução de código em aplicações web
* Enumeração Linux
* Leitura de arquivos locais
* Análise de código-fonte
* Enumeração de permissões
* SUID Binaries
* Privilege Escalation

---

# 💡 Lições Aprendidas

Uma das principais lições deste desafio foi compreender que a enumeração é frequentemente mais importante do que a exploração em si.

Diversas pistas relevantes foram encontradas apenas após análise cuidadosa dos arquivos, diretórios e comportamento da aplicação.

O sucesso na resolução não ocorreu devido a um único comando, mas sim através de um processo contínuo de:

1. Observação
2. Enumeração
3. Formulação de hipóteses
4. Testes
5. Documentação

---

# 🏆 Conclusão

A máquina RootMe representou meu primeiro CTF concluído com sucesso.

Além da obtenção das flags, o laboratório proporcionou experiência prática em metodologias de investigação ofensiva, análise de aplicações web e escalada de privilégios em ambientes Linux.

Este desafio consolidou conceitos fundamentais que servirão de base para estudos mais avançados em Cybersecurity e Pentest.

---

## Author

**Jonas Costa**

Cybersecurity Student | Pentest Enthusiast | Continuous Learner

> "Every flag is a lesson hidden behind a problem."
