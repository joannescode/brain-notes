# Pontos Relevantes
- Airflow é um orquestrador de scripts.
- Para trabalhar com Airflow pode ser necessário o Docker instalado.
- Necessitamos do astro-cli para implementar/executar um airflow de maneira local.

# Básico do Pipeline
- DAG: gráfico contendo todo o fluxo de trabalho, mostrando os nós relacionados e não relacionados.
- DAG Run: execução de uma dag contendo o fluxo de trabalho. Podendo estar dentro de quatro categorias de execução: agenda, manual, dataset triggered ou backfill.
- Task: uma tarefa única presente dentro do processo da DAG.
- Instance Task: execução de uma tarefa dentro de um momento especifico.
- Dynamic Task: tarefa dinâmica que serve como modelo para um numero variável de tarefas criadas a partir delas.
- Asset: objeto criado após a execução de uma tarefa, seja um dataset, data object, tables, files, etc.

# Formas de criar tarefas
- Decoradores: conjunto de decoradores que envolvem funções pythons para execução dentro de uma DAG. Cada função decorada se torna uma tarefa dentro de uma DAG.
- Operadores: classes que recebem argumentos, onde cada operador instanciado se torna uma DAG.
