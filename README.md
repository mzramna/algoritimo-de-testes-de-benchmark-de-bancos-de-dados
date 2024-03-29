﻿# algoritimo-de-testes-de-benchmark-de-bancos-de-dados
o banco de dados é definido pelos arquivos sql dentro da pasta containers_build e pelo arquivo scripts/padroes.json e seguindo os parametros a baixo
```
{
  "nome da tabela":{
  "nome da coluna":["tipo de dado","parametros adicionais"]
  }
}
```
os tipos de dados estão definidos a abaixo:
```
"nomeCompleto": gera um nome completo de uma pessoa relativa ao pais selecionado, não possui nenhum parametro adicional
"primeiroNome":  gera um primeiro nome de uma pessoa relativa ao pais selecionado, não possui nenhum parametro adicional
"sobrenome":  gera um sobrenome de uma pessoa relativa ao pais selecionado, não possui nenhum parametro adicional
"timestamp": gera um timestamp, precisa de entre 1 e 3 parametros adicionais:
    '''precisa obrigatoriamente de 1 parametro dizendo se vai ser tudo randomico ou se vai ter um intervalo, se tiver um intervalo devem ser passados mais 2 parametros,um inicial e um final , se o final for o valor "agora" então o valor final sera o timestamp de agora do sistema operacional  
    Para gerar com mais precisão usar o 2 parametro como: "-30y",sendo: - > significando anterior , 30 > quanto tempo , y > escala de tempo(anos) ou usando o padrão Date("dia") onde o dia deve ser passado como "1999-02-02" 
    O 3 parametro deve ser passado como o 2,mas não se limita apenas ao token de tempo anterior,sendo possivel um intervalo do futuro ''' 
"pais": insere o pais atual selecionado para a geração de dados, não possui nenhum parametro adicional
"cidade": gera uma cidade relativa ao pais selecionado, não possui nenhum parametro adicional
"endereco": gera um endereço relativa ao pais selecionado, não possui nenhum parametro adicional
"bairro": gera um bairro relativa ao pais selecionado, não possui nenhum parametro adicional
"cep": gera um cep/zip-code relativa ao pais selecionado, não possui nenhum parametro adicional
"telefone": gera um telefone relativa ao pais selecionado, não possui nenhum parametro adicional
"nomeCategoria": gera uma palavra aleatoria relativa ao idioma do pais selecionado, não possui nenhum parametro adicional
"email": gera um email, não possui nenhum parametro adicional
"usuario": gera um nome de usuario, não possui nenhum parametro adicional
"senha": gera uma senha com um tamanho entre 8 e 32 caracteres, não possui nenhum parametro adicional
"boleano": gera um valor booleado, não possui nenhum parametro adicional
"idioma": gera um idioma relativo ao pais selecionado, não possui nenhum parametro adicional
"titulo": gera uma sentença contendo entre 1 e 10 palavras no idioma relativo ao pais selecionado, não possui nenhum parametro adicional
"textoLongo": gera um texto contendo entre 1 e 2 paragrafos no idioma relativo ao pais selecionado, não possui nenhum parametro adicional
"nota": gera um valor decimal com virgula entre 0 e 10, não possui nenhum parametro adicional
"ano": gera um ano, não possui nenhum parametro adicional
"duracaoDias": gera um intervalo de dias entre 0 e 10, não possui nenhum parametro adicional
"datetime": gera uma data no padrão ano-mes-dia, não possui nenhum parametro adicional
"duracaoHoras": gera uma duração de horas entre 0 e 4, não possui nenhum parametro adicional
"naLista": seleciona um valor de texto entre os parametros inseridos nos parametros adicionais, aceita uma quantidade indeterminada de parametros adicionais, sendo eles os valores dentre os quais deve ser selecionado um aleatoriamente
"valorPago": gera um valor deciamal entre 0 e 50, não possui nenhum parametro adicional
"associacao": seleciona um dos valores previamente existentes de id em uma das tabelas informadas, parametros obrigatórios são nome da tabela e se random ou se definido é adicional, caso não seja inserido um valor obrigatoriamente é random,caso o valor seja random será selecionado entre os dados previamente gerados qualquer dado da tabela informada
"id": gera um numero inteiro sequencial, servindo como id da tabela selecionada, ele automaticamente contabiliza a quantidade de valores já inseridos na tabela sqlite e retorna esse valor mais 1
```
ainda existe mais um arquivo de configuração relevante, o scripts/info_docker.json, nele são inseridos os dados de acesso ao banco de dados gerado no docker,os parametros estão descritos a baixo:
```
{
    "maquina_arm":{
        "url":"url da maquina arm",
        "port_docker_sock":"porta de acesso do docker sock",
        "mariadb_id":"alpine-mariadb-1",
        "mariadb_connect":{
            "host":"url da maquina arm",
            "user":"usuario de acesso definido no arquivo docker-compose",
            "password":"senha de acesso definido no arquivo docker-compose",
            "database":"nome do banco de dados",
            "port":3306,
            "tipo":0,
            "sql_file_pattern":"containers_build/mysql default exemple.sql"
            },
        "postgres_id":"alpine-postgres-1",
        "postgres_connect":{
            "host":"url da maquina arm",
            "user":"usuario de acesso definido no arquivo docker-compose",
            "password":"senha de acesso definido no arquivo docker-compose",
            "database":"nome do banco de dados",
            "port":5432,
            "tipo":1,
            "sql_file_pattern":"containers_build/postgres default exemple.sql"
            }
        },
    "maquina_amd":{
        "url":"url da maquina amd",
        "port_docker_sock":2375,
        "mariadb_id":"alpine-mariadb-1",
        "mariadb_connect":{
            "host":"url da maquina amd",
            "user":"usuario de acesso definido no arquivo docker-compose",
            "password":"senha de acesso definido no arquivo docker-compose",
            "database":"nome do banco de dados",
            "port":3306,
            "tipo":0,
            "sql_file_pattern":"containers_build/mysql default exemple.sql"
        },
        "postgres_id":"alpine-postgres-1",
        "postgres_connect":{
            "host":"url da maquina amd",
            "user":"usuario de acesso definido no arquivo docker-compose",
            "password":"senha de acesso definido no arquivo docker-compose",
            "database":"nome do banco de dados",
            "port":5432,
            "tipo":1,
            "sql_file_pattern":"containers_build/postgres default exemple.sql"
        }
    }
}
```
