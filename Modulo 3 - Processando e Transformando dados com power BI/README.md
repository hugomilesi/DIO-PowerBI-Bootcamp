# Etapas de Transformação

- As tabelas "departament, dependent, dept_locations, employee, project, works_on" foram renomeadas para: "departamento, dependente, local_departamento, funcionario, projetos, setor_de_trabalho" para uma melhor leitura.

- Valores monetários foram convertidos para decimal.

- Encontrado um valor nulo na tabela funcionário coluna Super_ssn, indicando que o respectivo funcionário não possui supervisor. Para não deixar dados com valores nulos foi substituido por "sem_supervisor".

- Criação da coluna "Possui_supervisor", indicando os funcionários supervisionados e não supervisionados.

- Separado colunas complexas como "endereco" em 4 colunas "Address", "Street", "City" e "State".

- Mesclagem da tabela funcionário com a tabela departamento de forma a esclarecer qual departamento os funcionários trabalham. 

- Criada a tabela departamento/gerente para verificar se há algum departamento sem gerente.

- Junção dos respectivos nomes de gerentes e colaboradores pela query:
 ```sql 
    SELECT
    CONCAT(e.Fname, " ", e.Lname) AS colaboradores, 
    CONCAT(f.Fname, " ", f.Lname) AS gerente
    FROM employee e 
    LEFT JOIN 
    employee f ON e.Ssn = f.Super_ssn;
```
- Realizada a mesclagem da tabela departamento com local_departamento para coletar insights sobre o localização. Foi realizada uma mesclagem pois a mesclagem é usada para juntar tabelas com base em colunas-chave comuns, enquanto a atribuição é usada para empilhar tabelas com a mesma estrutura.

- Criação de uma tabela para registrar a relação de colaboradores por gerente.

