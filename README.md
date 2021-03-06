# ABNT NBR 15985:2011

A atenção a saúde depende de informação que é associada ao indivíduo assistido.
Em consequência, torna-se necessário "identificar de forma única e acurada um 
indivíduo quando ele se apresenta para a assistência", conforme a Norma ABNT 
NBR 15985:2011.

## SGBD H2
A simplicidade do [H2](http://www.h2database.com) foi determinante para identificá-lo para a fase
de desenvolvimento.

**Importante**: use a versão que é empregada pelo Spring e pelo Flyway. Para tal,
consulte o arquivo _pom.xml_ (effective pom) e procure pela propriedade
_h2.version_. Essa propriedade deve ser empregada pelo Flyway e também
para a configuração do **exec-maven-plugin**.

### Iniciar o H2 (Server Mode)
Basta executar **mvn exec:java***. No _pom.xml_ está indicada a versão
a ser utilizada. Deve ser a mesma versão empregada tanto pelo 
Flyway quanto pelo cliente SQL empregado.

# Passos

```
$ mvn exec:java
$ mvn clean package
$ java -jar target/spring-flyway-1.0.0.jar
```

## Migração (refatoração)
O diretório `src/main/db/migration` contém várias versões **V1**, 
**V2** e assim sucessivamente. 

Todas elas serão aplicadas, na ordem das versões, com o comando
**mvn flyway:migrate**. Use o comando **mvnflyway:info** para obter
informações sobre o banco de dados em questão, o que deve indicar
eventuais alterações pendentes, se for o caso.
