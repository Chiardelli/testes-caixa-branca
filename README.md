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

