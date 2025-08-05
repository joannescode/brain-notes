# Motivo para se utilizar?
- Otimização de recursos, o container separa somente a quantidade de recursos necessários para poder executar a aplicação.
- Empacotamento, todas as dependências, códigos etc necessários para execução ficam empacotados em conjunto.
- Imutabilidade, um app presente em um container nunca mudará.
- Deploy facilitado, é mais simples e fácil realizar o deploy de uma aplicação.

# Etapas pré-deploy
- Desenvolvimento do código fonte em si, planejar, arquitetar e desenvolver o projeto.
- Subir em um SCM (github, gitlab) para manutenibilidade, registro e compartilhamento remoto.
- Testar o projeto em contextos diferentes, funções diferentes etc.
- Realizar o build do projeto dentro de um container.
- Fazer o push para um registry, como ECS da Amazon para tornar o docker remoto.
- Disponibilizar ao cliente final o uso da aplicação ou entrega do serviço feito pela mesma (Deploy).

# Imagem vs Container
- Uma imagem nada mais é que uma modificação do estado anterior sendo registrado o seu ID atual, o tamanho da mudança e outras descrições.
- Uma imagem pode ter diversas camadas, sendo cada camada uma versão/alteração.
- A imagem só pode ser acessada para leitura, ou seja consultar informações sobre as alterações de cada camada da imagem.
- O container é como se fosse a camada "física" acessível para a execução da imagem final, ou seja a mesma contempla todas as camadas formando o conjunto da imagem em si.

## Boas práticas

No Dockerfile é onde vamos escrever as instruções para criar a imagem que, posteriormente, será usada para criar um container.

Algumas boas práticas:

1. Mantenha os containers _ephemerals,_ isto é, que você possa parar, reiniciar e ele continue funcionando sem maiores problemas.
2. Seguir o princípio 6 do 12 factor app. O processo deve ser stateless, e qualquer persistência precisa ser feito em alguma aplicação que mantém o estado, mais comumente uma database.
3. Não inclua arquivos desnecessários no seu Dockerfile, isso pode resultar em falhas de segurança e aumento no tamanho da imagem.
4. Use .dockerignore para evitar "lixo" no Dockerfile.
5. Use multi-staging para otimizar o tamanho da imagem.
6. Não instale pacotes desnecessários.
7. Desacople as aplicações. Nunca usar um container para mais de um objetivo. Por exemplo, o Wordpress deve rodar em um container, enquanto a database roda em outro, nunca ambos em um container.
8. Minimize o número de camadas, isso geralmente otimiza o tamanho da imagem.
9. Use e abuse da camada de cache do Docker.

# Deploy na prática
## Dicas Gerais
- Manter o Dockerfile no diretório pai de onde encontra-se o projeto, com isso ira facilitar os COPY das libs, utils e src necessário que completam o projeto.
- Elaborar um dockerignore contendo diretórios de registro, cache, backup e outros que não serão necessários em projetos gerais para o deploy de um container.
- Nomear o Dockerfile com . e o nome referente ao projeto a ser feito o deploy, exemplo: Dockerfile.etl_govbr;
## Montando um Dockerfile
## Etapas
1. Montar o Dockerfile com o nome respectivo ao projeto e manter no diretório acima de todo o código fonte.
2. Selecionar a versão correta da linguagem a ser trabalhada e de preferência escolher uma distribuição de SO leve e que atenda os requezitos do projeto.
3. Instalar todas as dependências necessárias para executar o projeto referente a instalações do sistema operacional.
4. Definir as variáveis de ambientes, exemplo (trabalhando com selenium webdriver): ![[Variáveis de Ambiente.png]]
5. Estabelecer o workdir da aplicação `WORKDIR /app`
6. Montar um requirements.txt contendo somente as bibliotecas/frameworks necessárias para execução do projeto.
7. Anotar todos os diretórios/arquivos importados dentro do código antecipadamente para realizar o COPY dentro do dockerfile.
8. Realizar a cópia de somente os diretórios/arquivos necessários para dentro do docker, com isso não teremos uma imagem grande de maneira desnecessária, comando: `COPY src/libs/gov/paineis/accept_cookies.py ./src/libs/gov/paineis/accept_cookies.py` (arquivos), `COPY project/scraper/gov/ ./project/scraper/gov/` (diretórios). Ao copiar arquivos, importante lembrar de adicionar também sua extensão, exemplo: .py
9. Por fim passar o comando de execução do projeto: `CMD ["python", "project/scraper/gov/airflow/main.py"]`