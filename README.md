# testes-caixa-branca

# TesteCaixaBranca - Sistema de Login

## Problemas Identificados

### 1. Problema com o driver JDBC
**Descrição:** O código está utilizando a classe "com.mysql.DriverManager" como driver JDBC, o que é incorreto.  
**Impacto:** Isso impede que a conexão com o banco de dados seja estabelecida, tornando a aplicação inoperante.

### 2. Vulnerabilidade de SQL Injection
**Descrição:** A construção da query SQL inclui diretamente as variáveis de login e senha, o que expõe o sistema a ataques de SQL Injection.  
**Impacto:** Há risco de ataques que podem comprometer a integridade do banco de dados e a segurança da aplicação.

### 3. Conexão de banco de dados não encerrada
**Descrição:** A conexão com o banco de dados (Connection) não é fechada após o seu uso, levando a possíveis vazamentos de recursos.  
**Impacto:** Pode ocorrer degradação de desempenho e falhas no sistema devido à exaustão de conexões.

### 4. Falta de tratamento adequado de exceções
**Descrição:** O código captura exceções sem um tratamento eficaz.  
**Impacto:** Isso dificulta a identificação e correção de problemas, afetando a manutenção e confiabilidade do sistema.

### 5. Uso de nomes pouco descritivos
**Descrição:** Variáveis como "result" e "nome" têm nomes genéricos, tornando o código mais difícil de entender.  
**Impacto:** Reduz a clareza e aumenta a possibilidade de erros por confusão.

### 6. Potencial de NullPointerException
**Descrição:** Se a conexão ao banco de dados falhar, a variável "conn" poderá ser nula. O código não verifica essa situação antes de sua utilização.  
**Impacto:** Pode resultar em erros inesperados e falhas durante a execução do sistema.

# Testes de Caixa Branca - Sistema de Login

## Descrição dos Nós
- **Início**: Entrada no método.
- **Conexão**: Estabelece a conexão com o banco de dados.
- **Query SQL**: Cria a instrução SQL para consulta.
- **Execução SQL**: Executa a query SQL.
- **Resultado Encontrado?**: Verifica se o resultado foi encontrado.
- **Nome do Usuário**: Obtém o nome do usuário do banco de dados.
- **Retorno Verdadeiro**: Retorna verdadeiro caso o usuário seja válido.
- **Retorno Falso**: Retorna falso caso o usuário não seja encontrado.
- **Exceção**: Tratamento de exceção para erros.

## Grafo de Fluxo
![Grafo de Fluxo do Código](/img/grafo.png)

## Complexidade Ciclomática
A complexidade ciclomática foi calculada para avaliar a complexidade do código, usando a fórmula:

M = E - N + 2P


Onde:
- **N**: Número de nós = 9
- **E**: Número de arestas = 10
- **P**: Número de componentes conexos = 1

**Cálculo da complexidade**:

M = 10 - 9 + 2(1) = 3


**Complexidade Ciclomática**: 3

## Caminhos Básicos
A complexidade ciclomática permite identificar 3 caminhos básicos no código:

### Caminho 1:
Início → Conexão com BD → Criação da Query SQL → Execução da Query SQL → Resultado Encontrado? (Sim) → Nome do Usuário → Retorno Verdadeiro

### Caminho 2:
Início → Conexão com BD → Criação da Query SQL → Execução da Query SQL → Resultado Encontrado? (Não) → Retorno Falso

### Caminho 3:
Início → Exceção (Caso ocorra um erro na conexão ou execução da query)


