## Passo 1: Configurar o Banco de Dados Neo4j

Para que o Neo4j possa se conectar a outros servidores, é necessário modificar as configurações no arquivo `/etc/neo4j/neo4j.conf`. Para isso, utilizaremos o editor Nano. Se você não estiver como usuário root, lembre-se de usar o comando `sudo`:

```sh
root@host:~# nano /etc/neo4j/neo4j.conf
```

No arquivo aberto, localize a seguinte linha na seção Network Connector:

```bash
#dbms.default_listen_address=0.0.0.0
```
Descomente essa linha removendo o símbolo #, e salve a alteração.


O valor 0.0.0.0 fará com que o Neo4j seja vinculado a todas as interfaces de rede IPv4 disponíveis. Caso deseje restringir a conexão a um IP específico ou a uma rede utilizada pelos seus servidores, substitua 0.0.0.0 pelo endereço desejado.

## Passo 2: Permitir o Tráfego nas Portas do Neo4j

O Neo4j utiliza portas específicas para comunicação. Para garantir o acesso adequado, execute os seguintes comandos:

```sh
sudo ufw allow 7687/tcp
```
A porta 7687 é utilizada pelo Bolt Protocol, que permite conexões entre clientes e o servidor Neo4j.

```sh
sudo ufw allow 7474/tcp
```
A porta 7474 é usada pela interface web do Neo4j, onde é possível acessar o banco de dados através do navegador.

## Passo 3: Recarregar as Regras do Firewall
Após adicionar as regras, é necessário recarregar o ufw para aplicar as alterações:

```sh
ufw reload
```

Verificar o Status do Firewall
Confirme se as regras foram aplicadas corretamente com o comando:

```sh
ufw status
```
A saída deve exibir algo como:

* 7474/tcp ALLOW Anywhere
* 7687/tcp ALLOW Anywhere

## Passo 4: Testar a Conectividade com a Interface Web
Para verificar se o Neo4j está acessível via HTTP, execute:

```sh
curl -I http://IPAQUIAMIGÃO:7474
```
Se o servidor estiver rodando corretamente, a saída mostrará um cabeçalho HTTP 200 OK ou algo semelhante, indicando que a conexão foi bem-sucedida.

## Passo 5: Reiniciar o Serviço do Neo4j
Caso a conexão não esteja funcionando corretamente, pode ser necessário reiniciar o serviço:

```sh
sudo systemctl restart neo4j
```

* Agora basta conectar no endereço http, segue exemplo http://IPAQUIAMIGAO:7474/browser/
