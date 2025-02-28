# Instalação do Neo4j

## 1. Instalar o Java

O Neo4j requer o Java para ser executado. Primeiro, atualize a lista de pacotes do sistema:
```bash
sudo apt update
```
A atualização garante que você terá acesso às versões mais recentes dos pacotes disponíveis.

Agora, instale o Java padrão do sistema:
```bash
sudo apt install default-jdk
```
Essa instalação configura o Java de forma genérica, permitindo que aplicações dependentes do Java sejam executadas.

Se precisar de uma versão específica do Java (neste caso, a versão 17 do OpenJDK):
```bash
sudo apt install openjdk-17-jdk
```
Essa instalação força o uso do OpenJDK 17, que pode ser um requisito para algumas versões do Neo4j.

Verifique se o Java foi instalado corretamente:
```bash
java -version
```
Este comando exibe a versão do Java instalada, confirmando se a instalação foi bem-sucedida.

## 2. Instalar o Neo4j

O Neo4j pode ser instalado na pasta home do usuário.
Baixar e extrair a Enterprise Edition:

```bash
wget -O neo4j-enterprise-5.5.0-unix.tar.gz 'https://neo4j.com/artifact.php?name=neo4j-enterprise-5.5.0-unix.tar.gz'
tar -xf neo4j-enterprise-5.5.0-unix.tar.gz
cd neo4j-enterprise-5.5.0
```

## 3. Aceitar o Contrato de Licença (apenas para Enterprise Edition)
Se estiver utilizando a versão Enterprise, é necessário aceitar os termos da licença antes de iniciar o serviço.

Defina a variável de ambiente NEO4J_HOME, apontando para o diretório onde o Neo4j foi extraído:

```bash
export NEO4J_HOME=~/neo4j-enterprise-5.5.0
```
Isso informa ao sistema onde está localizada a instalação do Neo4j.

Agora, adicione o diretório bin do Neo4j ao PATH do sistema, para poder executar comandos do Neo4j sem precisar especificar o caminho completo:
```bash
export PATH=$NEO4J_HOME/bin:$PATH
```
Para aceitar a licença comercial:

```bash
neo4j-admin server license --accept-commercial
```

Para aceitar a licença de avaliação:

```bash
neo4j-admin server license --accept-evaluation
```
Isso libera o uso da versão Enterprise conforme o tipo de licença escolhido.

## 3.1. Em caso de erro pelo java estar na versão errada basta selecionar a versão 17
```bash
sudo update-alternatives --config java
```

## 4. Executar o Neo4j

Finalmente, inicie o servidor do Neo4j:
```bash
neo4j start
```

## 5. Acesse o cypher

```bash
cypher-shell
```


* Mude a senha no primeiro acesso
