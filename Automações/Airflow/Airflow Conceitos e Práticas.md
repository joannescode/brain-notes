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


# Projeto Prático
## Aprendizados
- Após o desenvolvimento do projeto, importante salvar o requirements com as dependências do projeto.
- Dentro do requirements.txt ter cuidado para não passar como requerimentos versões de bibliotecas referentes ao airflow.
- Ao utilizar logging, importante tratar as mensagens que envolve variáveis e informações que não são strings diretas.
- Evitar configurar logging onde está presente a estrutura da dag, criar um .py separado e importar.
- Apos montar a estrutura da Dag e do def referente ao executor da tarefa/projeto, invocar a task (função a ser executada) ao final do código e instanciar globlamente.
- Airflow pode armazenar "cache" devido a diversos motivos, forma de como foi criado o docker, cache do python salvos diretamente dentro do vscode, etc.

### Exemplo de estrutura de uma dag:
@dag(
    schedule="@daily",                        # Frequência de execução
    start_date=datetime(2024, 1, 1),          # A partir de quando começa
    catchup=False,                            # Não executar pendências anteriores
    default_args={"owner": "...", "retries": 3},  # Argumentos padrão para tasks
    tags=["dev", "scraper"],                  # Tags para organização no UI
)

# Conceitos Fundamentais e Boas Práticas

- Idempotência, a mesma tarefa executada diversa vezes deverá gerar sempre a mesma saída. E toda execução que pode gerar um novo estado dentro da estrutura do projeto deve ser controlada de maneira correta.
- Funções pequenas e isoladas, é importante separar cada etapa de um pipeline em tasks separadas.
- Side-effects controlados, evitar efeitos colaterais durante e ao final da execução de um processo, airflow pode mata/reiniciar a tarefa, ou não é possível reiniciar com segurança.