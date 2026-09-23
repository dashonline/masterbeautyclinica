# Dashboard de Tráfego — Clínica Master Beauty

Dashboard estática (GitHub Pages) do funil de captação da Clínica Master Beauty:
**mensagens (WhatsApp/Direct)** hoje, com estrutura pronta para **leads de formulário** e
**agendamentos** (planilha preenchida pela equipe). Base: dash do Instituto Master Beauty.

## Como funciona
- `build.ps1` chama a **Meta Graph API** (insights nível anúncio, por dia) e gera `data.js`
  (`daily[]` + `grain[]`, agregados anonimizados). Imposto ×1,1385 sobre todo gasto.
  Só entram campanhas cujo nome começa com `CMB |`.
- `index.html` + `app.js` + `styles.css` renderizam Visão Geral + Tráfego Pago, sem libs.
  CTR sempre de **link**.
- **Leads**: aparecem sozinhos quando existir campanha `| LEAD |`. A lista de contatos precisa
  de `LEADS_ID` + `LEADS_FORMS` no `app.js` (conexão nativa Meta→Sheets).
- **Agendamentos**: lidos ao vivo da planilha `1jZMxkHeiLAwU3A-hR8Bs5zz6JT7nfap1u-BdR9xIJdY`,
  aba `Planilha agendamento` (A = dd/mm, D = agendamentos, F = valor total). Aparecem quando houver lançamento.
- `.github/workflows/build.yml` roda o build de hora em hora e publica no Pages (`deploy-pages@v4`).
  O token da Meta vem do secret **`META_ACCESS_TOKEN`**.

## Rodar local
```powershell
.\build.ps1 -Mode all      # lê META_ACCESS_TOKEN do ambiente ou do .env (gitignored)
python -m http.server       # abrir index.html
```

## Manutenção
- Conta: `act_1007230201772374` (CA - CLINICA MASTER BEAUTY).
