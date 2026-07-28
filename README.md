name: Enviar Lembrete Discord

on:
  schedule:
    - cron: '0 18 * * 1-5'
  workflow_dispatch:

jobs:
  enviar_mensagem:
    runs-on: ubuntu-latest
    steps:
      - name: Disparar Webhook
        run: |
          curl -H "Content-Type: application/json" \
               -X POST \
               -d '{"content": "💧 **Pausa para a Saúde!** @everyone, já são 15h! Hora de beber um copo d'\''água, levantar da cadeira e fazer um breve alongamento. 🏃‍♂️✨"}' \
               "${{ secrets.DISCORD_WEBHOOK }}"

