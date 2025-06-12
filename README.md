# 🕵️‍♂️ n8n-site-monitor

Este projeto utiliza o [n8n](https://n8n.io) (plataforma de automação de workflows) para monitorar mudanças em uma página web e enviar um e-mail de notificação quando houver alterações detectadas.

## 🚀 Funcionalidades

- Faz requisição HTTP para uma página web
- Verifica se houve mudança no conteúdo (ex: título)
- Envia notificação por e-mail em caso de alteração
- Executado automaticamente via agendamento (cron)

---

## 🧰 Tecnologias utilizadas

- [n8n](https://n8n.io/)
- Docker / Docker Compose
- Node `HTTP Request`, `If`, `Email`, etc.

---

## 📦 Como rodar o projeto

1. **Clone este repositório**:
   ```bash
   git clone https://github.com/CauanDZN/site_monitor_n8n.git
   cd site_monitor_n8n
```

2. **Suba os containers com Docker Compose**:

   ```bash
    docker-compose up -d
  ```

3. **Acesse a interface do n8n**:

   ```
   http://localhost:5678
   ```

   Login padrão (você pode mudar no `docker-compose.yml`):

   * **Usuário:** `admin`
   * **Senha:** `admin`

4. **Importe o workflow (caso tenha o arquivo JSON)** ou crie manualmente:

   * HTTP Request → verifica conteúdo da página
   * Set/Function → extrai conteúdo relevante
   * IF → detecta mudança
   * Email → envia alerta

---

## 🛠 Personalização

Você pode personalizar:

* A URL da página a ser monitorada
* O conteúdo que será comparado (ex: título, texto, etc.)
* O tempo entre checagens (ajustando o nó **Cron**)
* O serviço de e-mail (Gmail, SMTP personalizado, etc.)

---

## 🧪 Exemplo de uso

Imagine que você quer ser alertado quando o título do site `https://exemplo.com` mudar. O n8n irá:

1. Acessar o site periodicamente
2. Capturar o título da página
3. Comparar com o valor anterior salvo
4. Enviar um e-mail se o valor estiver diferente