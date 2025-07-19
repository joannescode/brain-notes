# Primeiro Módulo
## Vantagens e Desvantagens: Virtualização

- Virtualização de aplicação, temos dois tipos sendo o Bare-metal ou o Hospedado. O mais comum é o hospedado onde se é utilizado um software para isto rodando em cima do sistema operacional.
- Vantagens da Virtualização são o uso completo da virtualização, gerenciamento de recursos de forma precisa, execução de aplicações legadas, backup facilitado, uso total de recursos de hardware para evitar desperdício.
- Desvantagens da Virtualização são demora no tempo de inicialização do sistema, complexidade para gerenciamento e configuração, risco de segurança na camada hypervisor, menor portabilidade das imagens virtualizadas.

## Vantagens e Desvantagens: Docker

- Docker, basicamente compacta todas as dependências, versões e requisitos de um sistema e roda como um processo/aplicação diretamente no sistema operacional sem a necessidade da virtualização, assim evitando a sobrecarga da máquina hospedeira.
- Vantagens da conteinerização é necessidade de menor recurso para sua execução, portabilidade da mesma, rápida implementação e inicialização, ideal para micro serviços, integração continua e entrega de melhorias e também redução de custos.
- Desvantagens da conteinerização: segurança compartilhada devido a rodar no mesmo kernel, persistência de dados pois ao desligar um contêiner perdemos o estado do mesmo, complexidade de gerenciamento em alta escala, dificuldade para acesso de baixo nível

## Para quê serve Serverless?

- Serverless, basicamente trata-se de evitar preocupações com o implementação, gerenciamento e monitoramento de um servidor para execução de uma aplicação, onde a responsabilidade da mesma é terceirizada para sistemas em nuvem.
- FaaS, sendo a execução de funções através de requisições HTTP, mudanças em banco de dados, onde o desenvolvedor apenas se preocupa com a lógica/regras do negócio.

# Segundo Módulo
## Quais problemas o Serverless resolve?

- Tarefas possíveis de serem quebradas em diversos módulos tendo um baixo acoplamento assim permitindo trabalhar com micro serviços
- Processos que o seu padrão é ser instável em quantidade de execuções e períodos, mantendo em nuvem conseguimos ter uma boa elasticidade e escalabilidade.
- Processos em segundo plano ou comunicação entre sistemas que podem ser impactados devida sua latência (cold starts).
