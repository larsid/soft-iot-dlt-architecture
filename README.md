# soft-iot-dlt-architecture

## 1 - Pré-requisitos

- Java Developer Kit (JDK) 1.8
- Maven 3.0.4 ou superior
- ServiceMix

## 2 - Instalação do ServiceMix

- Baixe o servicemix no [site oficial](http://servicemix.apache.org/downloads/servicemix-7.0.0.html).

- [Manual de instalação](http://servicemix.apache.org/docs/7.x/quickstart/installation.html)

## 3 - Configurações iniciais

Com o servicemix instalado podemos inicar as configurações básicas necessárias para acompanhar os passos de instalação de cada _bundle_ da arquitetura soft-iot-dlt.

### 3.1 - Adicionar ServiceMix como variável de ambiente

Após baixar e descompactar o Apache ServiceMix é recomendado que ele seja configurado como variável de ambiente. Afim de facilitar o acesso do mesmo em qualquer diretório através do comando `servicemix`.

#### 3.1.1 - Linux

Para fazer isso linux será necessário executar o seguinte comando.

```
echo "export PATH=$PATH:SERVICEMIX_HOME/bin" >> ~/.bashrc
```

Atenção: SERVICEMIX_HOME deve ser substituido pelo caminho do diretório onde você descompatou o Apache ServiceMix.

Exemplo:

Caso tenha descompactado o servicemix na pasta `/opt/servicemix`
então o comando comando ficará:

```
echo "export PATH=$PATH:/opt/servicemix/bin" >> ~/.bashrc
```

Reinicie terminal e em seguida execute o comando `servicemix` para executar o terminal do servicemix.

#### 3.1.2 - Windows

...

### 3.2 - Repositório fonte

Esse passo é importante pois é graças a ele que será possivel utilizar os comandos de instalação dos bundles
pertencentes a arquitetura soft-iot-dlt.

```
config:edit org.ops4j.pax.url.mvn
config:property-append org.ops4j.pax.url.mvn.repositories ", https://jitpack.io@jitpack.io"
config:update
```

### 3.3 - Gerencia de bundles OSGI

<!-- Explicar o que é um bundle OSGI -->

#### 3.3.1 - Terminal

É possível gerenciar os bundles OSGI utilizando o terminal para fazer isso utilize os comandos com préfixo `bundle`, caso tenha dúvidas utilize o comando `bundle --help` para visualizar a lista de comandos disponíveis. Segue abaixo uma tabela com os comandos mais utilizados.

| Comando         | Ação                               | Exemplo                                         |
| --------------- | ---------------------------------- | ----------------------------------------------- |
| bundle:list     | Lista todos os bundles instalados. | bundle:list                                     |
| bundle:install  | Instala um novo bundle.            | bundle:install mvn:group-id/artifact-id/version |
| bundle:unistall | Desistala um bundle.               | bundle:unistall `<ID>`                          |
| bundle:start    | Inicia a execução de um bundle.    | bundle:start `<ID>`                             |
| bundle:stop     | Para a execução de um bundle.      | bundle:stop `<ID>`                              |
| bundle:restart  | Reinicia um bundle.                | bundle:restart `<ID>`                           |

    Dica: Utilize o webconsole para instalar ou atualizar um bundle recém construido.

#### 3.3.2 - WebConsole

O `webconsole` é uma interface gráfica web que permite gerenciar os bundles de forma simples. Com ele é possível instalar, remover, iniciar, parar e atualizar _bundles_.

Execute o comando abaixo no terminal do ServiceMix.

```
feature:install webconsole
```

webconsole do karaf é necessário acessar a URL abaixo.

```
http://localhost:8181/system/console/bundles
```

    :warning: O usuário e senha é "karaf" :warning:

<!--
## 4.0 - Visão geral

| ID  | Bundles                                                                        | Beans | Serviços | Dependencias ID |
| :-: | ------------------------------------------------------------------------------ | :---: | :------: | :-------------: |
|  0  | [dlt-client-tangle](https://github.com/larsid/soft-iot-dlt-client-tangle)      |   3   |    2     |        -        |
|  1  | [dlt-id-manager](https://github.com/larsid/soft-iot-dlt-id-manager)            |   2   |    2     |        -        |
|  2  | [soft-iot-mapping-devices](https://github.com/larsid/soft-iot-mapping-devices) |   3   |    3     |        -        |
|  3  | [dlt-load-monitor](https://github.com/larsid/soft-iot-dlt-load-monitor)        |   3   |    -     |    0, 1 e 2     |
|  4  | [dlt-auth](https://github.com/larsid/soft-iot-dlt-auth)                        |   1   |    -     |        2        |
|  5  | [dlt-load-balancer](https://github.com/larsid/soft-iot-dlt-load-balancer)      |   1   |    -     |    0, 1, e 2    |  -->
