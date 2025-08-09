# Conceito
- Basicamente cron job é um agendador para uma execução.
- Pode ser utilizado para realizar agendar/executar processos simples como um comando `echo 'I love DevOps' >> cronjob.txt` até executar um script bash ou código python por exemplo.
- No cron job agendamos a execução de um processo com base em cinco asteriscos,  onde o primeiro trata-se do minuto, o segundo das horas, dia, mês e semana (da esquerda para direita).
- Podemos também agendar de maneira verbosa utilizando @, exemplo @daily, @yearly, @weekly e @monthly.
![[cronjob.png]]

# Comandos úteis
1. `crontab -e` basicamente para abrir o registro de onde deverá ser configurado os agendadores
![[agendador comando.png]]
2. `contrab -l` retorna o registro sem necessariamente acessar o registro para modificação. Semelhante a utilizar o comando cat.


