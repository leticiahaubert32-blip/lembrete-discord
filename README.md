name: Enviar Lembrete Discord

on:
  schedule:
    # 18:00 UTC = 15:00 de Brasília. 
    # 1-5 = Segunda a Sexta-feira.
    - cron: '0 18 * * 1-5'

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
