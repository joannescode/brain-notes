# Lambda Conceitos
- Uma função lambda é um código executado em resposta a um evento, seja a solicitação de um usuário dentro de um site, um novo arquivo enviado ao storage ou a execução através de um agendamento.
- Para poder implementar um código em um handler e assim criar uma função lambda é preciso criar um pacote deste código seja em .zip ou containers.
- Ambiente de execução do lambda é onde é feito o gerenciamento de recursos necessários para execução da funcionalidade.
- Run times são ambientes para linguagem especifica para executar a função.
- Eventos e acionadores é como a AWS chama as funções com base em um evento especifico.
- Permissões do lambda e cargos servem para gerenciar quem pode acessar e interagir as funções e outros serviços AWS.

![[Lambda principios.png]]

- Para que uma função lambda responda a um evento é necessário a passagem de um gatilho, este gatilho pode ser um json contendo parâmetros, por exemplo:
``` {
  "Location": "SEA",
  "WeatherData":{
    "TemperaturesF":{
      "MinTempF": 22,
      "MaxTempF": 78
    },
    "PressuresHPa":{
      "MinPressureHPa": 1015,
      "MaxPressureHPa": 1027
    }
  }
}`