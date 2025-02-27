# Instalação do Repositório do Neo4j no Debian/Ubuntu

Este guia descreve o processo de instalação do repositório do Neo4j em um sistema baseado em Debian/Ubuntu.

## Passo 1: Atualizar os pacotes do sistema

Antes de instalar qualquer novo pacote, é recomendável atualizar a lista de pacotes disponíveis:

```bash
apt update -y
```

## Passo 2: Instalar dependências necessárias
Instale pacotes que garantem a comunicação segura com repositórios remotos:

```bash
apt install apt-transport-https ca-certificates curl software-properties-common -y
```

* apt-transport-https: Permite que o apt baixe pacotes usando HTTPS.
* ca-certificates: Garante que o sistema reconheça autoridades certificadoras confiáveis.
* curl: Utilizado para transferir dados via HTTP/HTTPS.
* software-properties-common: Fornece scripts para gerenciar repositórios adicionais.

## Passo 3: Adicionar a chave GPG do repositório Neo4j
Para garantir a autenticidade dos pacotes, é necessário adicionar a chave GPG do repositório Neo4j:

```bash
curl -fsSL https://debian.neo4j.com/neotechnology.gpg.key | apt-key add -
```

Se o for bem sucedido o retorno será um notório OK.

## Passo 4: Adicionar o repositório Neo4j ao APT
Agora, adicione o repositório do Neo4j à lista de fontes do sistema:

```bash
echo 'deb https://debian.neo4j.com stable 4.4' | sudo tee /etc/apt/sources.list.d/neo4j.list
```
Isso cria um novo arquivo de repositório chamado neo4j.list dentro de /etc/apt/sources.list.d/, apontando para a versão estável 4.4.

## Passo 5: Atualizar a lista de pacotes novamente
Por fim, atualize a lista de pacotes para incluir o novo repositório:

```bash
sudo apt-get update
```

## Passo 6: Instalar o Neo4j

Após adicionar o repositório do Neo4j, instale o pacote com:

```sh
apt install neo4j -y
```

## Passo 7: Habilitar e Iniciar o Serviço do Neo4j
Para garantir que o Neo4j seja iniciado automaticamente no boot do sistema, habilite o serviço:

```bash
systemctl enable neo4j.service
```

Agora, inicie o serviço do Neo4j:
```bash
systemctl start neo4j.service
```

Verifique se o serviço está rodando corretamente:
```bash
systemctl status neo4j.service
```
Se estiver funcionando corretamente, a saída mostrará algo como active (running).

## Passo 8: Acessar o Neo4j via Cypher Shell
O Neo4j pode ser acessado pelo cypher-shell, que permite executar comandos no banco de dados:
```bash
cypher-shell
```

Por padrão, utilize as credenciais iniciais:

* Usuário: neo4j
* Senha: neo4j

Mudança de Senha Após o Primeiro Acesso
No primeiro login, o Neo4j solicitará a alteração da senha por segurança. Basta seguir as instruções exibidas no terminal.

## Passo 9: Validando a Instalação
Verificar a Versão do Neo4j
Execute o seguinte comando dentro do cypher-shell para verificar a versão instalada:


## CALL dbms.components();
Listar os Bancos de Dados Existentes
Para verificar os bancos de dados disponíveis, execute:

```sql
SHOW DATABASES;
```

Passo 10: Sair do Cypher Shell
Para sair do cypher-shell, utilize:

```bash
:exit
```
