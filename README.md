# OS por Foto v2 — Atlântica-PI

App de celular para abrir OS a partir de fotos e de relato por voz.

- **Gemini (gratuito):** analisa as fotos e transcreve o áudio.
- **Offline:** as fotos, o áudio e a OS ficam guardados no celular e sobem quando a internet voltar.
- **Planilha Google:** recebe as OS (fila de lançamento).
- **WhatsApp:** o técnico manda o aviso pelo próprio celular, com até 3 fotos.
- **Claude:** só entra para lançar no SIGMA, em lote, 2 vezes ao dia.

## Instalação (uma vez, uns 20 minutos)

### 1. Chave gratuita do Gemini
1. Entre em https://aistudio.google.com com uma conta Google.
2. Clique em **Get API key → Create API key** e copie a chave (começa com `AIza`).
3. Em **Google Cloud Console → APIs e serviços → Credenciais**, edite a chave. Em **Restrições de aplicativo**, escolha **Sites** e adicione `https://wass021the.github.io/*`. Assim a chave só funciona no seu app.

Observação: no plano gratuito, o Google pode usar o conteúdo enviado para melhorar os produtos dele. Não fotografe documentos sigilosos.

### 2. Publicar o app (GitHub Pages)
1. No repositório, abra **Settings → Pages**.
2. Em **Source**, escolha **Deploy from a branch → main → / (root) → Save**.
3. Em 1 ou 2 minutos o app fica em https://wass021the.github.io/App-Os-Foto-/

### 3. Planilha da fila (Apps Script)
1. Crie uma planilha nova no Google Sheets chamada "OS por Foto v2".
2. Abra **Extensões → Apps Script**, apague o conteúdo e cole o arquivo `apps_script/Code.gs`.
3. Abra **Configurações do projeto (engrenagem) → Propriedades do script → Adicionar**. Nome: `TOKEN`. Valor: uma senha que você inventar. Não use a senha do SIGMA.
4. Clique em **Implantar → Nova implantação → Tipo: App da Web**:
   - Executar como: **Eu**
   - Quem pode acessar: **Qualquer pessoa**
5. Autorize e copie o endereço que termina em `/exec`.

### 4. Configurar cada celular
1. Abra o link do app no Chrome do celular.
2. Toque nos três pontinhos e em **Adicionar à tela inicial**.
3. Na aba **Config.**, preencha: técnico, chave do Gemini, endereço `/exec` e senha.

### 5. Rotina de lançamento
Crie a tarefa agendada com o texto de `rotina/ROTINA_LOTE.md` (o Claude faz isso se você pedir e passar o `/exec` e a senha).

## Fluxo do técnico
1. **Nova:** tirar fotos, gravar o relato (opcional) e salvar.
2. Com internet, o Gemini analisa e a OS aparece em **Fila → Revisar**.
3. Conferir as etapas de horas, o tempo de parada (se a máquina parou) e o texto do WhatsApp. Depois, **Confirmar e pôr na fila**.
4. **WhatsApp:** abre o compartilhamento com até 3 fotos. Escolha o grupo da manutenção. O botão **Teste p/ mim** manda só para o número de teste.
5. Depois da rotina, a OS mostra o número do SIGMA.
