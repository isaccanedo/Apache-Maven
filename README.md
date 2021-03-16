# Apache-Maven
:computer: # O objetivo principal do Maven é permitir que um desenvolvedor compreenda o estado completo de um esforço de desenvolvimento no menor período de tempo.

### Introdução
Maven, uma palavra em iídiche que significa acumulador de conhecimento, começou como uma tentativa de simplificar os processos de construção no projeto da Turbina de Jacarta. Havia vários projetos, cada um com seus próprios arquivos de construção Ant, que eram ligeiramente diferentes. Os JARs foram verificados no CVS. Queríamos uma maneira padrão de construir os projetos, uma definição clara do que o projeto consistia, uma maneira fácil de publicar as informações do projeto e uma maneira de compartilhar JARs entre vários projetos.

O resultado é uma ferramenta que agora pode ser usada para construir e gerenciar qualquer projeto baseado em Java. Esperamos ter criado algo que torne o trabalho diário dos desenvolvedores Java mais fácil e geralmente ajude na compreensão de qualquer projeto baseado em Java.

# Objetivos do Maven
O objetivo principal do Maven é permitir que um desenvolvedor compreenda o estado completo de um esforço de desenvolvimento no menor período de tempo. Para atingir esse objetivo, a Maven lida com várias áreas de preocupação:

- Facilitando o processo de build;
- Fornecimento de um sistema de construção uniforme;
- Fornecimento de informações de projeto de qualidade;
- Estimular melhores práticas de desenvolvimento.

# Facilitando o processo de construção
Embora o uso do Maven não elimine a necessidade de saber sobre os mecanismos subjacentes, o Maven protege os desenvolvedores de muitos detalhes.

# Fornecendo um sistema de construção uniforme
O Maven constrói um projeto usando seu modelo de objeto de projeto (POM) e um conjunto de plug-ins. Depois de se familiarizar com um projeto Maven, você saberá como todos os projetos Maven são construídos. Isso economiza tempo ao navegar em muitos projetos.

# Fornecimento de informações de projeto de qualidade
O Maven fornece informações úteis do projeto que são em parte retiradas de seu POM e em parte geradas a partir das fontes de seu projeto. Por exemplo, o Maven pode fornecer:

- Registro de alterações criado diretamente do controle de origem
- Fontes com referência cruzada
- Listas de mala direta gerenciadas pelo projeto
- Dependências usadas pelo projeto
- Relatórios de teste de unidade, incluindo cobertura

Produtos de análise de código de terceiros também fornecem plug-ins Maven que adicionam seus relatórios às informações padrão fornecidas pelo Maven.

# Fornecendo diretrizes para o desenvolvimento de melhores práticas
O Maven tem como objetivo reunir os princípios atuais para o desenvolvimento de melhores práticas e facilitar a orientação de um projeto nessa direção.

Por exemplo, especificação, execução e relatório de testes de unidade fazem parte do ciclo normal de construção usando Maven. As práticas recomendadas de teste de unidade atuais foram usadas como diretrizes:

- Manter o código-fonte do teste em uma árvore separada, mas paralela;
- Usando convenções de nomenclatura de casos de teste para localizar e executar testes;
- Ter casos de teste configurando seu ambiente em vez de customizar a construção para preparação de teste.

O Maven também auxilia no fluxo de trabalho do projeto, como liberação e gerenciamento de problemas.

O Maven também sugere algumas diretrizes sobre como fazer o layout da estrutura de diretórios do seu projeto. Depois de aprender o layout, você pode navegar facilmente em outros projetos que usam o Maven.

Embora adote uma abordagem opinativa para o layout do projeto, alguns projetos podem não se encaixar nesta estrutura por razões históricas. Embora o Maven seja projetado para ser flexível às necessidades de diferentes projetos, ele não pode atender a todas as situações sem comprometer seus objetivos.

Se o seu projeto tem uma estrutura de construção incomum que não pode ser reorganizada, você pode ter que abrir mão de alguns recursos ou do uso do Maven por completo.

# Instalação
Maven é uma ferramenta Java, portanto, você deve ter o Java instalado para continuar.

Primeiro, baixe o Maven e siga as instruções de instalação. Depois disso, digite o seguinte em um terminal ou prompt de comando:
```
mvn --version
```

Ele deve imprimir sua versão instalada do Maven, por exemplo:
```
Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
Maven home: D:\apache-maven-3.6.3\apache-maven\bin\..
Java version: 1.8.0_232, vendor: AdoptOpenJDK, runtime: C:\Program Files\AdoptOpenJDK\jdk-8.0.232.09-hotspot\jre
Default locale: en_US, platform encoding: Cp1250
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

Dependendo da configuração da sua rede, você pode precisar de configuração extra. Verifique o Guia para configurar o Maven, se necessário.

Se você estiver usando o Windows, deve consultar os Pré-requisitos do Windows para garantir que está preparado para usar o Maven no Windows.

# Criando um Projeto
Você precisará de um local para o seu projeto residir, crie um diretório em algum lugar e inicie um shell nesse diretório. Na linha de comando, execute o seguinte objetivo do Maven:
```
mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app 
-DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 
-DinteractiveMode=false
```
Se você acabou de instalar o Maven, pode demorar um pouco na primeira execução. Isso ocorre porque o Maven está baixando os artefatos mais recentes (jars de plugin e outros arquivos) em seu repositório local. Você também pode precisar executar o comando algumas vezes antes que ele seja bem-sucedido. Isso ocorre porque o servidor remoto pode atingir o tempo limite antes que os downloads sejam concluídos. Não se preocupe, existem maneiras de consertar isso.

Você notará que a meta de geração criou um diretório com o mesmo nome fornecido como artifactId. Mude para esse diretório.
```
cd my-app
```

Sob este diretório, você notará a seguinte estrutura de projeto padrão.

```
my-app
|-- pom.xml
`-- src
    |-- main
    |   `-- java
    |       `-- com
    |           `-- mycompany
    |               `-- app
    |                   `-- App.java
    `-- test
        `-- java
            `-- com
                `-- mycompany
                    `-- app
                        `-- AppTest.java
```

O diretório src/main/java contém o código-fonte do projeto, o diretório src/test/java contém a fonte de teste e o arquivo pom.xml é o modelo de objeto do projeto, ou POM.

# O POM
O arquivo pom.xml é o núcleo da configuração de um projeto no Maven. É um único arquivo de configuração que contém a maioria das informações necessárias para construir um projeto da maneira que você deseja. O POM é enorme e pode ser assustador em sua complexidade, mas não é necessário entender todas as complexidades ainda para usá-lo de forma eficaz. O POM deste projeto é:
```
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
 
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0-SNAPSHOT</version>
 
  <properties>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
  </properties>
 
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

# O que eu acabei de fazer?
Você executou o arquétipo de meta do Maven: gerar e passou vários parâmetros para essa meta. O arquétipo do prefixo é o plug-in que fornece o objetivo. Se você estiver familiarizado com o Ant, pode considerá-lo semelhante a uma tarefa. Este arquétipo: gerar meta criou um projeto simples baseado em um arquétipo maven-arquétipo-início rápido. Por ora, basta dizer que um plugin é uma coleção de objetivos com um propósito geral comum. Por exemplo, o jboss-maven-plugin, cujo propósito é "lidar com vários itens jboss".

# Construir o Projeto
```
mvn package
```
A linha de comando imprimirá várias ações e terminará com o seguinte:
```
 ...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.953 s
[INFO] Finished at: 2019-11-24T13:05:10+01:00
[INFO] ------------------------------------------------------------------------
```
Ao contrário do primeiro comando executado (arquétipo: gerar), você pode notar que o segundo é simplesmente uma única palavra - pacote. Em vez de um objetivo, esta é uma fase. Uma fase é uma etapa do ciclo de vida de construção, que é uma sequência ordenada de fases. Quando uma fase é fornecida, o Maven executará todas as fases na sequência até e incluindo aquela definida. Por exemplo, se executarmos a fase de compilação, as fases que realmente são executadas são:

- validar
- gerar-fontes
- fontes de processo
- gerar recursos
- recursos de processo
- compilar

Você pode testar o JAR recém-compilado e empacotado com o seguinte comando:
```
java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
```

Que irá imprimir o essencial:

```
Hello World!
```

# Java 9 ou posterior
Por padrão, sua versão do Maven pode usar uma versão antiga do maven-compiler-plugin que não é compatível com o Java 9 ou versões posteriores. Para direcionar o Java 9 ou posterior, você deve pelo menos usar a versão 3.6.0 do maven-compiler-plugin e definir a propriedade maven.compiler.release para a versão do Java que você está direcionando (por exemplo, 9, 10, 11, 12, etc. .).

No exemplo a seguir, configuramos nosso projeto Maven para usar a versão 3.8.1 do maven-compiler-plugin e Java 11 de destino:
```
<properties>
        <maven.compiler.release>11</maven.compiler.release>
    </properties>
 
    <build>
        <pluginManagement>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-compiler-plugin</artifactId>
                    <version>3.8.1</version>
                </plugin>
            </plugins>
        </pluginManagement>
    </build>
```

Para saber mais sobre a opção --release do javac, consulte JEP 247.

# Executando ferramentas Maven
### Fases Maven
Embora dificilmente seja uma lista abrangente, essas são as fases do ciclo de vida padrão mais comuns executadas.

- validar: validar se o projeto está correto e se todas as informações necessárias estão disponíveis;
- compilar: compila o código-fonte do projeto;
- test: testa o código-fonte compilado usando uma estrutura de teste de unidade adequada. Esses testes não devem exigir que o código seja empacotado ou implantado;
- pacote: pega o código compilado e empacota-o em seu formato distribuível, como um JAR;
- teste de integração: processe e implante o pacote, se necessário, em um ambiente onde os testes de integração possam ser executados;
- verificar: execute todas as verificações para verificar se a embalagem é válida e atende aos critérios de qualidade;
- instalar: instala o pacote no repositório local, para uso como uma dependência em outros projetos localmente;
- implantar: feito em um ambiente de integração ou liberação, copia o pacote final para o repositório remoto para compartilhamento com outros desenvolvedores e projetos.

Existem dois outros ciclos de vida Maven importantes além da lista padrão acima. Eles estão

- limpar: limpa artefatos criados por compilações anteriores;
- site: gera a documentação do site para este projeto.

As fases são, na verdade, mapeadas para objetivos subjacentes. Os objetivos específicos executados por fase dependem do tipo de embalagem do projeto. Por exemplo, package executa jar: jar se o tipo de projeto for um JAR, e war: war se o tipo de projeto for - você adivinhou - um WAR.

Uma coisa interessante a se notar é que as fases e metas podem ser executadas em sequência.
```
mvn clean dependency:copy-dependencies package
```
Este comando irá limpar o projeto, copiar dependências e empacotar o projeto (executando todas as fases até o pacote, é claro).

# Gerando o Site
```
mvn site
```
Esta fase gera um site com base nas informações do pom do projeto. Você pode consultar a documentação gerada em destino/site.

# Conclusão
Esperamos que esta rápida visão geral tenha despertado seu interesse na versatilidade do Maven. Observe que este é um guia de início rápido muito truncado. Agora você está pronto para obter detalhes mais abrangentes sobre as ações que acabou de realizar.
